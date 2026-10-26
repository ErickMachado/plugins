# KyberSwap

Cursor plugin that connects agents to [KyberSwap](https://kyberswap.com/) through KyberNetwork's open-source [kyberswap-mcp](https://github.com/KyberNetwork/kyberswap-mcp) [Model Context Protocol](https://modelcontextprotocol.io/) server.

Quote swaps, inspect pools, and build swap, zap, and gasless limit-order calldata across 18 EVM chains.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **KyberSwap**.
3. Click **Install**.

Or run `/add-plugin kybernetwork` in chat.

## MCP

```json
{
  "mcpServers": {
    "kybernetwork": {
      "type": "stdio",
      "command": "npx",
      "args": [
        "-y",
        "--package",
        "tsx@4",
        "--package",
        "github:KyberNetwork/kyberswap-mcp",
        "node",
        "-e",
        "const {spawn}=require('node:child_process');const path=require('node:path');const fs=require('node:fs');const suffix=path.join('node_modules','.bin');const root=(process.env.PATH||'').split(path.delimiter).filter((entry)=>entry.endsWith(suffix)).map((entry)=>path.resolve(entry,'..')).find((dir)=>fs.existsSync(path.join(dir,'kyberswap-mcp-server','src','index.ts')));if(!root){console.error('kyberswap-mcp-server source was not installed');process.exit(1);}const entry=path.join(root,'kyberswap-mcp-server','src','index.ts');const child=spawn(process.execPath,['--import','tsx',entry],{cwd:path.resolve(root,'..'),stdio:'inherit'});child.on('error',(error)=>{console.error(error);process.exit(1);});for(const signal of ['SIGINT','SIGTERM','SIGHUP']){process.on(signal,()=>{try{child.kill(signal);}catch{}});}child.on('exit',(code)=>process.exit(code??0));"
      ]
    }
  }
}
```

The server runs locally over stdio and needs Node.js 18+. The package is not on npm, and installing it from GitHub does not build `dist/`, so this command runs `src/index.ts` with `tsx`. It calls KyberSwap's public, unauthenticated APIs, so there is no API key or sign-in.

Optional: override the default public RPC for any chain with `RPC_URL_<CHAIN_SLUG_UPPER>` (for example `RPC_URL_ETHEREUM`). These are only used by `swap-simulate` and `swap-status`.

## What agents can do

| Category | Tools |
| --- | --- |
| Read-only | `get-quote`, `token-info`, `get-pool-info`, `order-manager`, `position-manager` |
| Build calldata | `swap-build`, `zap` |
| Verify | `swap-simulate`, `swap-status` |
| Limit orders | `limit-order-build`, `limit-order-submit`, `limit-order-cancel-build`, `limit-order-cancel-submit` |

Supported chains: Ethereum, BSC, Arbitrum, Polygon, Optimism, Base, Avalanche, Linea, Mantle, Sonic, Berachain, Ronin, Unichain, HyperEVM, Plasma, Etherlink, Monad, and MegaETH.

## Notes

- The server is non-custodial. It never holds private keys or signs transactions; it returns reviewable calldata or EIP-712 typed data that you sign and broadcast with your own wallet.
- Swap routes expire after about 30 seconds. Run `swap-simulate` before broadcasting.

## Docs

- KyberSwap: https://kyberswap.com/
- Server source: https://github.com/KyberNetwork/kyberswap-mcp

Logo is the Kyber Network mark from the verified `KyberNetwork` GitHub organization avatar (256×256). kyber.network and kyberswap.com were unreachable when this plugin was added, so the submitted logo file was not downloaded.

## License

MIT

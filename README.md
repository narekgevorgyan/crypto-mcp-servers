# Crypto MCP Servers

> The best Model Context Protocol (MCP) servers for crypto: market data, exchanges, wallets, on-chain data, DeFi, research, and agent payments. Checked against official docs and live endpoints.

[MCP](https://modelcontextprotocol.io/) servers let AI assistants like Claude, ChatGPT, Cursor, and Codex call real tools. This list covers the crypto ones worth connecting in 2026. Most entries are **official servers published by the provider itself**, and every listed repository passes a weekly freshness check, so abandoned projects drop out instead of piling up.

> **Maintained by the CoinStats team.** If you want one server that covers prices, charts, wallets on 120+ chains, exchange balances, portfolio P/L, DeFi, and news, start with the [CoinStats MCP](https://github.com/CoinStatsHQ/coinstats-mcp) at `https://mcp.coinstats.app/mcp`. Every other entry here meets the same inclusion standard, competitors included.

## Quick Index

- [Quick Start](#quick-start)
- [Try Without a Key](#try-without-a-key)
- [Server Categories](#server-categories)
  - [Market Data](#market-data)
  - [Exchanges & Trading](#exchanges--trading)
  - [Wallets & Portfolio](#wallets--portfolio)
  - [Agent Wallets & Payments](#agent-wallets--payments)
  - [On-chain Data & Infrastructure](#on-chain-data--infrastructure)
  - [DeFi](#defi)
  - [Analytics & Research](#analytics--research)
  - [News & Sentiment](#news--sentiment)
  - [Security & Smart Contracts](#security--smart-contracts)
  - [Aggregators & Multi-tool](#aggregators--multi-tool)
- [Safety Checklist](#safety-checklist)
- [Resources](#resources)
- [Methodology](#methodology)
- [Contributing](#contributing)

## Quick Start

Most servers below are **remote**: you paste one URL into your client and sign in. Using the CoinStats MCP as the example:

**Claude Code**

```bash
claude mcp add coinstats --transport http https://mcp.coinstats.app/mcp
```

**Claude.ai / Claude Desktop:** Settings → Connectors → Add custom connector → paste `https://mcp.coinstats.app/mcp`.

**Cursor** (`~/.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "coinstats": { "url": "https://mcp.coinstats.app/mcp" }
  }
}
```

**Codex**

```bash
codex mcp add coinstats --url https://mcp.coinstats.app/mcp
codex mcp login coinstats
```

**Local** servers run on your machine instead, usually with `npx`, `uvx`, or Docker plus an API key in the environment. Each server's docs show the exact command.

### How to read the tables

| Column | Values |
|---|---|
| Maintainer | `Official` = published by the company behind the product or data. `Community` = independent project. |
| Transport | `Remote` = hosted URL. `Local` = runs on your machine (stdio). `Both` = either. |
| Auth | `No` = no credentials. `apiKey` = provider key. `OAuth` = sign in through the browser. `Wallet` = needs a private key, seed, or wallet connection. `Mixed` = several modes, for example keyless public tools plus a key or OAuth for the rest. |

## Try Without a Key

These hosted servers answered an MCP `initialize` request with no credentials. They are the fastest way to test an agent against live crypto data. Rate limits apply.

| Server | Endpoint | What You Get |
|---|---|---|
| [Aave](https://aave.com/blog/introducing-aave-mcp-server) | `https://mcp.aave.com` | Aave markets, positions, health factors, unsigned txs |
| [Blockscout](https://github.com/blockscout/mcp-server) | `https://mcp.blockscout.com/mcp` | EVM explorer data across Blockscout chains |
| [CoinGecko](https://docs.coingecko.com/docs/mcp-server) | `https://mcp.api.coingecko.com/mcp` | Prices, markets, trending, GeckoTerminal DEX data |
| [CoinPaprika](https://github.com/coinpaprika/coinpaprika-mcp) | `https://mcp.coinpaprika.com/streamable-http` | Tickers, exchanges, and OHLCV for 12,000+ coins |
| [Crypto.com Market Data](https://mcp.crypto.com/docs) | `https://mcp.crypto.com/market-data/mcp` | Crypto.com Exchange tickers, books, and candles |
| [deBridge](https://github.com/debridge-finance/debridge-mcp) | `https://agents.debridge.com/mcp` | Cross-chain and same-chain swap transactions |
| [DexPaprika](https://github.com/coinpaprika/dexpaprika-mcp) | `https://mcp.dexpaprika.com/streamable-http` | DEX pools, liquidity, and token prices |
| [Etherscan (keyless)](https://docs.etherscan.io/ai/mcp) | `https://mcp-keyless.etherscan.io/mcp` | Explorer data on 60+ EVM chains |
| [Gate](https://github.com/gate/gate-mcp) | `https://api.gatemcp.ai/mcp` | Gate public market data |
| [InsumerAPI](https://github.com/insumerapi/mcp-server-insumer) | `https://api.insumermodel.com/mcp` | Signed yes or no on wallet conditions across 37 chains |
| [Jupiter](https://developers.jup.ag/docs/ai/trading-mcp) | `https://mcp.jup.ag` | Solana swap quotes, limit orders, lending data |
| [LI.FI](https://docs.li.fi/mcp-server/overview) | `https://mcp.li.quest/mcp` | Bridge and swap routes across 58 chains |
| [Morpho](https://docs.morpho.org/developers/agents/mcp/) | `https://mcp.morpho.org/` | Morpho vaults, markets, and positions |
| [Solana Explorer](https://github.com/solana-foundation/explorer/tree/master/app/mcp) | `https://explorer.solana.com/mcp` | Decode Solana accounts and signatures |
| [TronGrid](https://developers.tron.network/docs/mcp) | `https://mcp.trongrid.io/mcp` | TRON accounts, blocks, and TRC-20 data |

## Server Categories

### Market Data
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [Alpha Vantage](https://github.com/alphavantage/alpha_vantage_mcp) | Crypto and FX series plus technical indicators, alongside stocks | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/alphavantage/alpha_vantage_mcp) |
| [altFINS](https://altfins.com/crypto-market-and-analytical-data-api/documentation/mcp-server/) | Screeners, technical analysis, signals, news, and calendar events | `Official` | `Remote` | `Mixed` | [Docs](https://altfins.com/crypto-market-and-analytical-data-api/documentation/mcp-server/) |
| [Birdeye](https://data.birdeye.so/docs/agents/birdeye-mcp.md) | Solana and multichain token prices, OHLCV, and trending tokens (beta) | `Official` | `Remote` | `Mixed` | [Docs](https://data.birdeye.so/docs/agents/birdeye-mcp.md) |
| [CoinAPI](https://www.coinapi.io/products/market-data-api/docs/mcp) | Quotes, trades, order books, and OHLCV across hundreds of exchanges | `Official` | `Remote` | `apiKey` | [Docs](https://www.coinapi.io/products/market-data-api/docs/mcp) |
| [CoinDesk Data](https://data.coindesk.com/blogs/coindesk-data-now-available-via-claude-mcp-connector) | Spot, futures, options, and index data from the former CryptoCompare/CCData | `Official` | `Remote` | `OAuth` | [Docs](https://data.coindesk.com/blogs/coindesk-data-now-available-via-claude-mcp-connector) |
| [CoinGecko](https://docs.coingecko.com/docs/mcp-server) | Prices, market caps, categories, trending coins, and GeckoTerminal DEX pools | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/coingecko/coingecko-typescript/tree/main/packages/mcp-server) |
| [CoinGlass](https://docs.coinglass.com/reference/mcp-service) | Funding rates, open interest, liquidations, and ETF flows (paid API) | `Official` | `Remote` | `apiKey` | [Docs](https://docs.coinglass.com/reference/mcp-service) |
| [CoinMarketCap](https://coinmarketcap.com/api/mcp/) | Quotes, global metrics, Fear & Greed, narratives, and technical analysis | `Official` | `Remote` | `Mixed` | [Docs](https://coinmarketcap.com/api/mcp/) |
| [CoinPaprika](https://github.com/coinpaprika/coinpaprika-mcp) | Prices, tickers, exchanges, and OHLCV for 12,000+ coins, no key needed | `Official` | `Both` | `No` | [GitHub](https://github.com/coinpaprika/coinpaprika-mcp) |
| [CoinStats](https://github.com/CoinStatsHQ/coinstats-mcp) | Prices and charts for 100,000+ coins, tickers across 200+ exchanges | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/CoinStatsHQ/coinstats-mcp) |
| [Crypto.com Market Data](https://mcp.crypto.com/docs) | Crypto.com Exchange tickers, order books, candles, and trades | `Official` | `Remote` | `No` | [Docs](https://mcp.crypto.com/docs) |
| [DEX Screener CLI + MCP](https://github.com/vibeforge1111/dexscreener-cli-mcp-tool) | Scan and score trending DEX tokens by volume, liquidity, and momentum | `Community` | `Local` | `No` | [GitHub](https://github.com/vibeforge1111/dexscreener-cli-mcp-tool) |
| [DexPaprika](https://github.com/coinpaprika/dexpaprika-mcp) | DEX pools, token prices, liquidity, trades, and OHLCV across many chains | `Official` | `Both` | `No` | [GitHub](https://github.com/coinpaprika/dexpaprika-mcp) |
| [Pyth](https://docs.pyth.network/price-feeds/pro/mcp) | Real-time and historical oracle prices and candles for crypto, FX, and equities | `Official` | `Remote` | `apiKey` | [Docs](https://docs.pyth.network/price-feeds/pro/mcp) |
| [TradingView Desktop Bridge](https://github.com/tradesdontlie/tradingview-mcp) | Drive TradingView Desktop: chart analysis, Pine Script, replay | `Community` | `Local` | `No` | [GitHub](https://github.com/tradesdontlie/tradingview-mcp) |
| [TradingView MCP](https://github.com/atilaahmettaner/tradingview-mcp) | Crypto screeners, top gainers, indicators, and backtesting (unaffiliated) | `Community` | `Local` | `No` | [GitHub](https://github.com/atilaahmettaner/tradingview-mcp) |
| [Twelve Data](https://github.com/twelvedata/mcp) | Real-time and historical crypto pairs and indicators, plus stocks and FX | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/twelvedata/mcp) |

### Exchanges & Trading
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [Alpaca](https://docs.alpaca.markets/us/docs/trading-api-mcp) | Trade crypto, stocks, and options with paper trading on by default | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/alpacahq/alpaca-mcp-server) |
| [Binance](https://developers.binance.com/en/docs/agent-native/mcp-server/agentic) | Spot, margin, convert, and futures trading in an isolated agent sub-account | `Official` | `Remote` | `OAuth` | [Docs](https://developers.binance.com/en/docs/agent-native/mcp-server/agentic) |
| [Bitget Agent Hub](https://github.com/Bitget-AI/agent_hub) | Bitget spot and futures with read-only, paper-trading, and dry-run modes | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/Bitget-AI/agent-mcp) |
| [Bybit](https://github.com/bybit-exchange/trading-mcp) | Full Bybit V5 API: market data, orders, positions, earn, and bots | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/bybit-exchange/trading-mcp) |
| [CCXT MCP](https://github.com/lazy-dinosaur/ccxt-mcp) | Market data and trading across 100+ exchanges through CCXT | `Community` | `Local` | `Mixed` | [GitHub](https://github.com/lazy-dinosaur/ccxt-mcp) |
| [Coinbase for Agents](https://docs.cdp.coinbase.com/ai-agents/coinbase-for-agents/coinbase-mcp) | Advanced Trade prices, order previews, orders, portfolios, and futures | `Official` | `Both` | `Mixed` | [Docs](https://docs.cdp.coinbase.com/ai-agents/coinbase-for-agents/coinbase-mcp) |
| [Crypto.com Exchange CLI](https://github.com/crypto-com/cdcx-cli) | Trade, manage positions, and run bots on Crypto.com Exchange | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/crypto-com/cdcx-cli) |
| [Freqtrade MCP](https://github.com/kukapay/freqtrade-mcp) | Control a running Freqtrade bot: status, profit, forced entries and exits | `Community` | `Local` | `apiKey` | [GitHub](https://github.com/kukapay/freqtrade-mcp) |
| [Gate](https://github.com/gate/gate-mcp) | Gate spot and futures trading, transfers, DEX swaps, and public market data | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/gate/gate-mcp) |
| [Gemini](https://developer.gemini.com/tools) | Gemini market data, orders, funds, staking, and prediction markets | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/gemini/developer-platform/tree/main/packages/mcp-server) |
| [Hyperliquid MCP](https://github.com/GigabrainGG/hyperliquid-mcp) | Hyperliquid perps and spot orders, brackets, and positions | `Community` | `Local` | `Wallet` | [GitHub](https://github.com/GigabrainGG/hyperliquid-mcp) |
| [Kraken CLI](https://docs.kraken.com/home/mcp) | Kraken spot and futures, paper trading, and gated live-trading tools | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/krakenfx/kraken-cli) |
| [OKX Agent Trade Kit](https://github.com/okx/agent-trade-kit) | OKX spot, perps, options, grid and DCA bots, with a read-only flag | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/okx/agent-trade-kit) |
| [PMXT](https://github.com/pmxt-dev/pmxt-mcp) | Unified Polymarket, Kalshi, and Limitless markets, order books, and history | `Official` | `Both` | `apiKey` | [GitHub](https://github.com/pmxt-dev/pmxt-mcp) |
| [Polymarket MCP](https://github.com/caiovicentino/polymarket-mcp-server) | Analyze, monitor, and trade Polymarket, with a no-wallet demo mode | `Community` | `Local` | `Mixed` | [GitHub](https://github.com/caiovicentino/polymarket-mcp-server) |
| [Prediction Market MCP](https://github.com/JamesANZ/prediction-market-mcp) | Read-only odds from Polymarket, PredictIt, and Kalshi | `Community` | `Local` | `No` | [GitHub](https://github.com/JamesANZ/prediction-market-mcp) |
| [QuantConnect](https://www.quantconnect.com/docs/v2/ai-assistance/mcp-server/key-concepts) | Write, backtest, and deploy algorithmic strategies, crypto included | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/QuantConnect/mcp-server) |

### Wallets & Portfolio
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [Alchemy](https://www.alchemy.com/docs/alchemy-mcp-server) | Balances, NFTs, transfers, prices, and simulation on 100+ chains | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/alchemyplatform/alchemy-mcp-server) |
| [Blockscout](https://github.com/blockscout/mcp-server) | Address balances, tokens, NFTs, and tx history on EVM chains | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/blockscout/mcp-server) |
| [CoinStats](https://github.com/CoinStatsHQ/coinstats-mcp) | Portfolio P/L, wallets on 120+ chains, exchange balances, and DeFi positions | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/CoinStatsHQ/coinstats-mcp) |
| [GoldRush](https://goldrush.dev/docs/goldrush-mcp-server) | Covalent wallet balances, tx history, NFTs, and approvals on 100+ chains | `Official` | `Both` | `apiKey` | [Docs](https://goldrush.dev/docs/goldrush-mcp-server) |
| [Helius](https://www.helius.dev/docs/agents/mcp) | Solana wallets, DAS assets, tx history, webhooks, and transfers | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/helius-labs/core-ai/tree/main/helius-mcp) |
| [Nansen](https://docs.nansen.ai/mcp/connecting) | Labeled wallet profiles, PnL, counterparties, and smart-money flows | `Official` | `Remote` | `Mixed` | [Docs](https://docs.nansen.ai/mcp/connecting) |
| [Octav](https://github.com/Octav-Labs/octav-api-mcp) | Net worth, DeFi positions, history, and snapshots across 20+ chains | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/Octav-Labs/octav-api-mcp) |

### Agent Wallets & Payments
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [Alby](https://github.com/getAlby/mcp) | Lightning wallet over NWC: pay and create invoices, LNURL, L402 | `Official` | `Both` | `Wallet` | [GitHub](https://github.com/getAlby/mcp) |
| [Cobo Agentic Wallet](https://www.cobo.com/products/agentic-wallet/manual/developer/mcp) | Policy-scoped MPC agent wallet for transfers and calls on 80+ chains | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/CoboGlobal/cobo-agentic-wallet) |
| [Coinbase Agentic Wallet](https://docs.cdp.coinbase.com/agentic-wallet/mcp/welcome) | Agent wallet with onramp and x402 pay-per-call on Base, Polygon, and Solana | `Official` | `Local` | `Mixed` | [Docs](https://docs.cdp.coinbase.com/agentic-wallet/mcp/welcome) |
| [Coinbase AgentKit](https://github.com/coinbase/agentkit/tree/main/typescript/framework-extensions/model-context-protocol) | Build your own MCP server exposing 50+ onchain actions | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/coinbase/agentkit/tree/main/typescript/framework-extensions/model-context-protocol) |
| [Coinbase Wallet MCP](https://docs.cdp.coinbase.com/ai-agents/coinbase-for-agents/wallet-mcp) | Send, swap, sign, and batch calls from your own Coinbase Wallet with approvals | `Official` | `Remote` | `OAuth` | [Docs](https://docs.cdp.coinbase.com/ai-agents/coinbase-for-agents/wallet-mcp) |
| [Coinbase x402 Bazaar](https://docs.cdp.coinbase.com/x402/buyer/mcp-payments) | Discover and call x402 pay-per-request APIs | `Official` | `Remote` | `No` | [Docs](https://docs.cdp.coinbase.com/x402/buyer/mcp-payments) |
| [Fireblocks AI Link](https://developers.fireblocks.com/docs/building-with-ai) | Query Fireblocks vaults and transactions; local mode can create transactions | `Official` | `Both` | `Mixed` | [Docs](https://developers.fireblocks.com/docs/building-with-ai) |
| [Lightning Labs](https://github.com/lightninglabs/lightning-agent-tools) | Read-only lnd node data: channels, invoices, and payments | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/lightninglabs/lightning-agent-tools) |
| [Lit Protocol Vincent](https://github.com/LIT-Protocol/Vincent/tree/main/packages/apps/mcp) | User-delegated, policy-bounded agent actions such as swaps and transfers | `Official` | `Local` | `Wallet` | [GitHub](https://github.com/LIT-Protocol/Vincent/tree/main/packages/apps/mcp) |
| [OKX Agentic Wallet](https://web3.okx.com/onchainos/dev-docs/home/agentic-wallet-overview) | TEE agent wallet with balances, simulated DEX swaps, and broadcasting | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/okx/onchainos-skills) |
| [Phantom](https://docs.phantom.com/phantom-mcp-server/index) | Dedicated agent wallet for transfers, swaps, and signing on Solana and EVM | `Official` | `Local` | `OAuth` | [GitHub](https://github.com/phantom/phantom-connect-sdk/tree/main/packages/mcp-server) |
| [Solana Agent Kit](https://github.com/sendaifun/solana-agent-kit/tree/v2/packages/adapter-mcp) | Solana swaps, transfers, token launches, and DeFi through 60+ actions | `Official` | `Local` | `Wallet` | [GitHub](https://github.com/sendaifun/solana-agent-kit/tree/v2/packages/adapter-mcp) |
| [thirdweb](https://portal.thirdweb.com/ai/mcp) | Server wallets, transfers, contract deploys and writes, bridging, and swaps | `Official` | `Remote` | `apiKey` | [Docs](https://portal.thirdweb.com/ai/mcp) |

### On-chain Data & Infrastructure
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [Allium](https://docs.allium.so/ai/mcp/overview) | SQL and saved queries over normalized data on 85+ chains | `Official` | `Remote` | `Mixed` | [Docs](https://docs.allium.so/ai/mcp/overview) |
| [Aptos](https://github.com/aptos-labs/aptos-npm-mcp) | Aptos APIs, on-chain data, Move tooling, and API key management | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/aptos-labs/aptos-npm-mcp) |
| [Bankless Onchain](https://github.com/Bankless/onchain-mcp) | Contract state, ABIs, proxies, events, and tx history on EVM chains | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/Bankless/onchain-mcp) |
| [Bitquery](https://www.bitquery.io/products/bitquery-mcp-server) | DEX trades, holders, and money-flow tracing across 40+ chains | `Official` | `Remote` | `OAuth` | [GitHub](https://github.com/bitquery/mcp) |
| [Blockscout](https://github.com/blockscout/mcp-server) | Multichain EVM explorer: balances, tokens, NFTs, and contract ABIs | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/blockscout/mcp-server) |
| [BNB Chain](https://github.com/bnb-chain/bnbchain-mcp) | BNB Chain and EVM reads, preview-then-confirm transfers, Greenfield storage | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/bnb-chain/bnbchain-mcp) |
| [Chainstack](https://chainstack.com/mcp/) | Node deployment and management plus live RPC on 70+ chains | `Official` | `Remote` | `Mixed` | [Docs](https://chainstack.com/mcp/) |
| [Dune](https://docs.dune.com/docs/agents/mcp) | Find tables, run DuneSQL, and build charts and dashboards | `Official` | `Remote` | `Mixed` | [Docs](https://docs.dune.com/docs/agents/mcp) |
| [Etherscan](https://docs.etherscan.io/ai/mcp) | Transactions, balances, and contracts on 60+ EVM chains, with a keyless server | `Official` | `Remote` | `Mixed` | [Docs](https://docs.etherscan.io/ai/mcp) |
| [EVM MCP Server](https://github.com/mcpdotdirect/evm-mcp-server) | Generic reads and writes on 60+ EVM networks: balances, contracts, ENS | `Community` | `Local` | `Mixed` | [GitHub](https://github.com/mcpdotdirect/evm-mcp-server) |
| [Hedera Agent Kit](https://docs.hedera.com/solutions/ai/hosted-mcp-server) | Build Hedera account, token, HCS, and contract transactions for wallet signing | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/hashgraph/hedera-agent-kit-js/tree/main/packages/mcp) |
| [Helius](https://www.helius.dev/docs/agents/mcp) | Solana RPC, DAS assets, enhanced transactions, and webhooks | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/helius-labs/core-ai/tree/main/helius-mcp) |
| [InsumerAPI](https://github.com/insumerapi/mcp-server-insumer) | Signed yes or no on whether a wallet meets a condition (token balance, NFT, attestation) on 37 chains, verifiable offline | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/insumerapi/mcp-server-insumer) |
| [QuickNode](https://www.quicknode.com/docs/build-with-ai/quicknode-mcp) | Manage QuickNode endpoints and usage, plus read-only JSON-RPC calls | `Official` | `Remote` | `Mixed` | [Docs](https://www.quicknode.com/docs/build-with-ai/quicknode-mcp) |
| [Solana Developer MCP](https://mcp.solana.com) | Current Solana docs search plus Anchor and program checks | `Official` | `Remote` | `No` | [GitHub](https://github.com/solana-foundation/solana-mcp) |
| [Solana Explorer](https://github.com/solana-foundation/explorer/tree/master/app/mcp) | Keyless, read-only decoding of Solana accounts and signatures | `Official` | `Remote` | `No` | [GitHub](https://github.com/solana-foundation/explorer/tree/master/app/mcp) |
| [Tatum](https://github.com/tatumio/blockchain-mcp) | Balances, portfolios, blocks, and an RPC gateway across 130+ networks | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/tatumio/blockchain-mcp) |
| [Tenderly](https://docs.tenderly.co/mcp-server) | Transaction simulation, tracing, and Virtual TestNets (paid plans) | `Official` | `Remote` | `OAuth` | [Docs](https://docs.tenderly.co/mcp-server) |
| [The Graph Subgraph MCP](https://thegraph.com/docs/en/subgraphs/tooling/subgraph-mcp/introduction/) | Find subgraphs, read schemas, and run GraphQL queries | `Official` | `Both` | `apiKey` | [Docs](https://thegraph.com/docs/en/subgraphs/tooling/subgraph-mcp/introduction/) |
| [The Graph Token API](https://github.com/pinax-network/pinax-mcp) | Token metadata, balances, transfers, and holders | `Official` | `Remote` | `apiKey` | [GitHub](https://github.com/pinax-network/pinax-mcp) |
| [TronGrid](https://developers.tron.network/docs/mcp) | TRON accounts, blocks, TRC-10/20 tokens, wallet ops, and JSON-RPC | `Official` | `Remote` | `No` | [Docs](https://developers.tron.network/docs/mcp) |

### DeFi
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [1inch](https://business.1inch.com/portal/documentation/ai-integration/ecosystem) | Swap quotes and builds, limit orders, and 1inch APIs with WalletConnect signing | `Official` | `Remote` | `Mixed` | [Docs](https://business.1inch.com/portal/documentation/ai-integration/ecosystem) |
| [Aave](https://aave.com/blog/introducing-aave-mcp-server) | Aave V3/V4 markets, positions, health factors, and unsigned tx builders | `Official` | `Remote` | `No` | [Docs](https://aave.com/blog/introducing-aave-mcp-server) |
| [Across](https://docs.across.to/ai-agents/mcp-server) | Across bridge fees, supported chains, and integration docs | `Official` | `Remote` | `No` | [Docs](https://docs.across.to/ai-agents/mcp-server) |
| [deBridge](https://github.com/debridge-finance/debridge-mcp) | Cross-chain and same-chain swaps, fee estimates, and tx building | `Official` | `Both` | `No` | [GitHub](https://github.com/debridge-finance/debridge-mcp) |
| [DefiLlama](https://github.com/DefiLlama/defillama-skills) | TVL, yields, prices, protocol metrics, and stablecoins (subscription) | `Official` | `Remote` | `OAuth` | [GitHub](https://github.com/DefiLlama/defillama-skills) |
| [Jupiter](https://developers.jup.ag/docs/ai/trading-mcp) | Solana swaps, limit orders, lending, and positions as unsigned txs | `Official` | `Remote` | `No` | [Docs](https://developers.jup.ag/docs/ai/trading-mcp) |
| [KyberSwap](https://docs.kyberswap.com/ai-agent-hub/mcp-server-for-hosted-agents) | Aggregator quotes, unsigned swap txs, and limit orders on 18 chains | `Official` | `Local` | `No` | [GitHub](https://github.com/KyberNetwork/kyberswap-mcp) |
| [LI.FI](https://docs.li.fi/mcp-server/overview) | Cross-chain swap and bridge routes across 58 chains | `Official` | `Remote` | `No` | [Docs](https://docs.li.fi/mcp-server/overview) |
| [Morpho](https://docs.morpho.org/developers/agents/mcp/) | Morpho vaults, markets, positions, and unsigned prepare-tx tools | `Official` | `Remote` | `No` | [Docs](https://docs.morpho.org/developers/agents/mcp/) |
| [Pendle](https://github.com/pendle-finance/pendle-ai) | Pendle PT/YT trading, LP, limit orders, and Boros rate derivatives | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/pendle-finance/pendle-ai) |
| [Relay](https://github.com/relayprotocol/relay-mcp) | Cross-chain bridge and swap quotes, fees, and tx status | `Official` | `Local` | `No` | [GitHub](https://github.com/relayprotocol/relay-mcp) |
| [Solana Agent Kit](https://github.com/sendaifun/solana-agent-kit/tree/v2/packages/adapter-mcp) | Jupiter, Raydium, Orca, Kamino, and Pump.fun actions through plugins | `Official` | `Local` | `Wallet` | [GitHub](https://github.com/sendaifun/solana-agent-kit/tree/v2/packages/adapter-mcp) |

### Analytics & Research
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [CryptoQuant](https://userguide.cryptoquant.com/api/mcp-server-beta/remote-mcp-recommended) | Exchange flows, MVRV, SOPR, miner and derivatives data, and research | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/CryptoQuantOfficial/cryptoquant-mcp) |
| [Glassnode](https://docs.glassnode.com/integrations-and-tools/glassnode-mcp-server) | 900+ on-chain and market metrics for 1,700+ assets | `Official` | `Remote` | `Mixed` | [Docs](https://docs.glassnode.com/integrations-and-tools/glassnode-mcp-server) |
| [Messari](https://docs.messari.io/mcp-server/hosted) | Messari research and news search, datasets, and asset time series (Enterprise) | `Official` | `Remote` | `OAuth` | [Docs](https://docs.messari.io/mcp-server/hosted) |
| [Nansen](https://docs.nansen.ai/mcp/connecting) | Smart-money labels, token flows, and wallet PnL | `Official` | `Remote` | `Mixed` | [Docs](https://docs.nansen.ai/mcp/connecting) |
| [Token Terminal](https://tokenterminal.com/docs/mcp/introduction) | Protocol revenue, fees, financial statements, and sector comparisons | `Official` | `Remote` | `OAuth` | [Docs](https://tokenterminal.com/docs/mcp/introduction) |
| [Web3 Research MCP](https://github.com/aaronjmars/web3-research-mcp) | Free local token research reports from CoinGecko, DefiLlama, and the web | `Community` | `Local` | `No` | [GitHub](https://github.com/aaronjmars/web3-research-mcp) |

### News & Sentiment
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [BlockBeats](https://github.com/BlockBeatsOfficial/blockbeats-MCP) | Newsflashes, articles, BTC ETF flows, stablecoin and macro data | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/BlockBeatsOfficial/blockbeats-MCP) |
| [CoinMarketCap](https://coinmarketcap.com/api/mcp/) | Fear & Greed index, latest news, trending narratives, and macro events | `Official` | `Remote` | `Mixed` | [Docs](https://coinmarketcap.com/api/mcp/) |
| [CoinStats](https://github.com/CoinStatsHQ/coinstats-mcp) | Latest and trending crypto news, filtered by source or topic | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/CoinStatsHQ/coinstats-mcp) |
| [CryptoPanic MCP](https://github.com/kukapay/cryptopanic-mcp-server) | Latest crypto headlines from CryptoPanic | `Community` | `Local` | `apiKey` | [GitHub](https://github.com/kukapay/cryptopanic-mcp-server) |
| [Gloria AI](https://github.com/cryptobriefing-labs/gloria-mcp) | AI-curated crypto headlines with sentiment, recaps, and ticker summaries | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/cryptobriefing-labs/gloria-mcp) |
| [Kaito](https://github.com/MetaSearch-IO/kaito-mcp-server) | Crypto mindshare, social sentiment, and narrative intelligence | `Official` | `Both` | `apiKey` | [GitHub](https://github.com/MetaSearch-IO/kaito-mcp-server) |
| [LunarCrush](https://lunarcrush.com/developers/mcp) | Social sentiment, Galaxy Score, creator attention, and trend discovery | `Official` | `Remote` | `apiKey` | [Docs](https://lunarcrush.com/developers/mcp) |
| [Santiment](https://academy.santiment.net/mcp-connector/) | Social volume, sentiment, trending stories, and on-chain metrics | `Official` | `Remote` | `OAuth` | [Docs](https://academy.santiment.net/mcp-connector/) |

### Security & Smart Contracts
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [BICScan](https://github.com/ahnlabio/bicscan-mcp) | AhnLab risk scores for addresses, domains, and dApp URLs | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/ahnlabio/bicscan-mcp) |
| [Crypto APIs AML](https://github.com/CryptoAPIs-io/cryptoapis-mcp-aml) | AML address checks and transaction screening for sanctions and fraud | `Official` | `Local` | `apiKey` | [GitHub](https://github.com/CryptoAPIs-io/cryptoapis-mcp-aml) |
| [Foundry MCP](https://github.com/PraneshASP/foundry-mcp-server) | Forge, Cast, and Anvil from your agent: test, deploy, call, estimate gas | `Community` | `Local` | `Mixed` | [GitHub](https://github.com/PraneshASP/foundry-mcp-server) |
| [GoPlus AgentGuard](https://github.com/GoPlusSecurity/agentguard) | Guard agents against wallet drains, unlimited approvals, and malicious skills | `Official` | `Local` | `No` | [GitHub](https://github.com/GoPlusSecurity/agentguard) |
| [OpenZeppelin Contracts](https://mcp.openzeppelin.com/) | Generate contracts from audited OpenZeppelin libraries across languages | `Official` | `Both` | `No` | [GitHub](https://github.com/OpenZeppelin/contracts-wizard/tree/master/packages/mcp) |
| [Slither MCP](https://github.com/trailofbits/slither-mcp) | Trail of Bits static analysis, detectors, and call graphs for Solidity | `Official` | `Local` | `No` | [GitHub](https://github.com/trailofbits/slither-mcp) |
| [Webacy](https://docs.webacy.com/integrations/mcp-server) | Wallet, token, vault, and RWA risk scores, holder analysis, sanctions flags | `Official` | `Remote` | `apiKey` | [Docs](https://docs.webacy.com/integrations/mcp-server) |

### Aggregators & Multi-tool
| Server | What It Is Good For | Maintainer | Transport | Auth | Source |
|---|---|---|---|---|---|
| [BlockRun](https://blockrun.ai/docs) | Pay-per-call crypto data, X/Twitter, Polymarket, and web research over x402 | `Official` | `Local` | `Mixed` | [GitHub](https://github.com/BlockRunAI/blockrun-mcp) |
| [CoinStats](https://github.com/CoinStatsHQ/coinstats-mcp) | Market data, portfolios, wallets, exchanges, DeFi, and news in one server | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/CoinStatsHQ/coinstats-mcp) |
| [Heurist Mesh](https://github.com/heurist-network/heurist-mesh-mcp-server) | 30+ crypto analysis agents behind one key | `Official` | `Both` | `apiKey` | [GitHub](https://github.com/heurist-network/heurist-mesh-mcp-server) |
| [Hive Intelligence](https://hiveintelligence.xyz) | One server over many crypto data providers, with a free anonymous lane | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/hive-intel/hive-sdk) |
| [Kukapay MCP Servers](https://github.com/kukapay/kukapay-mcp-servers) | Index of single-purpose community crypto servers (check each one's activity) | `Community` | `Local` | `Mixed` | [GitHub](https://github.com/kukapay/kukapay-mcp-servers) |
| [Surf](https://github.com/asksurf-ai/surf-mcp) | Prices, wallets, social, news, on-chain SQL, and prediction markets | `Official` | `Both` | `Mixed` | [GitHub](https://github.com/asksurf-ai/surf-mcp) |

## Safety Checklist

Servers marked `Wallet`, and exchange servers with trading scopes, can move real money. Before you connect one:

- **Start read-only.** Many servers have a flag for it: OKX `--read-only`, Bitget `--read-only` and `--paper-trading`, Gate `GATE_READONLY=true`, Kraken's default `market,account,paper` services.
- **Isolate funds.** Use a sub-account (Binance Agentic, Coinbase agent portfolio), a dedicated agent wallet (Phantom, OKX, Cobo), or a testnet.
- **Never give a main-wallet key.** Hot-key servers (`SOLANA_PRIVATE_KEY`, `HYPERLIQUID_PRIVATE_KEY`) should get a fresh wallet funded only with what you can lose.
- **Prefer unsigned transactions.** Jupiter, Aave, Morpho, LI.FI, 1inch, and KyberSwap return unsigned transactions that your own wallet signs.
- **Scope API keys.** Disable withdrawals and IP-restrict exchange keys.

## Resources

### Learn MCP
- [Model Context Protocol](https://modelcontextprotocol.io/) - Official introduction and docs.
- [MCP Specification](https://modelcontextprotocol.io/specification/latest) - Transports and authorization.
- [MCP Inspector](https://github.com/modelcontextprotocol/inspector) - Test and debug a server before wiring it into a client.
- [Claude Code MCP setup](https://code.claude.com/docs/en/mcp) - `claude mcp add` and scopes.
- [Claude custom connectors](https://support.claude.com/en/articles/11175166-getting-started-with-custom-connectors-using-remote-mcp) - Add remote servers in Claude.ai and Claude Desktop.
- [Cursor MCP setup](https://cursor.com/docs/context/mcp) - Configure servers in Cursor.
- [VS Code MCP setup](https://code.visualstudio.com/docs/copilot/customization/mcp-servers) - Configure servers for GitHub Copilot.

### Registries and Other Lists
- [Official MCP Registry](https://registry.modelcontextprotocol.io/) - Searchable registry of published servers.
- [awesome-mcp-servers (punkpeye)](https://github.com/punkpeye/awesome-mcp-servers) - The largest general MCP list; crypto sits under Finance & Fintech.
- [Glama MCP directory](https://glama.ai/mcp/servers) - Directory with quality and security scores.
- [Smithery](https://smithery.ai) - MCP registry and hosted installer.
- [hive-intel/awesome-crypto-mcp-servers](https://github.com/hive-intel/awesome-crypto-mcp-servers) - Crypto list with use-case routing, maintained by Hive Intelligence.
- [BlockRunAI/awesome-finance-mcp](https://github.com/BlockRunAI/awesome-finance-mcp) - Finance and crypto MCP list, maintained by BlockRun.
- [Free Crypto APIs](https://github.com/narekgevorgyan/free-crypto-apis) - Sister list of free and free-tier crypto APIs.

## Methodology

Each entry was checked in October 2026 against the provider's official docs or repository. Hosted endpoints were tested with a live MCP `initialize` request, and GitHub repositories were checked for recent activity and archive status.

An entry is included only if it:

- is a real MCP server (not only a docs-search server, agent skill, or CLI without MCP mode),
- is documented by its maintainer, and
- has a repository pushed within the last 12 months, or is an official hosted server that is documented and responding.

Official vendor servers are preferred. A community server is listed when no official one exists or when it is clearly better adopted. Notable exclusions: GOAT SDK and Base MCP (archived), Token Metrics and Moralis (repositories removed), Dune Sim (shut down), and the many single-purpose servers whose last update was in early 2025.

The weekly [freshness check](./.github/workflows/check-freshness.yml) opens an issue whenever a listed repository is archived, deleted, or inactive for more than a year.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for inclusion rules and validation.

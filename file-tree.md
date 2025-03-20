# Project Structure

## Directory Structure

```
/                           # Root directory
├── node_modules/           # Dependencies (generated)
├── package.json            # Project configuration
├── package-lock.json       # Dependency lock file (generated)
├── server.js               # Main server application
├── README.md               # Project documentation
├── task-log.md             # Task tracking
├── dev-notes.md            # Development notes
└── file-tree.md            # This file
```

## Component Organization

### Server Components
- **server.js**: Main Express application
  - Dependencies:
    - express
    - coingecko-api-v3
  - Features:
    - API routing
    - Error handling
    - CoinGecko API integration
  - Organization:
    - Basic endpoints
    - Simple endpoints
    - Coins endpoints
    - Contract endpoints
    - Asset platforms endpoints
    - Categories endpoints
    - Exchanges endpoints
    - Derivatives endpoints
    - NFTs endpoints
    - Exchange rates endpoints
    - Search endpoints
    - Trending endpoints
    - Global endpoints
    - Companies endpoints

## File Dependencies

### Core Dependencies
- **server.js** → Express.js, CoinGecko API Client

### Documentation
- **README.md** → Usage instructions for end users
- **task-log.md** → Progress tracking for developers
- **dev-notes.md** → Technical implementation details
- **file-tree.md** → Project structure overview

## Feature Mapping

### API Endpoints
The server implements 30+ API endpoints organized by category, following the official CoinGecko API structure:

#### Basic
- `/` - Health check (server.js)
- `/api/ping` - CoinGecko API status (server.js)

#### Simple
- `/api/simple/price` - Current prices (server.js)
- `/api/simple/token_price/:id` - Token prices by contract (server.js)
- `/api/simple/supported_vs_currencies` - Supported currencies (server.js)

#### Coins
- `/api/coins/list` - All supported coins (server.js)
- `/api/coins/markets` - Market data with filtering (server.js)
- `/api/coins/:coinId` - Detailed coin information (server.js)
- `/api/coins/:coinId/tickers` - Coin tickers (server.js)
- `/api/coins/:coinId/history` - Historical data (server.js)
- `/api/coins/:coinId/market_chart` - Market charts (server.js)
- `/api/coins/:coinId/market_chart/range` - Custom range charts (server.js)
- `/api/coins/:coinId/ohlc` - OHLC data (server.js)

#### Contract
- `/api/coins/:assetPlatformId/contract/:contractAddress` - Contract info (server.js)
- `/api/coins/:assetPlatformId/contract/:contractAddress/market_chart` - Contract charts (server.js)
- `/api/coins/:assetPlatformId/contract/:contractAddress/market_chart/range` - Custom range (server.js)

#### Asset Platforms
- `/api/asset_platforms` - Blockchain networks (server.js)

#### Categories
- `/api/coins/categories/list` - All categories (server.js)
- `/api/coins/categories` - Categories with market data (server.js)

#### Exchanges
- `/api/exchanges` - All exchanges (server.js)
- `/api/exchanges/list` - Exchange identifiers (server.js)
- `/api/exchanges/:exchangeId` - Exchange details (server.js)
- `/api/exchanges/:exchangeId/tickers` - Exchange tickers (server.js)
- `/api/exchanges/:exchangeId/volume_chart` - Volume data (server.js)

#### Derivatives
- `/api/derivatives` - Derivative tickers (server.js)
- `/api/derivatives/exchanges` - Derivative exchanges (server.js)
- `/api/derivatives/exchanges/:exchangeId` - Exchange details (server.js)
- `/api/derivatives/exchanges/list` - Exchange identifiers (server.js)

#### NFTs
- `/api/nfts/list` - All supported NFTs (server.js)
- `/api/nfts/:id` - NFT details (server.js)
- `/api/nfts/:asset_platform_id/contract/:contract_address` - NFT by contract (server.js)

#### Other
- `/api/exchange_rates` - Currency exchange rates (server.js)
- `/api/search` - Search functionality (server.js)
- `/api/trending` - Trending coins (server.js)
- `/api/global` - Global crypto data (server.js)
- `/api/global/decentralized_finance_defi` - DeFi data (server.js)
- `/api/companies/public_treasury/:coin_id` - Company holdings (server.js)

## Size and Metrics

### File Sizes
- **node_modules/**: ~2-5MB (estimated)
- **server.js**: ~20KB (expanded with comprehensive endpoints)
- Documentation files: ~3-5KB each (expanded with detailed documentation)

### Dependency Metrics
- Direct dependencies: 2 (express, coingecko-api-v3)
- Total dependencies: ~71 packages

### API Metrics
- Total endpoints: 30+
- API categories: 10+
- Parameter validations: 40+
- Error handling patterns: 3 (missing parameters, API errors, server errors) 
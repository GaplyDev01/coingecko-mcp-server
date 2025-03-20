# CoinGecko API Server

A Node.js Express server that provides a simplified and configurable interface to the CoinGecko cryptocurrency data API. This server supports both the free public API and the Pro API with automatic fallback.

## Features

- Comprehensive cryptocurrency data access
- Support for both CoinGecko Free and Pro APIs
- Automatic fallback to free API during development
- Simple RESTful endpoints
- Detailed error handling
- Environment variable configuration

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [API Endpoints](#api-endpoints)
- [Using CoinGecko Pro](#using-coingecko-pro)
- [Development](#development)
- [Troubleshooting](#troubleshooting)

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/coingecko-api-server.git
cd coingecko-api-server
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file based on the example:
```bash
cp .env.example .env
```

4. Edit the `.env` file to add your CoinGecko API key (if you have one)

5. Start the server:
```bash
node server.js
```

## Configuration

The server can be configured using environment variables in the `.env` file:

| Variable | Description | Default |
|----------|-------------|---------|
| `PORT` | The port the server will listen on | `3000` |
| `COINGECKO_API_KEY` | Your CoinGecko Pro API key | - |
| `CACHE_REFRESH_INTERVAL` | Cache refresh interval in minutes | `60` |

## API Endpoints

The server provides the following endpoints:

### Basic

- `GET /` - Health check
- `GET /api/ping` - Check CoinGecko API status

### Price Data

- `GET /api/simple/price` - Get price data for specified coins
  - Query params: `ids`, `vs_currencies`, `include_market_cap`, `include_24hr_vol`, `include_24hr_change`, `include_last_updated_at`, `precision`
  
- `GET /api/simple/token_price/:id` - Get token price by contract address
  - Path params: `id` (blockchain id)
  - Query params: `contract_addresses`, `vs_currencies`, `include_market_cap`, `include_24hr_vol`, `include_24hr_change`, `include_last_updated_at`, `precision`

- `GET /api/simple/supported_vs_currencies` - Get list of supported vs currencies

### Coins

- `GET /api/coins/list` - Get list of all coins
  - Query params: `include_platform`
  
- `GET /api/coins/markets` - Get market data for coins
  - Query params: `vs_currency`, `ids`, `category`, `order`, `per_page`, `page`, `sparkline`, `price_change_percentage`
  
- `GET /api/coins/:coinId` - Get coin details
  - Path params: `coinId`
  - Query params: `localization`, `tickers`, `market_data`, `community_data`, `developer_data`, `sparkline`

- Plus many more coin-specific endpoints (history, market charts, OHLC data)

### Additional Data

- `GET /api/global` - Get global cryptocurrency data
- `GET /api/search/trending` - Get trending coins
- `GET /api/exchanges` - Get exchange data
- `GET /api/asset_platforms` - Get asset platforms
- `GET /api/nfts` - Get NFT data
- And many more...

See the [CoinGecko API Documentation](https://www.coingecko.com/api/documentation) for detailed information about all available endpoints.

## Using CoinGecko Pro

This server supports the CoinGecko Pro API for increased rate limits and additional features. See [USING_COINGECKO_PRO.md](USING_COINGECKO_PRO.md) for detailed setup instructions.

Key benefits of using the Pro API:
- Higher rate limits
- Lower latency
- Additional endpoints
- Commercial usage rights

## Development

For development purposes, the server will automatically fall back to the free CoinGecko API if no API key is provided. This allows for easier local development without requiring a Pro subscription.

To contribute to this project:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Troubleshooting

Common issues:

- **429 Too Many Requests**: You've exceeded the rate limit. With the free API, this is typically 10-30 calls per minute. Consider upgrading to a Pro plan.
- **401 Unauthorized**: Your API key is invalid or expired.
- **403 Forbidden**: You're trying to access endpoints not included in your plan.
- **404 Not Found**: The resource or endpoint doesn't exist.
- **Connection Issues**: The CoinGecko API might be experiencing downtime. Check their status page.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- [CoinGecko](https://www.coingecko.com/) for providing the cryptocurrency data API
- [coingecko-api-v3](https://www.npmjs.com/package/coingecko-api-v3) for the Node.js client library 
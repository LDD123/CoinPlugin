# CoinPlugin

A LangBot plugin for querying cryptocurrency prices in real-time.

## Features

- Query real-time cryptocurrency prices in USD and CNY
- Support for 24-hour price changes
- Support for multiple popular cryptocurrencies
- Simple and intuitive command interface

## Commands

### `/info [coin_name...]`
Query cryptocurrency prices

**Examples:**
- `/info bitcoin` - Query Bitcoin price
- `/info btc` - Query Bitcoin price (using symbol)
- `/info eth` - Query Ethereum price
- `/info btc eth sol` - Query multiple coins at once

**Supported Coins:**
The plugin supports hundreds of cryptocurrencies including:
- Major coins: Bitcoin (btc), Ethereum (eth), Solana (sol), Ripple (xrp)
- Altcoins: Dogecoin (doge), Cardano (ada), Polygon (matic), Litecoin (ltc)
- Stablecoins: USDT, USDC, DAI
- And many more...

## Installation

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Start your LangBot instance and load the plugin

## Configuration

No special configuration required. The plugin uses public APIs to fetch real-time cryptocurrency prices.

## Technical Details

- Uses CoinGecko API for real-time pricing data
- Built with LangBot Plugin SDK
- Handles both USD and CNY price display
- Shows 24-hour percentage changes
- Comprehensive coin mapping with over 300 supported cryptocurrencies

## License

This plugin is part of the LangBot ecosystem and follows the corresponding licensing terms.
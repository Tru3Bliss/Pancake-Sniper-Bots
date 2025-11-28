# Bnb Pancakeswap Sniper

This tool allows users can detect new migration from four.meme to PancakeSwap.
It can be used for migration sniping if we integrate pancake swap.

## Configuration

### Environment Variables

Required:
- `PRIVATE_KEY` - Your wallet private key
- `SNIPER_CONTRACT_ADDRESS` - Your sniper contract address
- `WS_PROVIDER_URL` - WebSocket provider URL for event monitoring
- `RPC_PROVIDER_URL` - RPC provider URL for transactions
- `SEND_BNB` - Amount of BNB to send per trade (e.g., "0.0005")

Optional:
- `TOKEN_NAME_CONTAINS` - Filter out tokens by name (see Token Filtering section)
- `MIN_LIQUIDITY_BNB` - Minimum liquidity filter (see Liquidity Filtering section)

### Token Filtering (Optional)

You can filter out tokens by name before buying. Add this to your `.env` file:

- `TOKEN_NAME_CONTAINS` - Tokens with names containing these strings will be **SKIPPED** (case-insensitive)
  - Multiple keywords can be separated by commas
  - The bot will **SKIP** tokens if the name contains **ANY** of the specified keywords
  - The bot will **BUY** all other tokens that don't match the filter

**Examples:**
```env
# Skip tokens where name contains "Moon" (buy everything else)
TOKEN_NAME_CONTAINS=Moon

# Skip tokens where name contains "Moon" OR "DOGE" OR "Pepe" (buy everything else)
TOKEN_NAME_CONTAINS=Moon,DOGE,Pepe

# Skip tokens where name contains "Safe" OR "Moon" OR "Rocket" (buy everything else)
TOKEN_NAME_CONTAINS=Safe,Moon,Rocket
```

**Note:** 
- If `TOKEN_NAME_CONTAINS` is not set or empty, the bot will buy all detected tokens
- Filtering is case-insensitive
- Keywords are separated by commas (spaces around commas are automatically trimmed)
- This is a **blacklist** filter - tokens matching the keywords are excluded

### Liquidity Filtering (Optional)

You can filter tokens by minimum liquidity before buying. Add this to your `.env` file:

- `MIN_LIQUIDITY_BNB` - Minimum total liquidity required in BNB (e.g., "1.0" for 1 BNB minimum)
  - Pools with less liquidity than this will be skipped
  - Total liquidity = 2 × WBNB reserve (since AMM pools maintain equal value on both sides)

**Examples:**
```env
# Only buy tokens with at least 1 BNB total liquidity
MIN_LIQUIDITY_BNB=1.0

# Only buy tokens with at least 5 BNB total liquidity
MIN_LIQUIDITY_BNB=5.0

# Only buy tokens with at least 0.5 BNB total liquidity
MIN_LIQUIDITY_BNB=0.5
```

**Note:**
- If `MIN_LIQUIDITY_BNB` is not set or 0, liquidity filtering is disabled
- The bot calculates total liquidity as 2 × WBNB reserve
- This helps avoid low-liquidity tokens that may be rug pulls or have high slippage

## Development Process

✔ Monitoring (Completed)

✔ Sniping (Completed)

✔ Sniping as first buyer (Completed)

✔ Selling logic (Completed)

✔ Token filtering (Completed)


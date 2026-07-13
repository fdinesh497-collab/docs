---
title: TRON CLI Tool Reference
shortTitle: ts CLI reference
intro: 'Detailed usage information for the `ts` TRON blockchain CLI tool.'
contentType: reference
---

## Overview

The `ts` CLI tool is a command-line interface for interacting with the TRON blockchain. It provides quick access to token information, blockchain data, transaction details, and account analysis.

## General Usage

```bash
ts COMMAND [OPTIONS]
```

### Global Options

- `--raw` - Output raw data in compact format
- `--json` - Output data in JSON format

## Commands

### Help

Display all available subcommands and general usage information.

```bash
ts help
```

### Token Commands

#### Get Token Price by Symbol

Retrieve the current price of a token by its symbol.

```bash
ts token-price SYMBOL
```

**Example:**
```bash
ts token-price trx                    # Get TRX (TRON) price
ts token-price usdt --raw             # Get USDT price with raw output
```

#### Get Token Information

Retrieve detailed information about a specific token.

```bash
ts token SYMBOL
```

**Example:**
```bash
ts token usdt                         # Get USDT token information
ts token trx --json                   # Get TRX info in JSON format
```

#### Search Tokens

Search for tokens by name, symbol, or other criteria.

```bash
ts search QUERY
```

**Example:**
```bash
ts search usdt                        # Search for USDT-related tokens
ts search "stable coin" --json        # Search with multiple keywords
```

### Blockchain Commands

#### Get Latest Block

Display information about the most recent block on the TRON blockchain.

```bash
ts block
```

**Example:**
```bash
ts block                              # Get latest block info
ts block --raw                        # Get raw block data
```

#### Get Current TPS

Display the current Transactions Per Second (TPS) on the TRON network.

```bash
ts tps
```

**Example:**
```bash
ts tps                                # Get current TPS
ts tps --raw                          # Get raw TPS data
```

### Account Commands

#### Get Account Details

Retrieve comprehensive information about a TRON account.

```bash
ts account ADDRESS
```

**Parameters:**
- `ADDRESS` - TRON account address (starts with `T`)

**Example:**
```bash
ts account TXxx...                    # Get account details
ts account TXxx... --json             # Get account info in JSON format
```

#### Account Risk Check

Perform a security assessment of a TRON account to identify potential risks.

```bash
ts security-account ADDRESS
```

**Parameters:**
- `ADDRESS` - TRON account address (starts with `T`)

**Example:**
```bash
ts security-account TXxx...           # Check account security risks
ts security-account TXxx... --raw     # Get raw security data
```

### Transaction Commands

#### Get Transaction by Hash

Retrieve detailed information about a specific transaction.

```bash
ts tx HASH
```

**Parameters:**
- `HASH` - Transaction hash (transaction ID)

**Example:**
```bash
ts tx af949...                        # Get transaction details
ts tx af949... --json                 # Get transaction in JSON format
```

#### Get TRC20 Transfers

Retrieve TRC20 token transfer information for an address.

```bash
ts transfer-trc20 ADDRESS
```

**Parameters:**
- `ADDRESS` - TRON account address or contract address (starts with `T`)

**Example:**
```bash
ts transfer-trc20 TXxx...             # Get TRC20 transfers for address
ts transfer-trc20 TXxx... --raw       # Get raw transfer data
```

## Output Formats

### Default Format

Human-readable format with structured output.

```bash
ts token usdt
```

### Raw Format

Compact, minimized output ideal for scripting.

```bash
ts token usdt --raw
```

### JSON Format

Structured JSON output for programmatic use.

```bash
ts token usdt --json
```

## Common Use Cases

### Monitor Network Activity

Check current network performance and block information:

```bash
ts block      # Latest block
ts tps        # Current transactions per second
```

### Research Token Information

Look up token prices and details:

```bash
ts token-price trx              # Get TRX price
ts token usdt                   # Get detailed USDT info
ts search "stablecoin"          # Search for stablecoins
```

### Analyze Accounts

Examine account details and security:

```bash
ts account TXxx...              # View account details
ts security-account TXxx...     # Check account risks
```

### Track Transactions

Find transaction details and token transfers:

```bash
ts tx af949...                  # Look up transaction
ts transfer-trc20 TXxx...       # View TRC20 transfers for address
```

## Tips and Best Practices

- Use `--json` output when piping to other tools or scripts
- Use `--raw` for quick console checks or scripting with minimal overhead
- Always verify addresses start with `T` for TRON mainnet accounts
- Include transaction hashes and addresses fully for accurate lookups
- Use `ts help` to see the latest available commands and options

## Troubleshooting

### Invalid Address

If you receive an invalid address error, ensure:
- The address starts with `T`
- The address is correctly formatted
- You're using a mainnet address (not testnet)

### No Results Found

If a transaction or address returns no results:
- Verify the exact address or transaction hash
- Ensure the transaction has been confirmed on the network
- Check network status with `ts tps` and `ts block`

### Connection Issues

If commands fail with connection errors:
- Verify your internet connection
- Check TRON network status
- Try again after a few moments

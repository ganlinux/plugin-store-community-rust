---
name: signal-tracker-rust
description: "TODO: Brief description of what this skill does"
version: "1.0.0"
author: "TODO: Your Name"
tags:
  - TODO
---

# signal-tracker-rust

## Overview

TODO: Describe what this skill enables the AI agent to do.

> All on-chain write operations (signing, broadcasting, swaps, contract calls)
> MUST use onchainos CLI. You are free to query external data sources
> (third-party DeFi APIs, market data, analytics, etc.).

## Pre-flight Checks

Before using this skill, ensure:

1. The `onchainos` CLI is installed and authenticated
2. Network connectivity is available

## Commands

Below are working onchainos examples. Replace or extend them with your plugin's logic.

### Search for a Token

```bash
onchainos token search --query "ETH" --chain ethereum
```

**When to use**: When the user asks to find a token by name, symbol, or address.
**Output**: Token name, symbol, contract address, chain, price.

### Get Token Price

```bash
onchainos market price --address <TOKEN_ADDRESS> --chain ethereum
```

**When to use**: When the user asks for the current price of a specific token.
**Output**: Current price in USD, 24h change, volume.

### Get Wallet Balance

```bash
onchainos portfolio all-balances --address <WALLET_ADDRESS> --chain ethereum
```

**When to use**: When the user wants to check their token holdings.
**Output**: List of tokens with balances and USD values.

### Swap Tokens

```bash
onchainos swap quote --from ETH --to USDC --amount 1 --chain ethereum
```

**When to use**: When the user wants to exchange one token for another.
**Ask user to confirm** the quote before executing:

```bash
onchainos swap swap --from ETH --to USDC --amount 1 --chain ethereum
```

## Error Handling

| Error | Cause | Resolution |
|-------|-------|------------|
| "Token not found" | Invalid token symbol or address | Ask user to verify the token name |
| "Rate limited" | Too many API requests | Wait 10 seconds and retry once |
| "Chain not supported" | Wrong chain parameter | Show supported chains: ethereum, solana, base, bsc |
| "Insufficient balance" | Not enough tokens | Check balance with `onchainos portfolio all-balances` |

## Skill Routing

- For token swaps → use `okx-dex-swap` skill
- For wallet balances → use `okx-wallet-portfolio` skill
- For security scanning → use `okx-security` skill
- For smart money signals → use `okx-dex-signal` skill
- For meme token analysis → use `okx-dex-trenches` skill

## onchainos Commands Quick Reference

| Command | Description |
|---------|-------------|
| `onchainos token search` | Search tokens by name/symbol/address |
| `onchainos token info` | Get detailed token information |
| `onchainos market price` | Get current token price |
| `onchainos market kline` | Get price chart (candlestick) data |
| `onchainos swap quote` | Get DEX swap quote |
| `onchainos swap swap` | Execute DEX swap |
| `onchainos portfolio all-balances` | Get wallet token balances |
| `onchainos wallet send` | Transfer tokens (requires user confirmation) |
| `onchainos security token-scan` | Scan token for risks |
| `onchainos gateway gas` | Get current gas price |

---
name: _example-plugin
description: "Example skill showing the standard SKILL.md format"
version: "1.0.0"
author: "Plugin Store Team"
tags:
  - example
---

# Example Plugin

## Overview

This is an example skill that demonstrates the standard SKILL.md format.
It searches for token information and displays market prices.

> **This plugin is for reference only.** Do not install it.

## Pre-flight Checks

Before using this skill, ensure:

1. The `onchainos` CLI is installed and authenticated
2. Network connectivity is available

## Commands

### Search for a Token

```bash
onchainos token search --query "ETH" --chain ethereum
```

**When to use**: When the user asks to find a token by name, symbol, or address.
**Output**: Token name, symbol, contract address, chain, price.

### Get Market Price

```bash
onchainos market price --address "0x..." --chain ethereum
```

**When to use**: When the user asks for the current price of a specific token.
**Output**: Current price, 24h change, volume.

## Error Handling

| Error | Cause | Resolution |
|-------|-------|------------|
| "Token not found" | Invalid symbol or address | Ask user to verify the token name/address |
| "Rate limited" | Too many requests | Wait 10 seconds and retry |
| "Chain not supported" | Unsupported chain | Show supported chains: ethereum, solana, base, bsc |

## Skill Routing

- For token swaps → use `okx-dex-swap` skill
- For wallet balances → use `okx-wallet-portfolio` skill
- For security scanning → use `okx-security` skill
- For transaction broadcasting → use `okx-onchain-gateway` skill

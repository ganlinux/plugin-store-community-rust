# Example Plugin CLI Reference

## Token Search

```bash
onchainos token search --query <QUERY> [--chain <CHAIN>]
```

| Parameter | Required | Description |
|-----------|----------|-------------|
| `--query` | Yes | Token name, symbol, or contract address |
| `--chain` | No | Chain name (default: searches all) |

## Market Price

```bash
onchainos market price --address <ADDRESS> [--chain <CHAIN>]
```

| Parameter | Required | Description |
|-----------|----------|-------------|
| `--address` | Yes | Token contract address |
| `--chain` | No | Chain name (default: ethereum) |

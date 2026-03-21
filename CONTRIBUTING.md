# Contributing — Plugin Store Community

Thank you for contributing to the Plugin Store ecosystem! This guide walks you through submitting a new plugin.

## Prerequisites

- [plugin-store CLI](https://github.com/yz06276/plugin-store) installed
- A GitHub account
- Your plugin's SKILL.md written and tested locally

## Step 1: Scaffold Your Plugin

```bash
plugin-store init my-awesome-plugin
```

This creates a standard directory with all required files:

```
my-awesome-plugin/
  plugin.yaml          # Plugin manifest — fill this in
  skills/
    my-awesome-plugin/
      SKILL.md         # Your skill definition
      references/
        cli-reference.md
  LICENSE
  CHANGELOG.md
  README.md
```

## Step 2: Write Your Plugin

### plugin.yaml

This is your plugin's manifest. Key fields:

| Field | Required | Description |
|-------|----------|-------------|
| `name` | ✅ | Lowercase, hyphens only, 2-40 chars |
| `version` | ✅ | Semantic versioning (x.y.z) |
| `description` | ✅ | One-line description |
| `author.name` | ✅ | Your name |
| `author.github` | ✅ | Your GitHub username (must match PR author) |
| `license` | ✅ | SPDX identifier (MIT, Apache-2.0, etc.) |
| `category` | ✅ | One of: trading-strategy, defi-protocol, analytics, utility, security, wallet, nft |
| `permissions` | ✅ | Declare what your plugin can do |
| `components.skill.dir` | ✅ | Path to your skill directory |

### SKILL.md

Your skill definition tells AI agents how to use your plugin. Must include:

- YAML frontmatter with `name`, `description`
- Pre-flight checks
- Command reference
- Error handling
- Skill routing (when to defer to other skills)

### Permissions

**You must accurately declare all permissions.** The automated review will cross-check your SKILL.md against your declared permissions.

```yaml
permissions:
  wallet:
    read_balance: true       # Does your skill read wallet balances?
    send_transaction: false   # Does your skill initiate transfers?
    sign_message: false       # Does your skill sign messages?
    contract_call: false      # Does your skill call smart contracts?
  network:
    onchainos_commands:       # List every onchainos command your skill uses
      - "token search"
      - "market price"
  chains:
    - ethereum
    - solana
```

> **Note:** Community plugins cannot declare `send_transaction` or `contract_call` on their first submission. You must reach Verified Publisher status first.

## Step 3: Validate Locally

```bash
plugin-store lint my-awesome-plugin/
```

Fix all errors (❌) before submitting. Warnings (⚠️) are advisory but recommended to address.

## Step 4: Submit

1. **Fork** this repository
2. **Copy** your plugin directory into `submissions/`:
   ```bash
   cp -r my-awesome-plugin submissions/
   ```
3. **Commit and push** to your fork
4. **Open a Pull Request** against `main`

### PR Title Format

```
[new-plugin] my-awesome-plugin v1.0.0
```

For updates:
```
[update] my-awesome-plugin v1.1.0
```

## What Happens Next

### Automated Review (~10 minutes)

1. **Structure validation** — Schema, naming, license, file sizes
2. **AI code review** — Prompt injection scan, API compliance, quality score
3. **Security audit** — Permission consistency, MCP config safety, dangerous patterns
4. **Sandbox test** — Install/uninstall verification

### Human Review (1-3 days)

A maintainer reviews:
- Intent and usefulness
- Security considerations
- Quality and user experience
- Permission appropriateness

### After Merge

Your plugin is automatically added to the registry and becomes available via:
```bash
plugin-store install my-awesome-plugin
```

## Naming Rules

- Lowercase alphanumeric + hyphens: `[a-z0-9-]`
- 2-40 characters
- No consecutive hyphens (`--`)
- No reserved prefixes: `okx-`, `official-`, `plugin-store-`

## File Size Limits

- Single file: < 100 KB
- Total submission: < 1 MB

## Updating Your Plugin

1. Modify files in `submissions/your-plugin/`
2. Bump `version` in `plugin.yaml`
3. Update `CHANGELOG.md`
4. Open a new PR

If your update changes `permissions`, it will require full human review.

## Getting Help

- Open an [issue](https://github.com/yz06276/plugin-store-community/issues)
- See existing plugins in `submissions/` for examples

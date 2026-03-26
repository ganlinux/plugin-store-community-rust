# Plugin Store Community

Submit your plugin to the [Plugin Store](https://github.com/yz06276/plugin-store) ecosystem in 5 minutes.

## Quick Start (5 steps)

### Step 1: Create your plugin

```bash
plugin-store init my-plugin
```

This generates a ready-to-edit template:

```
my-plugin/
├── plugin.yaml       ← fill in your plugin info
├── skills/
│   └── my-plugin/
│       └── SKILL.md  ← write what your plugin does
├── LICENSE
└── README.md
```

### Step 2: Edit SKILL.md

SKILL.md teaches the AI agent how to use your plugin. Write what your plugin does and which `onchainos` commands it uses:

```markdown
# My Plugin

## Commands

### Search Token
​```bash
onchainos token search --query "ETH" --chain ethereum
​```
**When to use**: when the user asks to find a token.
```

### Step 3: Check locally

```bash
plugin-store lint ./my-plugin/
```

Fix any errors (❌) it reports, then re-run until you see ✓.

### Step 4: Submit

```bash
git clone git@github.com:yz06276/plugin-store-community.git
cd plugin-store-community
git checkout -b submit/my-plugin
cp -r /path/to/my-plugin submissions/my-plugin
git add submissions/my-plugin/
git commit -m "[new-plugin] my-plugin v1.0.0"
git push origin submit/my-plugin
```

Then open a **Pull Request** on GitHub.

### Step 5: Wait for review

Your PR automatically gets:

```
✅ Structure check (~30s)     — bot validates plugin.yaml + SKILL.md
📋 AI code review (~2min)     — Claude reads your code and writes a report
🔨 Build check (if binary)    — compiles your source code
👤 Human review (1-3 days)    — maintainer reads AI report, clicks Merge
```

Once merged, your plugin is live:
```bash
plugin-store install my-plugin
```

---

## Full Guides

- **[Development Guide (English)](./PLUGIN_DEVELOPMENT_GUIDE.md)** — all details, examples, error codes, FAQ
- **[开发指南（中文）](./PLUGIN_DEVELOPMENT_GUIDE_ZH.md)** — 完整的 plugin 开发与提交指南

## Getting Help

- Open an [issue](https://github.com/yz06276/plugin-store-community/issues)
- See `submissions/_example-plugin/` for a complete reference plugin
- Read the full [Development Guide](./PLUGIN_DEVELOPMENT_GUIDE.md) for troubleshooting

## License

Each plugin must include its own license. This repository is MIT licensed.

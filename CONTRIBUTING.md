# Contributing

One plugin, one copy of everything. Every client reads the same `skills/` folder; only the small manifest each client requires is its own.

## Release

After changing a skill or a manifest, set the new version in every manifest that carries one:

```bash
perl -pi -e 's/"version": "[0-9.]+"/"version": "1.0.5"/' plugin.json .claude-plugin/plugin.json gemini-extension.json
```

## ChatGPT package

ChatGPT takes the plugin as a zip. Generate it into `dist/` (gitignored):

```bash
mkdir -p dist && zip -r -X -D dist/raindrop.zip plugin.json mcp.json skills assets -x "*.DS_Store"
```
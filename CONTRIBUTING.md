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

## MCP Registry

`server.json` lists the hosted MCP server in the [MCP Registry](https://registry.modelcontextprotocol.io) as `io.raindrop/mcp`. Its `version` is its own, not the plugin version: the registry accepts each version once, so raise it whenever `server.json` changes, then publish with [`mcp-publisher`](https://modelcontextprotocol.io/registry/quickstart):

```bash
mcp-publisher validate
MCP_PRIVATE_KEY=<hex key> mcp-publisher login dns --domain raindrop.io
mcp-publisher publish
```

The key pairs with the `v=MCPv1` TXT record of `raindrop.io`, see [authentication](https://modelcontextprotocol.io/registry/authentication).

## ClawHub

[ClawHub](https://clawhub.ai) lists each skill separately under the `raindropio` publisher. Publish new and changed skills:

```bash
npx clawhub login
npx clawhub sync --root skills --owner raindropio --all
```

## skills.sh

Nothing to publish: [skills.sh](https://skills.sh/raindropio/skills) lists the repo from `npx skills add raindropio/skills` installs.
# Raindrop.io Skills

This repo is the one-stop shop for using [Raindrop.io](https://raindrop.io) with AI assistants and agents.

It contains the official Raindrop.io plugin: the configuration for the Raindrop.io MCP server and a collection of agent skills, packaged for popular agent harnesses.

## Model Context Protocol (MCP)

Raindrop.io hosts a remote MCP server at `https://api.raindrop.io/rest/v2/ai/mcp`. This allows secure MCP client access via OAuth. View the docs [here](https://help.raindrop.io/integrations/mcp).

## Agent skills

[Agent skills](https://agentskills.io/home) are instructions that agents can use to work faster and more accurately. Raindrop.io offers a collection of [skills](/skills) that help your agents organize a bookmark library the way Raindrop.io is meant to be used:

- [`sort-into-collections`](/skills/sort-into-collections/SKILL.md): file bookmarks into existing collections, create and suggest new ones.
- [`tag-bookmarks`](/skills/tag-bookmarks/SKILL.md): tag bookmarks using the existing tags of the library.
- [`library-checkup`](/skills/library-checkup/SKILL.md): fix inconsistent tags, misfiled bookmarks, duplicates, and broken links; empty the Trash.
- [`raindrop-help`](/skills/raindrop-help/SKILL.md): answer product questions from the official help docs.

If you use one of these popular agent harnesses, we recommend installing the official Raindrop.io plugin, which bundles the skills with the MCP server.

### Claude Code

Run this command in your terminal:

```bash
claude plugin install raindrop@claude-plugins-official
```

### Codex

Run this command in your terminal:

```bash
codex plugin add raindrop@openai-curated
```

### Grok Build

Run this command in your terminal:

```bash
grok plugin install raindrop --trust
```

### Gemini CLI

Run this command in your terminal:

```bash
gemini extensions install https://github.com/raindropio/skills
```

### Agent Plugins

Installation methods currently vary by client for the new [Agent Plugins](https://agent-plugins.org/) standard, but you can point your client to our package via its Git URL: `https://github.com/raindropio/skills`.

## Manual installation

> Manually installed skills don't auto-update. Run `npx skills update -y` to get the latest versions.

Run this command in your project:

```bash
npx skills add raindropio/skills
```

## Data

The plugin sends your requests to your Raindrop.io account through `https://api.raindrop.io/rest/v2/ai/mcp` and reads or changes bookmarks, collections, tags, and highlights there. It stores nothing itself.

## License

[MIT](LICENSE)
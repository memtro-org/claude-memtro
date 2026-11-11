# Memtro for Claude Code

Your company's memory and its connected systems as Claude Code tools. One install registers Memtro's MCP server and a skill that tells Claude when to use it.

```
/plugin marketplace add memtro-org/claude-memtro
/plugin install memtro@memtro
```

Claude Code asks for your API key when the plugin is enabled. That is the whole setup.

## Get a key

Create a personal API key on [Dashboard → Profile → API keys](https://platform.memtro.com/dashboard/profile/keys). The key acts as you: your memory, your connections, your permissions. It is marked sensitive, so Claude Code keeps it in your platform's secure credential store rather than `settings.json`. Change it later with `/plugin configure memtro@memtro`.

Installing from a shell instead of a session never prompts, so pass the key at install time:

```bash
claude plugin marketplace add memtro-org/claude-memtro
claude plugin install memtro@memtro --config api_key=sk-memtro-...
```

## What you get

**Tools.** `memtro_search`, `memtro_remember`, `memtro_why`, `memtro_measures` and the rest of Memtro's platform tools, plus one tool per connected system (GitHub, HubSpot, Xero, …) that you have access to. They arrive named `mcp__plugin_memtro_memtro__*`; use `/mcp` to inspect them.

**A skill.** `memtro` teaches Claude to search memory before guessing about the company, to read the agreed definition before quoting a business figure, and to save decisions with `memtro_remember` as self-contained statements. Claude loads it when a task calls for it; you can also run `/memtro:memtro` directly.

Everything Claude Code looks up this way is anchored into Memtro's memory, so what you work out in a session is there for the next question somebody asks in Chat.

## Self-hosted Memtro

Set **Memtro address** (`base_url`) to your installation, for example `https://memtro.internal.example.com`. Leave it alone for hosted Memtro.

## Fewer tools

An organisation with many connections serves many tools. The server already folds each connected system into one tool. To narrow further, register the server by hand instead of through this plugin, with a query string on the address: `?tools=memory` for the `memtro_*` tools alone, `?actions=none` to drop everything that changes anything, `?connectors=xero,github` for named systems. See the [manual setup](https://www.memtro.com/docs/guide-claude-code/).

## Memtro as the model, too

This plugin gives Claude Code Memtro's tools. Claude Code can also run *on* Memtro as its model, with routing, cost allowances and the request log. That is a `settings.json` change rather than a plugin; see [Memtro as Claude Code's model](https://www.memtro.com/docs/guide-claude-code/).

## License

MIT

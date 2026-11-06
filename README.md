# Respan plugins for Claude Code

The marketplace for [Respan](https://respan.ai)'s Claude Code plugins.

```bash
claude plugin marketplace add respanai/claude-plugins
```

| Plugin | What it does | Install |
| :- | :- | :- |
| `respan` | The Respan skill and the hosted Respan MCP server: query traces and logs, run evals, manage prompts and datasets | `claude plugin install respan@respan` |
| `session-traces` | Sends your Claude Code sessions to Respan as traces, with a span for each model request and tool call | `claude plugin install session-traces@respan` |

After you install `session-traces`, run `/plugin configure session-traces@respan` in Claude Code to set your Respan API key. Installing it turns tracing on, so install it only if you want your sessions sent to Respan. See the [Claude Code integration docs](https://www.respan.ai/docs/integrations/claude-code).

## How this repository works

This repository only lists the plugins. Their code lives in [respanai/respan](https://github.com/respanai/respan), in `claude-plugin/` and `claude-tracing-plugin/`, and each entry here points at its folder with a `git-subdir` source. Installing a plugin downloads that folder only, not the rest of the repository.

To release a change, merge it into `respanai/respan` with a higher `version` in the plugin's `.claude-plugin/plugin.json`. Users get it with `claude plugin marketplace update respan`.

Check the marketplace file with:

```bash
claude plugin validate . --strict
```

# Upstream tracking

| Plugin | Upstream | Last synced commit (last change to that path) | Synced on |
|---|---|---|---|
| discord | https://github.com/anthropics/claude-plugins-official/tree/main/external_plugins/discord | `c5b12e00f542249d808782afbaa074b9493507b1` (v0.0.4) | 2026-10-26 |

## Changes in this fork

- discord: adds the `create_thread` tool (create a standalone thread in a channel, start one from an existing message, or create a post in a forum channel with its first message). Version is `0.0.4-sozu.N`. If upstream issue #1144 lands, switch to the upstream implementation.
- discord: adds an optional per-channel `threadRequireMention` to `access.json` (overrides `requireMention` for messages in that channel's threads; unset = same as before).

## Branches

- `upstream`: unmodified copies of the upstream files only. Never edit by hand.
- `main`: merges `upstream` and adds this fork's changes. Claude Code reads `plugins/discord` from this checkout directly.

## How to sync (done by the `discord-fork-sync` scheduled task)

1. Find the latest upstream commit that touched `external_plugins/discord` (`gh api "repos/anthropics/claude-plugins-official/commits?path=external_plugins/discord&per_page=1"`). If it matches the table above, stop.
2. On the `upstream` branch, replace `plugins/discord` with the upstream files and commit (mention the upstream commit in the message).
3. Merge `upstream` into `main`. On conflict, abort the merge and report.
4. Update the table above, and set `version` in `plugin.json` to the upstream version plus `-sozu.N`.
5. If `package.json` or `bun.lock` changed, run `bun install` in `plugins/discord`.

# claude-plugins

A small Claude Code plugin marketplace with forks of official plugins plus small, generic additions.

```sh
claude plugin marketplace add sozuuuuu/claude-plugins
claude plugin install discord@sozuuuuu
```

Channels from non-official marketplaces are not on the research-preview allowlist, so `--channels plugin:discord@sozuuuuu` loads the tools but drops inbound messages. Start with the development flag instead:

```sh
claude --dangerously-load-development-channels plugin:discord@sozuuuuu
```

## Plugins

| Plugin | Upstream | Changes |
|---|---|---|
| `discord` | [anthropics/claude-plugins-official `external_plugins/discord`](https://github.com/anthropics/claude-plugins-official/tree/main/external_plugins/discord) | Adds a `create_thread` tool: creates a public thread in an allowlisted guild channel, either standalone or from an existing message (`message_id`), or a new post in an allowlisted forum channel (with `text` as its first message). It goes through the same outbound allowlist check as the other tools. See [anthropics/claude-plugins-official#1144](https://github.com/anthropics/claude-plugins-official/issues/1144). |

The `upstream` branch holds unmodified upstream copies; `main` merges it and adds the changes above. Synced upstream commits and the sync procedure are in [UPSTREAM.md](UPSTREAM.md).

## License

`plugins/discord` is Apache-2.0 (see [plugins/discord/LICENSE](plugins/discord/LICENSE)), modified as described above.

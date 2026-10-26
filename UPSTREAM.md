# 上流（upstream）の追跡

| プラグイン | 上流 | 取り込み済みのコミット（そのパスを最後に変えたもの） | 取り込んだ日 |
|---|---|---|---|
| discord | https://github.com/anthropics/claude-plugins-official/tree/main/external_plugins/discord | `c5b12e00f542249d808782afbaa074b9493507b1`（v0.0.4） | 2026-10-26 |

## フォークでの変更

- discord: `create_thread` ツールを追加（チャンネルに新しいスレッドを作る／既存メッセージからスレッドを作る）。版は `0.0.4-sozu.N`。上流の issue #1144 が取り込まれたら、そちらに寄せる

## ブランチ

- `upstream`: 上流のファイルをそのまま置くだけのブランチ（手を入れない）
- `main`: `upstream` をマージしたうえでフォークの変更を足したもの。Claude Code はこのディレクトリ（`plugins/discord`）を直接読む

## 追従のしかた（定期タスク `discord-fork-sync` が行う）

1. 上流で `external_plugins/discord` を最後に変えたコミットを調べる（`gh api "repos/anthropics/claude-plugins-official/commits?path=external_plugins/discord&per_page=1"`）。上の表と同じなら終わり
2. `upstream` ブランチに上流のファイルを丸ごと置き直してコミット（メッセージに上流のコミットを書く）
3. `main` に `upstream` をマージ。衝突したらマージを中止して報告する
4. 上の表を更新し、`plugin.json` の版を上流の版＋`-sozu.N` に合わせる
5. `package.json` か `bun.lock` が変わったら `plugins/discord` で `bun install`

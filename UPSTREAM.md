# 上流（upstream）の追跡

| プラグイン | 上流 | 取り込み済みのコミット | 日付 |
|---|---|---|---|
| discord | https://github.com/anthropics/claude-plugins-official/tree/main/external_plugins/discord | `2a8ad9f74633d10e3d9bb0660a03bfc6e50584b1`（v0.0.4） | 2026-10-26 |

## フォークでの変更

- discord: `create_thread` ツールを追加（チャンネルに新しいスレッドを作る／既存メッセージからスレッドを作る）。上流の issue #1144 が取り込まれたら、そちらに寄せる

## 追従のしかた

上流の `external_plugins/discord` を取得して `plugins/discord` と比べ、上流側の変更を取り込む。フォークでの変更（上の一覧）と衝突したら手で直す。取り込んだら上の表のコミットと日付を更新する。

# Internal Comms - 社内広報・発信システム

## 概要

社内向けコンテンツの収集・管理・自動発信を担う部署。
ネタはClaudeと手動で作成し、毎朝 `#出社メンバー`（ID: `C0A83PD42J0`）に自動投稿する。

## ディレクトリ構成

```
.internal-comms/
├── CLAUDE.md
├── commands/
│   ├── post-daily-tips.md      # 毎朝9時Routine：Slackへ自動投稿
│   └── prepare-daily-tips.md   # 参考：ネタ調査フローのメモ（手動運用時に参照）
└── content/
    └── efficiency-tips/
        ├── _template.md        # ネタファイルのテンプレート
        └── YYYY-MM-DD.md       # 日付ごとのネタファイル
```

## 運用フロー

```
【手動】あなたとClaudeでネタを作成
  → content/efficiency-tips/YYYY-MM-DD.md に保存

【自動・毎朝9時】Routineが発火
  → ファイルを読んでSlackに投稿
```

## Routine設定（Claude Code UIで登録）

| 名前 | 時刻 | プロンプト |
|------|------|-----------|
| `毎朝効率化tips投稿_出社メンバー` | 毎日 9:00 | 以下の手順に従って実行してください：1. 今日の日付をYYYY-MM-DD形式で確認する 2. WebFetchで `https://raw.githubusercontent.com/ovis03/kse-efficiency-tips/main/YYYY-MM-DD.md` を取得する（日付を置き換える）3. 取得できない場合はスキップして終了 4. 取得できた場合、#出社メンバー（channel ID: C0A83PD42J0）に `**【M/Dのtips】** [絵文字]` を親投稿し、本文をスレッドにリプライする 5. `.png` 版URLも試してあれば画像もスレッドに投稿する |

**ネタの追加フロー（macOS側）**
`/internal-comms` → ネタ作成 → `queue/YYYY-MM-DD.md` に保存 → `git push`（queue/リポジトリ: https://github.com/ovis03/kse-efficiency-tips）

## 投稿フォーマット

- **親メッセージ**：`【M/Dのtips：タイトル】 [絵文字]`（プレーンテキスト・タイトル含む）
- **スレッド返信**：導入 → `▼動画（分数）` → URL → 学び・効果説明
- ★ 太字・下線は Slack 側で手動装飾する前提。ファイル中に `*` `**` 等のマークダウン装飾は入れない
- 絵文字は反映されるのでOK

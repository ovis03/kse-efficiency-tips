---
description: 翌日以降の効率化tipsネタを調査・作成し、queueに保存する（手動運用用）
---

## ステップ1：ネタ候補の調査

1. `queue/` 内のファイルを確認し、最後にストックされている日付を調べる
2. 次に必要な日付（最終ストック日の翌日）を決定する
3. 以下の観点でネタ候補を5件程度提示する：

   **ネタの選定基準**
   - 社会人が仕事や日常で実践できる効率化・生産性向上の内容
   - YouTube動画またはPodcastが存在するもの（URLが実在するもの）
   - 直近のqueueやarchiveと同じネタの重複を避ける

   **よく使うチャンネル・番組**
   - まこなり社長（YouTube）
   - 勝間和代（YouTube / Spotify）
   - その他：生産性・仕事術・セルフケア系のYouTuber・Podcastホスト

   **提示フォーマット（候補リスト）**
   ```
   No. チャンネル名｜動画/放送タイトル（推定分数）
   → 一言で内容：〇〇について解説。〇〇な人に刺さる内容。
   ```

---

## ステップ2：ネタの選定

4. ユーザーが候補から1件を選ぶ（または別のURLを指定する）
5. 指定がある場合はURLをWebFetchで取得し、タイトル・チャンネル名・長さを確認する

---

## ステップ3：下書き作成

6. `_template.md` の形式に従って下書きを作成し、ユーザーに提示する：
   - frontmatter：`topic`（チャンネル名｜動画タイトル）、`posted: false`
   - 親メッセージ：`【M/Dのtips：タイトル（30字以内）】 [絵文字]`（プレーンテキスト・タイトル含む）
   - スレッド本文：導入、▼動画（分数）、URL、学び・効果説明
   - ★ 太字・下線は Slack 側で手動装飾する前提。ファイル中に `*` `**` 等のマークダウン装飾は入れない

7. ユーザーに確認を取る（「このまま保存しますか？」）

---

## ステップ4：保存

8. OKが出たら `queue/YYYY-MM-DD.md` に保存する
   - YYYY-MM-DDは投稿予定日（次に必要な日付）
   - 保存先: `/Users/mh/.claude/KSE-claude/.internal-comms/content/efficiency-tips/queue/`

9. GitHubにpushする：
   ```
   cd /Users/mh/.claude/KSE-claude/.internal-comms/content/efficiency-tips/queue
   git add YYYY-MM-DD.md
   git commit -m "add: YYYY-MM-DD tips"
   git push
   ```

10. 「保存しました：queue/YYYY-MM-DD.md（GitHub pushも完了）」と報告する
11. 続けてもう1件作る場合はステップ1に戻る

---
description: 今日の効率化tipsをSlackの#出社メンバーに投稿する（毎朝9時Routine用）
---

1. 今日の日付をYYYY-MM-DD形式で確認する

2. 以下のURLから今日のネタファイルをWebFetchで取得する：
   `https://raw.githubusercontent.com/ovis03/kse-efficiency-tips/main/YYYY-MM-DD.md`
   （YYYY-MM-DDを今日の日付に置き換える）

3. ファイルが取得できない（404など）場合:
   - 投稿をスキップする
   - 処理を終了する

4. ファイルが取得できた場合、内容を読み込む

5. `#出社メンバー`（channel ID: C0A83PD42J0）に親メッセージを投稿する:
   ```
   **【M/Dのtips】** [ネタファイルの親メッセージに記載の絵文字]
   ```
   （M/Dは今日の日付。例: **【5/5のtips】** 😴）

6. その投稿のスレッドに、ファイルの本文をリプライとして投稿する

7. 以下のURLに画像ファイルが存在する場合はスレッドにも投稿する：
   `https://raw.githubusercontent.com/ovis03/kse-efficiency-tips/main/YYYY-MM-DD.png`

作成中です！ すみません何でもはしません！

* 話者はAssistantSeikaの話者一覧の先頭から持ってくる
* commentary_backend\config\defaultSpeaker.jsonをいじると実況内容を変えられる
  * いじりかたは察してください
  * GUI化は最優先TODOです
* defaultSpeaker.jsonをコピーしてxxxx.json（xxxxは[AssistantSeikaの話者一覧で確認できるcid](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-004)。例えば1707.jsonなら東北きりたん）を作成すると、話者毎に実況内容を変えられる
  * GUI化は最優先TODOです

# 仕組み

* [MTG Arena](https://mtg-jp.com/mtgarena/)
  * Player.logを出力する。
* mtgatracker_backend
  * Player.logを解析する。
  * WebSocketサーバとしてWebSocketクライアントの接続を待つ。<br />WebSocketクライアントが接続してきたら、Player.logを解析した結果をJSONメッセージとして渡す。
* commentary_backend
  * WebSocketクライアントとして、mtgatracker_backendに接続する。<br />JSONメッセージを受け取ったら、config\xxxx.jsonと合わせて実況内容を組み立ててSeikaSay2を実行する。
* SeikaSay2
  * 受け取った実況内容をAssistantSeikaに渡す。
* [AssistantSeika](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/start)
  * 受け取った実況内容を音声合成ソフトにしゃべらせる。
* 音声合成ソフト
  * しゃべる。

# FAQ

## 挙動

### 実況

* カード名の読み方が間違っている。例えば茜ちゃんが平地を「ひらち」と読む。
  * 音声合成ソフト側で辞書登録してください。<br />茜ちゃんが「ひらち」と読むのはかわいいのでそのままでもいいかとも思います。
* ライフがマイナスになったときに「マイナス」と言わない。
  * SofTalkで発生することを確認済です。<br />commentary_backendは音声合成ソフトに「-5」みたいな文字列を渡しているだけなので、音声合成ソフト側でマイナスを読むようになっていないとcommentary_backend側ではどうしようもないです。
* 実況のタイミング遅くない？
  * MTG Arena側のログ出力タイミングに依存するので、早められないです。
* 対戦終了の実況後にライフ減少の実況をするんだけど
  * MTG Arena側のログ出力タイミングに依存するので以下略。
* VOICEROID2だとピッチ調整パラメータが初期化されてしまうことがある。
  * SeikaSay2が、保存されたボイスプリセットの設定値ではなく、製品スキャン時の設定値に戻してしまいます。<br />VOICEROID2側でボイスプリセットの設定値にしたあと、VOICEROID2を再起動すれば解消されると思います。

### その他

* ログファイル（.log）は何？
  * デバッグ用なので無視してください。<br />最大10ファイルしか作成されないようになっています。削除しても問題ありません。<br />
* `--- Logging error ---`って表示されたんだけど？
  * 「ü」等の一部の環境依存文字を含むログを出力しようとした場合に表示されます。<br />典型的には、対戦相手の名前に環境依存文字が含まれていることがあります。<br />動作には影響しないので、無視してください。<br />
* `不明なxxx: yyy`って表示されたんだけど？
  * 未対応のメッセージが届いたことを示します。対応したいので、表示された内容と、可能であれば表示された状況を教えてください。

## 仕組み

* exe以外に大量のファイルがあるの何とかならない？
  * 外部ライブラリのライセンスの都合上、1ファイルに統合できないのでこうしています。
* mtgatracker_backendとcommentary_backendは統合できないの？
  * mtgatracker_backendはもともと[MTGATracker](https://mtgatracker.com/)の一部品なので、最新のMTG Arenaのログを解析するための必要最低限の改修に留めています。<br />※本家MTGATrackerは2020年7月を最後に更新が停止しており、最新のMTG Arenaのログを解析できません<br />MTGATracker自体、backendとfrontendの間でWebSocketを使って情報の受け渡しを行っているので、commentary_backendと分割することは想定通りの使用方法と言えます。
* commentary_backendから直接AssistantSeikaに実況内容を渡せないの？
  * AssistantSeikaに実況内容を渡すためのツールがSeikaSay2です。
* commentary_backendから直接音声合成ソフトに実況内容を渡せないの？
  * やろうとしたけど力不足で無理でした。先人の成果物はありがたく利用させていただくのが吉、はっきりわかんだね。

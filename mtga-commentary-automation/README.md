# これは何？

MTG ArenaをVOICEROID等に実況してもらうためのツールです。<br />
紹介動画（ https://www.nicovideo.jp/watch/sm39704958 ）を見ればおおよそ分かると思います。

# 動作条件

* OSがWindowsであること。
* MTG Arenaがインストール済であること。
* MTG Arenaの詳細ログ（プラグインのサポート）がONであること。
* AssistantSeikaがインストール済であること。
  * https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-001a
* AssistantSeikaが対応している音声合成製品がインストール済であること。
  * https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E5%AF%BE%E5%BF%9C%E8%A3%BD%E5%93%81

# 導入方法

* mtga-commentary-automation.zipをダウンロードして、適当なフォルダに展開する。
  * https://github.com/poslogithub/binary-dist/raw/main/mtga-commentary-automation/mtga-commentary-automation.zip
* commentary_backendフォルダ（commentary_backend.exeファイルが存在するフォルダ）に、AssistantSeikaに同梱されているSeikaSay2.exeファイルをコピーする。

# 起動方法

1. MTG Arenaを起動する。
2. AssistantSeikaと音声合成製品を起動する。
3. AssistantSeikaの製品スキャンを実行する。
4. mtgatracker_backend.exeを実行する。
5. commentary_backend.exeを実行する。

# 配布場所

https://github.com/poslogithub/binary-dist/tree/main/mtga-commentary-automation

# ライセンス

MIT License

Copyright (c) 2021 poslogithub

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

mtgatrackerおよび外部ライブラリのライセンスはLICENSEフォルダを参照してください。

# 実況内容の置換される文字列

話者ウィンドウで指定する実況内容に含まれる、以下の文字列はカード名等に置換されます。

* カードを引いた時
  * `{card}`: 引いたカード名（自分のアクションのみ）
* カードを捨てた時
  * `{card}`: 捨てたカード名
* 土地をプレイした時
  * `{card}`: プレイしたカード名
* 呪文を唱えた時
  * `{card}`: 唱えたカード名
* 呪文が打ち消された時
  * `{source}`: 打ち消し呪文名
  * `{target}`: 打ち消された呪文名
* 呪文が解決された時
  * `{card}`: 解決された呪文名
* 攻撃クリーチャー指定時
  * `{attacker}`: 攻撃クリーチャー名
* ブロッククリーチャー指定時
  * `{attacker}`: 攻撃クリーチャー名
  * `{blocker}`: ブロッククリーチャー名
* ライフが増えた時
  * `{life_from}`: 増える前のライフ総量
  * `{life_to}`: 増えた後のライフ総量
  * `{life_diff}`: 増えたライフ量
* ライフが減った時
  * `{life_from}`: 減る前のライフ総量
  * `{life_to}`: 減った後のライフ総量
  * `{life_diff}`: 減ったライフ量
* クリーチャーが死亡した時
  * `{card}`: 死亡したクリーチャー名
* パーマネントが破壊された時
  * `{card}`: 破壊されたパーマネント名
* パーマネントを生け贄に捧げた時
  * `{card}`: 生け贄に捧げられたパーマネント名
* カードが追放された時
  * `{card}`: 追放されたカード名
* カードが墓地に置かれた時
  * `{card}`: 墓地に置かれたカード名
* カードが創出された時
  * `{card}`: 創出されたカード名

# 既知の不具合

* 直したけど難しいもの（MTGATrackerの実装に依存するため）
  * トークン関連の実況をしない。
* 直せないもの（MTG Arenaのログ出力に依存するため）
  * 実況のタイミングが早い/遅い。
  * 対戦終了の実況後にライフ減少やクリーチャー死亡等の実況をする。
  * ネットワークの再接続が行われた際に、ゲーム開始時の実況をしたり、ライフ変動時の変動前ライフ総量が初期ライフ総量であるかのような実況をする。

# FAQ

## 実況

* カード名の読み方が間違っている。例えば茜ちゃんが平地を「ひらち」と読む。
  * 音声合成ソフト側で辞書登録してください。<br />茜ちゃんが「ひらち」と読むのはかわいいのでそのままでもいいかとも思います。<br />
* ライフがマイナスになったときに「マイナス」と言わない。
  * SofTalkで発生することを確認済です。<br />commentary_backendは音声合成ソフトに「-5」みたいな文字列を渡しているだけなので、音声合成ソフト側で「-」を「マイナス」を読むようにしてもらうしかないです。

## その他

* 自動実況を録画/配信できない
  * Windowsの標準機能であるXbox Game Barによる録画は、デフォルトでは録画対象アプリケーションとマイク入力の音声しか録音してくれません。全ての音声を録音するようにXbox Game Barの設定を変更する必要があります。設定変更方法は、下記URLを参照してください。
    * [富士通Q&A - [Windows 10] Xbox Game Barでアプリの音声が録音されません。 - FMVサポート : 富士通パソコン](https://www.fmworld.net/cs/azbyclub/qanavi/jsp/qacontents.jsp?PID=4811-2677)<br />この設定を行った場合、システム通知音等を含め全ての音声が録音されることに注意してください。
  * Xbox Game Bar以外による録画や配信は分かりませんが、同じような制約がある可能性があります。
* commentary_backendを終了すると、mtgatracker_backendも勝手に終了する。
  * 仕様です。<br />commentary_backend終了後は、mtgatracker_backendも再起動しないと挙動がおかしくなるので、そのようにしました。
* ログファイル（.log）は何？
  * デバッグ用なので無視してください。<br />最大10ファイルしか作成されないようになっています。削除しても問題ありません。<br />
* `--- Logging error ---`って表示されたんだけど？
  * 「ü」等の一部の環境依存文字を含むログを出力しようとした場合に表示されます。<br />典型的には、対戦相手の名前に環境依存文字が含まれていることがあります。<br />動作には影響しないので、無視してください。<br />
* `不明なxxx: yyy`って表示されたんだけど？
  * 未対応のメッセージが届いたことを示します。<br />対応したいので、表示された内容と、可能であれば表示された状況を教えてください。

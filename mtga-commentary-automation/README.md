# これは何？

MTG ArenaをVOICEROID等に実況してもらうためのツールです。<br />
紹介動画（ https://www.nicovideo.jp/watch/sm39704958 ）を見ればおおよそ分かると思います。<br />
[ゆかりねっとコネクターNeo](https://www.machanbazaar.com/ync-neo/)と連携することで、字幕やカード画像の表示もできるようになります。参考動画：https://www.nicovideo.jp/watch/sm39993445

# 動作条件

* OSがWindowsであること。
* MTG Arenaがインストール済であること。
* MTG Arenaの詳細ログ（プラグインのサポート）がONであること。
* AssistantSeikaがインストール済であること。
  * https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-001a
* AssistantSeikaが対応している音声合成製品がインストール済であること。
  * https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E5%AF%BE%E5%BF%9C%E8%A3%BD%E5%93%81
* ゆかりねっとコネクターNeoがインストール済であること。<br />（ゆかりねっとコネクターNeoとの連携機能を利用する場合のみ）
  * https://www.machanbazaar.com/ync-neo/

※ゆかりねっとコネクターNeoとの連携機能だけを利用する場合、AssistantSeikaと音声合成製品のインストールは不要。

# 導入方法

* mtga-commentary-automation.zipをダウンロードして、適当なフォルダに展開する。
  * https://github.com/poslogithub/binary-dist/raw/main/mtga-commentary-automation/mtga-commentary-automation.zip
* commentary_backendフォルダ（commentary_backend.exeファイルが存在するフォルダ）に、AssistantSeikaに同梱されているSeikaSay2.exeファイルをコピーする。

※ゆかりねっとコネクターNeoとの連携機能だけを利用する場合、SeikaSay2.exeファイルをコピーは不要。

# 起動方法

1. MTG Arenaを起動する。
2. AssistantSeikaと音声合成製品を起動する。
3. AssistantSeikaの製品スキャンを実行する。
4. MTGA自動実況ツール起動.batを実行する。
5. ゆかりねっとコネクターNeoを起動する。<br />（ゆかりねっとコネクターNeoとの連携機能を利用する場合のみ）
6. ゆかりねっとコネクターNeoのMTGカード支援プラグインの設定を開き、カード特定辞書にmtgatracker_backendフォルダ配下のCardDictionary.csvファイルを指定する。<br />（初回のみ。ゆかりねっとコネクターNeoとの連携機能を利用する場合のみ）

* ゆかりねっとコネクターNeoとの連携機能だけを利用する場合、
  * AssistantSeikaと音声合成製品の起動は不要。
  * commentary_backend起動後のAssistantSeika 起動確認で「いいえ」を押下する。

## 配布場所

https://github.com/poslogithub/binary-dist/tree/main/mtga-commentary-automation

## 連絡先

https://twitter.com/poslog

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

# より詳しい使用方法

## 実況内容の置換される文字列

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
* トークンが生成された時
  * `{card}`: 生成されたトークン名
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
  * `{card}`: 生け贄に捧げたパーマネント名
* カードが追放された時
  * `{card}`: 追放されたカード名
* カードが墓地に置かれた時
  * `{card}`: 墓地に置かれたカード名
* カードが創出された時
  * `{card}`: 創出されたカード名

## WAVファイル出力

[説明動画](https://www.nicovideo.jp/watch/sm39814379)

設定ウィンドウで「WAVファイル出力」を「WAVファイル出力用batファイルを作成する」にすると、commentary_backendフォルダに「WAVファイル出力_YYYYMMDD_hhmmss.bat」ファイルが作成されます。<br />
**以下の条件を全て満たしてから**このbatファイルを実行すると、実況内容が個別のWAVファイルとしてcommentary_backend\wavフォルダに出力されます。<br />

* AssistantSeikaと音声合成製品が起動している。
* AssistantSeikaの製品スキャンが実行済である。
* AssistantSeikaの [基本設定]タブ > [音声キャプチャ] > [音声保存時に再生デバイスをキャプチャする] のチェックが入っている。（デフォルト）
* AssistantSeikaの [基本設定]タブ > [音声キャプチャ] > [16bitのwavファイルを使用] が選択されている。（AviUtl使用時のみ？）
* スピーカーから何の音も出ていない。

## [ゆかりねっとコネクターNeo](https://www.machanbazaar.com/ync-neo/)との連携

設定ウィンドウで「ゆかりねっとコネクターNeo」を「ゆかりねっとコネクターNeoに実況内容を連携する」にすると、ゆかりねっとコネクターNeoの外部ツールから文章を受け取るAPIに実況内容を送るようになります。<br />
これにより、ゆかりねっとコネクターNeo側の設定内容次第で、字幕を出したり、[MTGカード支援プラグイン](https://www.machanbazaar.com/plugin_mtg/)によりカード画像を表示したりできます。<br />
MTGカード支援プラグインを使用するためのカード特定辞書(Card Dictionary)は、mtgatracker_backend.exeを起動した時点でmtgatracker_backendフォルダに自動的に作成されます（commentary_backendフォルダではありません）。<br />
ファイル名は「CardDictionary.csv」です。<br />

### 自動実況させずにゆかりねっとコネクターNeoとの連携を行う

MTGカード支援プラグインを使ってカード画像を表示したいけど、実況は自分でやるので自動実況はしてほしくない、という場合のやり方です。<br />
AssistantSeikaが未起動、または未導入の状態でcommentary_backendを起動すると、AssistantSeika起動確認ダイアログが表示されます。<br />
AssistantSeika起動確認ダイアログで「いいえ」をクリックすると、話者にダミー話者が設定されます。<br />
ダミー話者は実況をしませんが、実況しているかのようにゆかりねっとコネクターNeoとの連携が可能です。<br />
ダミー話者も他の話者と同じく、実況内容を変更することが可能です。<br />

### カード画像以外の画像を表示する

1. mtgatracker_backendフォルダにある「_Append.csv」ファイルを「Append.csv」にリネームする。
2. Append.csvファイルの内容を変更する。<br />例えばライフ減少時に画像を表示させる場合は「くらって,ライフ減少」という行を追加する。<br />
3. ゆかりねっとコネクターNeoのMTGキャッシュフォルダ（マイ ドキュメント\YukarinetteConnector\MTGCache）に表示させたい画像ファイルを配置する。<br />例えばライフ減少時に画像を表示させる場合は「ライフ減少.jpg」というファイルを配置する。<br />拡張子がjpgであれば、実際の画像フォーマットはjpgでなくてもよい。アニメーションGIFと透過PNGで確認済）。<br />

# 既知の不具合

* 直したけど難しいもの（MTGATrackerの実装に依存するため）
  * トークン関連の実況をしない。
  * 初期ライフが20点でないフォーマットのゲーム開始時にライフが5点増えたかのように実況する。
  * いくつかのアクションを実況しない。
    * 起動型能力の起動
    * 誘発型能力の誘発（実況させる気もありません）
    * 占術
    * カードを手札に加える（ドローではなく）
    * カードの公開
    * 手札以外の領域からカードをプレイ（例：統率者、予顕）
    * 創出
    * 抽出
    * 呪文書のドラフト
    * トークンの死亡、生け贄、追放等
* 直したけど難しいもの（その他外部ツールの実装に依存するため）
  * ゆかりねっとコネクター Neoと連携してMTGカード連携プラグインでカード画像を表示する際に、誤った画像が表示される場合がある。
    * これは、ゆかりねっとコネクターNeoのMTGキャッシュフォルダ（マイ ドキュメント\YukarinetteConnector\MTGCache）内の同名画像ファイルを、正しい画像ファイルに差し替えることで回避できます。
    * ゆかりねっとコネクターNeo v1.83で多少改善されています。[参考](https://twitter.com/mikasa231/status/1489905231819608068)
  * ゆかりネットコネクターNeoに発話内容が連携されない
    * ゆかりねっとコネクターNeo v1.952以上で、ゆかりネットコネクターNeoに発話内容が連携されない事象が確認されています。
    * https://machanbazaar.com/ync-neo/ の最下部からダウンロードできる、ゆかりねっとコネクターNeo v1.947ならば発話内容が連携されることを確認済です。
  * ゆかりねっとコネクターNeoのOBS連携プラグインがOBSに接続できない
    * わかんない！
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
* カード名を英語で読み上げる。
  * 原因は不明ですが、MTGAの再インストールで解消したという例があります。[参考](https://twitter.com/poslog/status/1490080489696542720)
* たまにVOICEROIDが「記号ポーズ辞書」というエラーダイアログを表示して止まる。
  * VOICEROID＋ 東北きりたん EXでときどき発生することを確認しています。<br />[設定]メニュー > [日本語辞書設定] > [記号ポーズ辞書を使用する] のチェックを外すと解消する。かも。

## WAVファイル出力

* 出力したwavファイルにBGMやシステム通知音等が入ってしまう
  * AssistantSeikaの仕様です。
  * AssistantSeikaの [基本設定]タブ > [音声キャプチャ] > [音声保存時に再生デバイスをキャプチャする] のチェックを**外す**ことで回避できますが、[AssistantSeikaの公式サイト](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E9%9F%B3%E5%A3%B0%E3%82%AD%E3%83%A3%E3%83%97%E3%83%81%E3%83%A3_%E9%9F%B3%E5%A3%B0%E4%BF%9D%E5%AD%98)では非推奨とされています。
  * [音声保存時に再生デバイスをキャプチャする] のチェックを外してもWAVファイル出力できることは確認できています。<br />試したい方は、[AssistantSeikaの公式サイト](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E9%9F%B3%E5%A3%B0%E3%82%AD%E3%83%A3%E3%83%97%E3%83%81%E3%83%A3_%E9%9F%B3%E5%A3%B0%E4%BF%9D%E5%AD%98)とにらめっこしつつやってみてください。
* 出力したwavファイルが[AviUtl](http://spring-fragrance.mints.ne.jp/aviutl/)で使用できない
  * AssistantSeikaの [基本設定]タブ > [音声キャプチャ] > [16bitのwavファイルを使用] を選択することで使用できるようになるそうです。

## その他

* 自動実況を録音/配信できない
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

# 更新履歴

## version 1.0.0

* 公開

## version 1.0.1

* Loggerが機能していないので機能させる

## version 1.1.1

* speaker.jsonにピッチ調整パラメータのみのオブジェクトを追加して、speakオブジェクトの値として保持するように
* SeikaSey2.exeのオプションに対応
  * CeVIOのalpha値とかoverBannerとかはテストしてない。する気もない。
* 起動時にconfig.jsonをGUIで編集できるようにした
* 実況内容の追加
  * 墓地送り時のreason: (SBA_Deathtouch)の追加
  * 墓地送り時のreason: (Put)の追加

## version 1.2.0

* 設定画面からxxxx.jsonファイルを編集するウィンドウを表示できるようにした

## version 1.2.1

* カード名から<.*>を除去するようにした（アルケミー対応）

## version 1.3.0

* WAVファイル出力用batファイル作成機能追加

## version 1.4.0

* ゆかりねっとコネクター Neo連携機能追加
* mtgatracker_backend起動時に、CardDictionary.csvを出力するようにした

## version 1.4.1

* AssistantSeika未導入でもゆかりねっとコネクター Neo連携機能を使えるようにした

## version 1.4.2

* mtgatracker_backend起動時に、CardDictionary.csvにAppend.csvを追加するようにした

## version 1.4.3

* いつの間にかゲーム終了時に実況しなくなっていた不具合を修正した
* websocketのpingタイムアウトを無効化

## version 1.5.0

* トークンに関する実況をするようにしました
* 起動用バッチファイルを追加

## version 1.5.1

* CardDictionary.csvにトークン類の名前を出力しないように変更
  * ゆかりねっとコネクターNeoとの連携時に変なカード画像を引っ張ってこないようにする
* リンク集を追加

## version 1.6.0

* アルケミー：ニューカペナ実装後に動かなくなったのを修正
  * 一部のmtgaファイルがjsonからSQLiteに変わったことに対応

## version 1.6.1

* ヒストリックアンソロジー6とエクスプローラーアンソロジー1実装後に動かなくなったのを修正
  * 一部のmtgaファイルのキー名とデータ型が変わったことに対応

## version 1.6.2

* 団結のドミナリア実装あたりで動かなくなったのを修正
  * 一部のログフォーマットが変わったことに対応

## version 1.6.3

* なんか動かなくなったのを修正
  * カード情報のフォーマットがjsonからSQLiteに変わったことに対応

## version 1.6.4

* 兄弟戦争実装あたりで動かなくなったのを修正
  * MatchGameRoomStateChangedEventのeventIdが必須でなくなったことに対応

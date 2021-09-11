# mtgatracker_backend

## これは何？

[MTGATracker](https://mtgatracker.com/)のバックエンド部分を独自に改修したものです。<br />
commentary_backendと組み合わせて[MTG Arena](https://mtg-jp.com/mtgarena/)を自動実況するために使用します。<br />
導入方法、起動手順等はcommentary_backendのreadme.txtを参照してください。<br />

[MTG Arena](https://mtg-jp.com/mtgarena/)のインストールパスをレジストリに探しに行ったりするので、セキュリティ警告が表示される場合があります。<br />
停止するには、起動時に表示されるウィンドウの右上の×ボタンをクリックして閉じてください。<br />


# commentary_backend

## これは何？

mtgatracker_backend、[AssistantSeika](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/start)と組み合わせて[MTG Arena](https://mtg-jp.com/mtgarena/)を[VOICEROID](https://www.ah-soft.com/voiceroid/)等に実況させるためのツールです。

## 導入方法

1. [AssistantSeikaで利用できる音声合成製品](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E5%AF%BE%E5%BF%9C%E8%A3%BD%E5%93%81)を導入する
2. [AssistantSeika](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/start)を導入する
3. [mtgatracker_backend.zip](https://github.com/poslogithub/binary-dist/raw/main/mtgatracker_backend.zip)をダウンロードし、適当なフォルダに展開する
4. [commentary_backend.zip](https://github.com/poslogithub/binary-dist/raw/main/commentary_backend.zip)をダウンロードし、適当なフォルダに展開する
5. [AssistantSeika](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/start)に同梱されている[SeikaSay2.exe](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000)をcommentary_backend.exeと同じフォルダにコピーする

## 起動手順

1. [AssistantSeikaで利用できる音声合成製品](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E5%AF%BE%E5%BF%9C%E8%A3%BD%E5%93%81)を起動する
2. [AssistantSeika](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/start)を起動する
3. [AssistantSeikaの製品スキャンを実行](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95)し、話者一覧に実況させたい話者が表示されていることを確認する
4. [MTG Arena](https://mtg-jp.com/mtgarena/)を起動する
5. mtgatracker_backend.exeを実行する
6. commentary_backend.exeを実行する

commentary_backendの起動後、[MTG Arena](https://mtg-jp.com/mtgarena/)をプレイすると、勝手に実況してくれます。<br />
[Windows 10 の Xbox Game Bar](https://support.xbox.com/ja-JP/help/games-apps/game-setup-and-play/get-to-know-game-bar-on-windows-10)で実況付きで録画する場合、設定/キャプチャ中/録音するオーディオを「すべて」にする必要があります。<br />
その場合、通知音や音声通話等がすべて録音されるのでご注意ください。<br />

## 停止手順

mtgatracker_backend.exeを実行した際に表示されるウィンドウを、右上の×ボタンをクリックして閉じてください。<br />
mtgatracker_backendを停止すれば、commentary_backendは自動的に停止します。<br />

## より詳しい使い方

https://github.com/poslogithub/binary-dist/blob/main/commentary_backend_MANUAL.md を参照してください。<br />

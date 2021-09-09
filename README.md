# windows-binary-dist
 Windows用バイナリ配布用

## mtgatracker_backend

[MTGATracker](https://mtgatracker.com/)のバックエンド部分を独自に改修したものです。<br />
zipを展開して、mtgatracker_backend.exeを実行すると起動します。<br />
[MTG Arena](https://mtg-jp.com/mtgarena/)を起動してから起動してください。<br />
[MTG Arena](https://mtg-jp.com/mtgarena/)のインストールパスをレジストリに探しに行ったりするので、セキュリティ警告が表示される場合があります。<br />

## commentary_backend

mtgatracker_backend、[AssistantSeika](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/start)と組み合わせて[MTG Arena](https://mtg-jp.com/mtgarena/)を[VOICEROID](https://www.ah-soft.com/voiceroid/)等に実況させるためのツールです。<br />
zipを展開して、commentary_backend.exeを実行すると起動します。<br />
起動する前に、以下を実行してください。<br />

1. [AssistantSeikaで利用できる音声合成製品](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E5%AF%BE%E5%BF%9C%E8%A3%BD%E5%93%81)を起動する
2. [AssistantSeika](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/start)を起動する
3. [AssistantSeikaの製品スキャンを実行](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95)し、話者一覧に実況させたい話者が表示されていることを確認する
4. mtgatracker_backendを起動する

commentary_backendの起動後、[MTG Arena](https://mtg-jp.com/mtgarena/)をプレイすると、勝手に実況してくれます。<br />
[Windows 10 の Xbox Game Bar](https://support.xbox.com/ja-JP/help/games-apps/game-setup-and-play/get-to-know-game-bar-on-windows-10)で実況付きで録画する場合、設定/キャプチャ中/録音するオーディオを「すべて」にする必要があります。<br />
その場合、通知音や音声通話等がすべて録音されるのでご注意ください。<br />

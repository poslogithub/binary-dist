# mtg-card-gallery-file-downloader

## これは何？

Magic: the Gateringのカード画像をセットごとに一括ダウンロードするツールです。
具体的には、指定したCard Image Galleryのページから全てのカード画像を、指定したフォルダに「カード名.png」という名前で保存します。<br />
**『統率者マスターズ』以降の、フィルタ機能を備えたカードイメージギャラリーのみ対応しています。**<br />
『統率者マスターズ』以前のカードイメージギャラリーからカード画像をダウンロードしたい場合は、[mtg-card-gallery-file-downloader](https://github.com/poslogithub/binary-dist/tree/main/mtg-card-gallery-downloader)を使用してください。

## 用途は？

* 動画作成のためにカード画像をダウンロードしたいけど、1枚ずつダウンロードしてファイル名をカード名にするのが面倒だ、という場合に。
* [MTGA自動実況ツール](https://github.com/poslogithub/binary-dist/tree/main/mtga-commentary-automation)+[ゆかりねっとコネクターNeo](https://www.machanbazaar.com/ync-neo/)の[MTGカード支援プラグイン](https://www.machanbazaar.com/plugin_mtg/)でカード画像を表示するために、カード画像のキャッシュをあらかじめダウンロードしておきたい、という場合に。<br />
ゆかりねっとコネクターNeoのMTGカード支援プラグインのキャッシュフォルダ（通常、`マイ ドキュメント\YukarinetteConnector\MTGCache`）を指定すれば、ゆかりねっとコネクターNeoのMTGカード支援プラグインがキャッシュとして認識します。<br />

## 導入方法

* mtg-card-gallery-downloader.zipをダウンロードして、適当なフォルダに展開する。
  * https://github.com/poslogithub/binary-dist/raw/main/mtg-card-gallery-downloader-file/mtg-card-gallery-file-downloader.zip

## 実行方法（よく読んでね）

1. Webブラウザでカードイメージギャラリーを開く。※Chrome以外では動作確認していません。<br />
   注意：Card Image GalleryのURLには「`https://magic.wizards.com/`」で始まるものと、<br />
   　　　「`https://mtg-jp.com/`」で始まるものの2種類が存在します。<br />
   　　　本ツールは前者「`https://magic.wizards.com/`」で始まるCard Image Galleryのみ対応しています。<br />
2. ダウンロードしたい画像だけが表示されるように、適当にフィルターを指定する。<br />
   よくわからなかったら、ここは飛ばしても良いです。<br />
3. カードイメージギャラリーを一番下（利用規約とか行動規範とか書いてあるところ）までスクロールする。<br />
   この手順は飛ばしてはいけません。<br />
4. Ctrl+S を押し、カードイメージギャラリーを「Webページ、完全」形式で保存する。<br />
   保存先フォルダを覚えておきましょう。<br />
5. Webページのダウンロードが完了するまで待つ。<br />
5. downloader_file.exeを実行する。<br />
6. 「Card Image Gallery File」にダウンロードしたhtmlファイルのパスを指定する。<br />
7. 「保存先フォルダ」を指定する。<br />
8. 「実行」ボタンを押下する。<br />
　ダウンロード状況はプロンプト（黒背景のウィンドウ）に表示されます。<br />

## 配布場所

https://github.com/poslogithub/binary-dist/raw/main/mtg-card-gallery-downloader-file

## 連絡先

https://twitter.com/poslog

## ライセンス

MIT License

Copyright (c) 2023 poslogithub

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

## その他

* 分割カードは正しく保存できないかもしれません（カード名にファイル名に使用不可能な文字を含むため）。

## 改訂履歴

* 1.0.0
  * 公開
* 1.0.1
  * 一部環境で起動できない不具合を修正

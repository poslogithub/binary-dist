# mtg-card-gallery-downloader

## これは何？

[MTGA自動実況ツール](https://github.com/poslogithub/binary-dist/tree/main/mtga-commentary-automation)+[ゆかりねっとコネクターNeo](https://www.machanbazaar.com/ync-neo/)の[MTGカード支援プラグイン](https://www.machanbazaar.com/plugin_mtg/)でカード画像を表示するために、<br />
カード画像のキャッシュをあらかじめダウンロードするためのツールです。<br />
具体的には、指定したCard Image Galleryのページから全てのカード画像を、<br />
指定したフォルダに「カード名.jpg」という名前で保存します。<br />
ゆかりねっとコネクターNeoのMTGカード支援プラグインのキャッシュフォルダ<br />
（通常、`マイ ドキュメント\YukarinetteConnector\MTGCache`）を指定すれば、<br />
ゆかりねっとコネクターNeoのMTGカード支援プラグインがキャッシュとして認識します。<br />

## 実行方法

1. downloader.exeを実行する
2. 「Card Image Gallery URL」にカード画像をダウンロードしたいCard Image GalleryのURLの入力する。<br />
   注意：Card Image GalleryのURLには「`https://magic.wizards.com/`」で始まるものと、<br />
   　　　「`https://mtg-jp.com/`」で始まるものの2種類が存在します。<br />
   　　　本ツールは前者「`https://magic.wizards.com/`」で始まるCard Image Galleryのみ対応しています。<br />
3. 「保存先フォルダ」にゆかりねっとコネクターNeo(MTGカード支援プラグイン)のキャッシュフォルダを指定する。
4. 「実行」ボタンを押下する。<br />
　ダウンロード状況はプロンプト（黒背景のウィンドウ）に表示されます。<br />

## 配布場所

https://github.com/poslogithub/binary-dist/tree/main/mtg-card-gallery-downloader

## 連絡先

https://twitter.com/poslog

## ライセンス

MIT License

Copyright (c) 2022 poslogithub

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

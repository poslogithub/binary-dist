# sealed_generator

## これは何？

MTG Arena用シールドシミュレータです。以下の機能があります。<br />

* カードプールをインポート可能なデッキリストの形式で出力する。
* 構築したデッキが適正か否か（カードプール内のカードのみで構築されているか）を検証する。
* 日次、週次、月次で固定のカードプールを出力する。
* 剥くパックの個数を指定する。
* デッキリスト画像を出力する。

## 動作条件

* OSがWindowsであること。
* MTG Arenaがインストール済であること。

## 導入方法

* magic-league-generator.zipをダウンロードして、適当なフォルダに展開する。
  * https://github.com/poslogithub/binary-dist/raw/main/sealed_generator/sealed_generator.zip

## 起動方法

1. magic_league_generator.exeを実行する。

## 配布場所

https://github.com/poslogithub/binary-dist/raw/main/sealed_generator/

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

外部ライブラリのライセンスはLICENSEフォルダを参照してください。

## より詳しい使用方法

雰囲気で。

## 既知の問題

* メイス＋２をインポートできない
  * 謎。
  * MTGAでメイス＋２を含むデッキをエクスポート→インポートしても失敗するので、MTGAのバグと言ってよい。
* デッキリスト画像をエクスポートした時、一部のカード画像がダミーになる
  * 仕様。
  * 本ツールは[MTG Developers](https://magicthegathering.io/)で画像URL（通常[Gatherer](https://gatherer.wizards.com/Pages/Default.aspx)）を特定してダウンロードしている。<br />[MTG Developers](https://magicthegathering.io/)で画像URLを特定できない場合や、[Gatherer](https://gatherer.wizards.com/Pages/Default.aspx)に画像データが存在しない場合は、ダミーを出力するようにしている。<br />
  * ダミー出力される主なカードは以下。
    * デジタル専用カード
      * アルケミー専用カード
      * アリーナ基礎セット
      * アルケミーで調整されたカード
* デッキリスト画像をエクスポートした時、一部のカード画像が英語版になる
  * 仕様。
  * [MTG Developers](https://magicthegathering.io/)で日本語版カード画像URLを特定できない場合は、英語版カード画像を出力するようにしている。<br />
  * 英語版カード画像が出力される主なカードは以下。
    * カルドハイム以降の両面カード
    * イニストラード：真夜中の狩りの基本土地カード
      * 実際は日本語版カード画像URLを特定できないわけではなく、カード裏面画像になっているため英語版カード画像を出力している
* ドミナリアのカード画像が表示されない
  * MTGAと[MTG Developers](https://magicthegathering.io/)でセット名が異なるのが原因です。
    * MTGA: DAR
    * [MTG Developers](https://magicthegathering.io/): DOM
  * 印刷されているカードを見る限りDOMが正しいはずですが、[公式でもDARを使うことがあるらしい](https://mtg.fandom.com/wiki/Dominaria)です。あのさぁ...

## FAQ

### モードと基準日時の関係

| モード | 基準日時(UST) | 備考 |
| ---- | ---- | ---- |
| 日次 |毎日 08:00:00|日次勝利報酬更新日時|
| 週次 |日曜日 08:00:00|週間勝利報酬更新日時|
| 月次 |前月末日 20:00:00|ランクシーズン終了日時|
| ランダム |現在日時||
| 固定 |任意の日時|手動で設定|

### モードが月次の場合のパック数

| 週 | パック数 |
| ---- | ---- |
| 第1週 | 4|
| 第2週 | 6|
| 第3週 | 9|
| 第4週 | 12|

### パックの生成

* 内訳は以下の通り。
  * レア/神話レア 1枚
    * 神話レアの出現確率は、セットに依らず`1 / 7.4`
  * アンコモン 3枚
  * コモン 10枚
  * 土地 1枚
    * 土地が含まれていないセットでは出ない
    * コモン多色土地がコモンではなくこの枠に割り当てられているセットも存在する
      * あえてそうしているのではなく、MTGAの内部仕様としてそうなっている
    * 持っていないスタイルの基本土地（神河の浮世絵土地とか）が出る場合もある
* Masterpiece Seriesやゼンディカーの夜明けエクスペディション、ミスティカルアーカイブ等は出ない
* いわゆる[変則的な希少度](http://mtgwiki.com/wiki/%E5%A4%89%E5%89%87%E7%9A%84%E3%81%AA%E7%A8%80%E5%B0%91%E5%BA%A6)（ゼンディカーの夜明けで1パックに両面カードが必ず1枚入っているとか）は無視する。<br />同一のレアリティならば同一の確率で出る。
* 同一パックから同名のカードは1枚しか出ない

### デッキリストの検証

* カード名だけで検証しているので、異なるセットの同名カードでも検証は通る。
* 基本土地は検証しない。
  * 氷雪基本土地は検証する。
  * 荒地は検証する...MTGAで荒地は未実装だけど。
  * 日本語と英語しか対応していません。

### 略号とセット名の対応

SNCリリース直前確認。

| 略号 | セット名 |
| ---- | ---- |
| AFR |フォーゴトン・レルム探訪|
| AKR |アモンケットリマスター|
| ANB |アリーナ基礎セット|
| DAR |ドミナリア|
| ELD |エルドレインの王権|
| GRN |ラヴニカのギルド|
| IKO |イコリア：巨獣の棲処|
| J21 |Jumpstart: Historic Horizons|
| JMP |Jumpstart|
| KHM |カルドハイム|
| KLR |カラデシュリマスター|
| M19 |基本セット2019|
| M20 |基本セット2020|
| M21 |基本セット2021|
| MH1 |モダンホライゾン|
| MH2 |モダンホライゾン2|
| MID |イニストラード：真夜中の狩り|
| NEO |神河：輝ける世界|
| RIX |イクサランの相克|
| RNA |ラヴニカの献身|
| SNC |ニューカペナの街角|
| STX |ストリクスヘイヴン：魔法学院|
| THB |テーロス還魂記|
| VOW |イニストラード：真紅の契り|
| WAR |灯争大戦|
| XLN |イクサラン|
| ZNR |ゼンディカーの夜明け|

### リストに出てこないセットがある

レア1枚以上、アンコモン3枚以上、コモン10枚以上を含まないセットはリストに出さないようになっています。<br />
具体的には、コモンが存在しない「ミスティカルアーカイブ」「アルケミー：イニストラード」「アルケミー：神河」や、コモンが10枚未満である「ヒストリック・アンソロジー」は出てきません。<br />

## 更新履歴

### version 1.0.0

* 公開

### version 1.1.0

* セットを3つまで指定できるようにした。<br />複数セットを指定する場合、パック数は手動にすること。<br />
* 分割カードの検証ができない問題を修正した。

### version 1.2.0

* デッキリストにプールに無いカードが含まれている場合、不正カードを除外したデッキリストをエクスポートできるようにした。
* デッキリストに無いカードがプールに含まれている場合、不足カードをサイドボードに追加したデッキリストをエクスポートできるようにした。

### version 1.3.0

* デッキリスト画像をエクスポートできるようにした。

### version 1.3.1

* デッキリスト画像用のカード画像ダウンロードを並列化して速くした。

### version 1.3.2

* アルケミー調整カード（エクスポート時のカード名が「A-」で始まるカード）の画像が表示されない不具合を修正<br />（画像が表示されるとは言っていない）

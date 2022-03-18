# sealed_generator

## これは何？

MTG Arena用シールドシミュレータです。以下の機能があります。<br />

* カードプールをインポート可能なデッキリストの形式で出力する。
* 構築したデッキが適正か否か（カードプール内のカードのみで構築されているか）を検証する。
* 日次、週次、月次で固定のカードプールを出力する。
* 剥くパックの個数を指定する。

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

## 既知の不具合

* メイス＋２をインポートできない
  * 謎。<br />MTGAでメイス＋２を含むデッキをエクスポート→インポートしても失敗するので、MTGAのバグと言ってよい。<br />
* 分割カードが検証で引っかかる
  * Version 1.1.0で修正済。

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

* 神話レアの出現確率は、セットに依らず`1 / 7.4`
* Masterpiece Seriesやゼンディカーの夜明けエクスペディション、ミスティカルアーカイブ等は出ない
* 両面カードが最低でも1枚出るとか、土地が最低でも1枚出るとかは無視
* 同一パックから同名のカードは1枚しか出ない

### 略号とセット名の対応

NEOリリース直後確認。

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
| STX |ストリクスヘイヴン：魔法学院|
| THB |テーロス還魂記|
| VOW |イニストラード：真紅の契り|
| WAR |灯争大戦|
| XLN |イクサラン|
| ZNR |ゼンディカーの夜明け|

### リストに出てこないセットがある

レア1枚以上、アンコモン3枚以上、コモン10枚以上を含まないセットはリストに出さないようになっています。<br />
具体的には、コモンが存在しない「アルケミー：イニストラード」「アルケミー：神河」等は出てきません。<br />

## 更新履歴

### version 1.0.0

* 公開

### version 1.1.0

* セットを3つまで指定できるようにした。<br />複数セットを指定する場合、パック数は手動にすること。<br />
* 分割カードの検証ができない問題を修正した。

### version 1.2.0

* デッキリストにプールに無いカードが含まれている場合、不正カードを除外したデッキリストをエクスポートできるようにした。
* デッキリストに無いカードがプールに含まれている場合、不足カードをサイドボードに追加したデッキリストをエクスポートできるようにした。

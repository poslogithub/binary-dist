# これは何？

[変愚蛮怒](https://hengband.github.io/)をVOICEROID等に実況してもらうためのツールです。<br />
といいつつ、派生版（TObandとか幻想蛮怒とか）でも使えるんじゃないかな...試してないけど。<br />

# 動作条件

* OSがWindowsであること。
* AssistantSeikaがインストール済であること。
  * https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-001a
* AssistantSeikaに同梱されているSeikaSay2.exeファイルが下記パスにコピー済であること。
  * C:\Program Files\510Product\SeikaSay2\SeikaSay2.exe
  * SeikaSay2フォルダは存在しないので作成してください。
* AssistantSeikaが対応している音声合成製品がインストール済であること。
  * https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E5%AF%BE%E5%BF%9C%E8%A3%BD%E5%93%81
  * [VOICEVOX](https://voicevox.hiroshiba.jp/)は無償なので、お試しするのにおすすめです。

# 導入方法

* hengband-with-voice.zipをダウンロードして、適当なフォルダに展開する。
  * https://github.com/poslogithub/binary-dist/raw/main/hengband-with-voice/hengband-with-voice.zip

# 起動方法

1. 変愚蛮怒を起動する。
2. 変愚蛮怒で新規ゲームを始めるなりセーブデータを開くなりする。
3. AssistantSeikaと音声合成製品を起動する。
4. AssistantSeikaの製品スキャンを実行する。
5. hengband-with-voice.exeを実行する。

# FAQ

* ウィンドウ上部で白い帯がピコピコしている
  * 仕様です。逆に、白い帯がピコピコしていない場合は実況されません。
  * 
* 何も喋らない
  * config.iniにAssistantSeikaの話者一覧に表示されているcidが書いてあります。デフォルトでは50022（ずんだもん（ノーマル））になっています。<br />別のキャラクターに喋らせたい場合は、config.iniのcidの値を書き換えて、保存してからhengband-with-voice.exeを実行してください。
  * 

# 配布場所

* バイナリ
  * https://github.com/poslogithub/binary-dist/tree/main/mtga-commentary-automation
* ソース
  * https://github.com/poslogithub/mtgatracker
  * https://github.com/poslogithub/mtga-commentary-automation

## 連絡先

https://twitter.com/poslog

# ライセンス

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

# 更新履歴

## version 1.0.0

* 公開

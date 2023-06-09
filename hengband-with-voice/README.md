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

* 起動しない
  * 起動方法の通りに起動したか確認してください。<br />hengband-with-voiceは、変愚蛮怒が起動していないと勝手に終了します。
* マウスカーソルが勝手に動く
  * 仕様です。変愚蛮怒がアクティブウィンドウでなくなれば動かなくなるので、Alt+Tabでウィンドウ切り替えしてください。
* ウィンドウ上部で白い帯がピコピコしている
  * 仕様です。目障りかもしれませんが、そのうち慣れます。
* 何も喋らない
  * 白い帯がピコピコしている場合
    * AssistantSeikaと音声合成製品が起動していること、Assistanteikaの製品スキャンが実行済であること（話者一覧が空でないこと）を確認してください。
    * config.iniにAssistantSeikaの話者一覧に表示されているcidが書いてあります。デフォルトでは50022（ずんだもん（ノーマル））になっています。<br />別のキャラクターに喋らせたい場合は、config.iniのcidの値を書き換えて、保存してからhengband-with-voice.exeを実行してください。
    * config.iniに書いてあるSeikaSay2のパスにSeikaSay2.exeが配置されていることを確認してください。
    * 白い帯がピコピコしている位置が変愚蛮怒はメインウィンドウの最上行の左端から右端でない場合
      * 後述の「白い帯がピコピコしていない場合」を参照してください。
  * 白い帯がピコピコしていない場合/白い帯がピコピコしている位置が変愚蛮怒はメインウィンドウの最上行の左端から右端でない場合
    * 後述の「仕組み」に書いてある通り、hengband-with-voiceはメインウィンドウの最上行を自動的にドラッグしようとします。<br />「メインウィンドウの最上行」の座標は、ウィンドウ左上端からの相対位置と、ウィンドウ右上端からの相対位置を使って取得しています。<br />この「相対位置」がconfig.iniのMouseClickDrag～です。<br />デフォルトの相対位置は作者の環境（Windows 11 Homeの初期設定）で決め打っているので、環境次第ではメインウィンドウの最上行の座標を正しく取得できていない可能性があります。<br />この場合は、環境に合わせてconfig.iniのMouseClickDrag～を変更する必要があります。<br />ウィンドウの左上端と右上端ですが、見た目通りの端ではなく、半透明の部分＝影も含めた範囲の端になります。なので、メインウィンドウのプリントスクリーンを取得してピクセル数を数えてもうまくいきません。<br />Au3Infoを使えば影も含めたウィンドウサイズを取得できるので、プリントスクリーンのサイズとの差でピクセル数を数えることができますが（実際に作者はそうやって決め打ちました）、何を言っているのかさっぱりわからんと思うので、適当な値を指定してトライアンドエラーしたほうが早いと思います。<br />


# 仕組み

変愚蛮怒には、メインウィンドウをドラッグすると、選択した範囲の文字列をクリップボードにコピーするという仕様があります(※1)。<br />
そこで、[AutoIt](https://www.autoitscript.com/site/)を使って1秒ごとに変愚蛮怒はメインウィンドウの最上行を自動的にドラッグして、<br />
クリップボードにコピーされた内容が実況すべき内容ならば(※2)、AssistantSeika経由で音声合成製品にしゃべらせます(※3)。<br />
※1: サブウィンドウ1にはこの仕様はありません。ちくしょうめ。<br />
※2: 「。」か「！」か「-続く-」で終わる文字列は実況すべき内容と判断しています。詳細が知りたい方はソースを読んでください。<br />
※3: このへんの仕組みは[AssistantSeika の説明 ［努力したWiki］](https://wiki.hgotoh.jp/documents/tools/assistantseika/assistantseika-000)を参照してください。<br />

# 配布場所

* バイナリ
  * https://github.com/poslogithub/binary-dist/edit/main/hengband-with-voice/
* ソース
  * https://github.com/poslogithub/hengband-with-voice

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

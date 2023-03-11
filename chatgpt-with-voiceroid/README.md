# これは何？

[ChatGPT](https://openai.com/blog/chatgpt/)の回答をVOICEROID等に読み上げてもらうツールです。<br />
サンプル：https://twitter.com/poslog/status/1628533596846952448<br />

# 動作条件

* OSがWindowsであること。
* ChatGPTのアカウントを持っていること。
* AssistantSeikaがインストール済であること。
  * https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-001a
* AssistantSeikaが対応している音声合成製品がインストール済であること。
  * https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-000#%E5%AF%BE%E5%BF%9C%E8%A3%BD%E5%93%81

# 導入方法

* chatgpt-with-voiceroid.zipをダウンロードして、適当なフォルダに展開する。
  * https://github.com/poslogithub/binary-dist/raw/main/chatgpt-with-voiceroid/chatgpt-with-voiceroid.zip
* chatgpt-with-voiceroidフォルダ（chatgpt-with-voiceroid.exeファイルが存在するフォルダ）に、AssistantSeikaに同梱されているSeikaSay2.exeファイルをコピーする。

# 起動方法

1. 音声合成製品を起動する。
2. AssistantSeikaを起動する。
3. AssistantSeikaの製品スキャンを実行する。
4. chatgpt-with-voiceroid.exeを実行する。
5. chat.openai.comを使う (無料)場合: 
  * 設定ウィンドウのAccess tokenに、[ChatGPTのセッション情報](https://chat.openai.com/api/auth/session)の`accessToken`の値を入力する。<br />セッション情報は「開く」ボタンをクリックすることでも表示される。
6. 公式APIを使う (有料)場合:
  * 設定ウィンドウのAPI Keyに、[API Key](https://platform.openai.com/account/api-keys)の`accessToken`の値を入力する。<br />API Keyは「開く」ボタンをクリックすることでも表示される。
7. 設定ウィンドウの話者から読み上げさせたい話者を選択する。
8. 「開始」ボタンをクリックする。

# 配布場所

* バイナリ
  * https://github.com/poslogithub/binary-dist/tree/main/mtga-commentary-automation
* ソース
  * https://github.com/poslogithub/chatgpt-with-voiceroid

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

外部ライブラリのライセンスはLICENSEフォルダを参照してください。

# 今後の展望

1. キュー管理をちゃんとする
2. 質問を音声認識で入力できるようにする
3. 公式APIをrevChatGPTを介さずに利用する
4. 質問もVOICEROID等に読み上げてもらえるようにする

# 更新履歴

## version 1.0.0

* 公開
* 発話開始までの時間が短縮された
* 発話中に発話内容が表示されるようになった
* SeikaSay2.exeの場所が保存されない不具合を解消した

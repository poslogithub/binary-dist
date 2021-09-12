作成中です！ すみません何でもはしません！

* commentary_backend\config\config.jsonのspeakDuoをfalseにすると一人で自分と対戦相手の両方のアクションを実況するようになる
* 話者はAssistantSeikaの話者一覧の先頭から持ってくる
  * commentary_backend\config\config.jsonにheroCidとopponentCidを追加すると話者を指定できる
    * 追加の仕方は察してください
* commentary_backend\config\defaultSpeaker.jsonをいじると実況内容を変えられる
  * いじりかたは察してください
* defaultSpeaker.jsonをコピーしてxxxx.json（xxxxは[AssistantSeikaの話者一覧で確認できるcid](https://hgotoh.jp/wiki/doku.php/documents/voiceroid/assistantseika/assistantseika-004)。例えば1707.jsonなら東北きりたん）を作成すると、話者毎に実況内容を変えられる

---
title: "[Chatbot] 使用Messaging API(C# SDK)建立LINE Bot WebAPI(二)"
---

## 前情提要
在[上一篇]({{ site.url }}/chatbot-create-line-bot-using-messageing-api-1/)建立LINE Bot串接Messaging API，使用到[LineMessagingApi](https://github.com/pierre3/LineMessagingApi)，大略過了一次官方Messaging API，這套SDK已對應了大部分的功能(我無法一一比對，搞不好根本完全同步了:feelsgood:)。
鱿申請[LINE developer](https://developers.line.me)帳號、建立Visual Studio Templates Project，將Web發布後，就可以和自建的LINE Bot對話了。

## LineBotApp
透過LINEBot WebAPI，和我們所建立的LINE Bot進行訊息的串接，而事件以及邏輯運算，都寫在Root下的 LineBotApp.cs中，作者已經做過初始化，並且將訊息進行分類，以範例的方式呈現。

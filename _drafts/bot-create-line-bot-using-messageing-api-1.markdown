---
title: "[BOT] 使用Messaging API(C# SDK)建立LINE Bot WebAPI(一)"
date: "2018-05-17 04:21"
---

### 緣起
Chatbot為近年最為火紅的應用服務，越多人使用的平台，越能有開發多元化層面的效果；Facebook、Skype均有提供Chatbot的開發介面，而且Microsoft Azure也提供了Bot Services提供跨平台應用，但在東亞、東南亞使用者眾的LINE平台並沒有整合進來，需要單獨做串接。

:beginner: LINE提供開發者打造LINE Chatbot已有一段時間，去年OT API改名為LINE Messaging API以符合應用情境，畢竟建立Bot核心在於開發端。

🚀LINE Messaging API使用RESTful的通訊格式，雖然知道，使用原生的API最為安全可靠，但是最後還是被 😩**懶惰** 擊垮，開始了尋覓SDK的生涯；[LINE官方提供的SDK](https://developers.line.me/en/docs/messaging-api/line-bot-sdk/)，有```Java```、```PHP```、等，但沒有提供```C#```(沒關係，已經習慣了)，但還是有社群善心人事提供了C#版本。

> 官網推薦了兩個社群開發的C# SDK，也有台灣人自己提供的版本，當然沒辦法馬上比較出優劣，只能用Github上的更新日期以及提供的Template來決定了。
> 我這邊是使用[pierre3/LineMessagingApi ](https://github.com/pierre3/LineMessagingApi)這個版本的SDK，若想要使用SDK更深入了解學習，我特別推薦[.NET Walker所撰寫的LineBot系列](http://studyhost.blogspot.tw/2016/05/linebot-1-clinebot.html)

### 目標
建立的LINE Chatbot可以加入好友，並且進行初步訊息的溝通；分為幾個步驟，以下圖(取自於[LINE Developer](https://developers.line.me/en/docs/messaging-api/overview/))來說，第一步先要在Messaging API建立帳號、設定一個LINE Channel，然後建立一個WebAPI(```YOUR SYSTEM```)上面建立Webhook的應用程式。  

![bot-create-line-bot-using-messageing-api-01](/images/2018/05/bot-create-line-bot-using-messageing-api-01.png)

#### LINE Messaging API
首先要先申請帳號加入LINE Developer，以此帳號登入Console後，要建立一個Provider，請參考[LINE Developer 官方說明](https://developers.line.me/en/docs/messaging-api/overview/)，中文則推薦[.NET Walker的Line Bot申請流程](http://studyhost.blogspot.tw/2016/05/linebot-1-clinebot.html)  

![bot-create-line-bot-using-messageing-api-02](/images/2018/05/bot-create-line-bot-using-messageing-api-02.png)

#### 使用LineMessagingApi SDK範本建立WebAPI
我們現在要來做圖示的**YOUR SYSTEM**這一段  

![bot-create-line-bot-using-messageing-api-03](/images/2018/05/bot-create-line-bot-using-messageing-api-03.png)。
1. 請先下載安裝[LINE Bot C# Template](https://marketplace.visualstudio.com/items?itemName=pierre3.LINEBotCSharpTemplate)；這位日本好手已經是雲端能者，範本已經結合Azure Storage Account，也提供了Azure Function的範本。
2. 建立LINEBotApplication WebAPI  
  - 在Visual Studio，建立新專案，找到Cloud分類，往下拉就可以看到三個LINE Bot的範本，選擇LINEBotApplication。  
  ![bot-create-line-bot-using-messageing-api-04](/images/2018/05/bot-create-line-bot-using-messageing-api-04.png)
  - 這是一個WebAPI的專案結構  
   ![bot-create-line-bot-using-messageing-api-05](/images/2018/05/bot-create-line-bot-using-messageing-api-05.png)
  - Controllers資料夾中的LINEBotController就是要註冊我們在LINE Developers Console中Channel Settins Webhook。
  - CloudStorage資料夾中定義存取Media資源以及事件的紀錄。
  - Root下的LineBotApp.cs，就是我們撰寫傳接LINE Messaging API的位置，
3. Web.config設定  
以下由相關網站取得資料填入  

```HTML
<appSettings>
  <add key="ChannelSecret" value="由LINE Console取得(Channel secret)" />
  <add key="ChannelAccessToken" value="由LINE Console取得(Channel accesss token)" />
  <add key="StorageConnectionString" value="由Azure Storage Account取得連接字串" />
</appSettings>
```
4. 建立WebAPI網站
  - 最快的方式是將網站發布到Azure Web App。
  - 在LINE Developer Console啟用Webhooks，並將Azure Web App的WebAPI位置設定在Webhook URL，SSL是必須的，Azure Web App好處是預設啟用方便開發人員進行部署，只要將URL改為https即可(不建議產品類型)!  
  [bot-create-line-bot-using-messageing-api-06](images/2018/05/bot-create-line-bot-using-messageing-api-06.png)

完成了，只要將LINE Bot加入好友，就可以對話了~~ ，這個Template做得太貼心了💥。

#### 測試
![bot-create-line-bot-using-messageing-api-07](/images/2018/05/bot-create-line-bot-using-messageing-api-07.png)
1. 掃描LINE Developers Console中Channel所提供的QR code，加入有後，開始傳遞訊息。
2. 加入好友會有初始訊息，可以在LINE Developers Console中設定
  - Auto-reply messages.
  - Greeting messages
3. 傳遞文字，LINE Bot會回您相同的文字，傳遞貼圖，LINE Bot回傳您隨機抽樣的貼圖，傳遞Media，LINE Bot回傳您儲存在Azure Blob的位置。

Done:metal:

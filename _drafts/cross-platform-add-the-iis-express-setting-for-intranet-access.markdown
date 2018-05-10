---
title: "[Cross Platform] 設定IISExpress將網站分享至內部網路存取"
categories: IISExpress
---

### 緣起
開發跨平台專案，時常需要同時了解Server與Client互動的關係與結果，過去，Server端一定要完成API的設計與開發，Client端才能依據文件與端口進行開發與測試，在Visaul Studio的跨平台方案，將Server與Client放在一起，本篇將介紹如何在內網的手機App存取內網的Server，以便快速除錯平衡兩邊的開發。

### 目標
時常會需要Server端與Client端同時執行方便除錯與預覽，在Visual Studio開發時，預設會使用IIS Express提供虛擬網站進行執行時期的偵錯，設定環境讓Client端包含手機存取IISExpress。

### 不適用
本章內容以內網固定IP的方式進行設定，當設定進行版控時，另一位開發者的電腦將不適用此設定，會造成專案無法載入的問題。

#### 網路環境設置
* 取得IISExpress執行時期的Port，在防火牆開啟規則讓遠端的Client可以通過
  - 開啟Visual Studio 網站專案屬性頁，在Web的頁籤中，找到Project Url，這邊有預設的Port號。
   ![cross-platform-add-the-iis-express-setting-for-intranet-access-02](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-02.png)
  - 開啟防火牆設定，選取進階設定，在**輸入規則**新增規則設定本機連接埠。
    ![cross-platform-add-the-iis-express-setting-for-intranet-access-03](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-03.png)
* 開啟可供存取的固定IP位址
  - 取得本機聯網的IPv4位址
```bash
  ipconfig
```
![cross-platform-add-the-iis-express-setting-for-intranet-access-01](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-01.png)

  原始網站預設的位址為```localhost```，要改為固定IP，要先改applicationhost的設定，否則直接在專案改會出錯，無法更動。
  - 開啟```applicationhost.config```有兩種方式，一種是執行網站後，由IISExpress的快速啟動列開啟，另一種是直接在方案下找到.vs -> config開啟後進行編輯。
  - 找到網站設定的```tag```，因為有可能這個專案被重複建立了幾次，因此會有id作為辨認，可以直接使用Port來找到正確的設定位置。
  - 將```localhost```，改為IP位址後存檔
    ![cross-platform-add-the-iis-express-setting-for-intranet-access-04](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-04.png)
* 此時將網站屬性的Project Url由localhost改為固定IP即可

### 測試
由手機端App的網頁開啟本機的IISExpress固定IP網站，理論上只要Client端的瀏覽器可以存取網站，開發的App或網頁，都可以存取網站的WebAPI。
#### 執行ASP.NET專案
* 很酷的，現在增強了Chrome做Debug瀏覽器的功能
![cross-platform-add-the-iis-express-setting-for-intranet-access-05](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-05.png)
* 執行出固定IP與Port的網站(馬賽克搞得像國王的新衣嗎?哈，還是要保持資訊安全的習慣😄)
  ![cross-platform-add-the-iis-express-setting-for-intranet-access-06](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-06.png)
#### [macOS Safari]
![cross-platform-add-the-iis-express-setting-for-intranet-access-07](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-07.png)
#### [iPhone Safari]
![cross-platform-add-the-iis-express-setting-for-intranet-access-08](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-08.png)
#### [Android Google Chrome]
![cross-platform-add-the-iis-express-setting-for-intranet-access-09](/images/2018/05/cross-platform-add-the-iis-express-setting-for-intranet-access-09.png)

Done!:metal:

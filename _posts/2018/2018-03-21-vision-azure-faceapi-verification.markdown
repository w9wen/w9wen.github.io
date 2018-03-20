---
title: '[Vision] Azure Face API 臉部驗證 (一) 架構與設定'
date: '2018-03-21 06:23'
---

目前(2018-03-21)雲端的人臉比對驗證，Azure以及AWS的[Amazon Rekognition](https://aws.amazon.com/rekognition/)均有提供，本篇介紹Azure的人臉比對實作。

### Microsoft Face API
微軟的Face API服務在Azure屬於AI + Cognitive Services的分類![AI + Cognitive Services](/images/2018/03/ai-cognitive-services.png)
分為以下的功能使用
* Face Verification 臉部驗證
* Face Recognition 臉部偵測
* Finding Similar Face 人臉搜尋
* Face Grouping
* Face Identificaion

### Face Verification
開始臉部驗證體驗的旅程，enjoy😅
#### 在Azure Portal建立
1. 建立新的Resources，選擇 AI + Cognitive Services中的Face API(如上圖)
2. 給予特定的名稱，在選擇Location，我會盡量和其他相關的Resources選擇同一地區，或是靠近，因為聽說會有跨地域效能的問題，選擇同一個地域，效能會快一點。
3. 因為只是試用，價錢選擇免費的。
![Create Face API resource](/images/2018/03/create-face-api-resource.png)

建立完成，存取使用最重要的就是這個API的連結和Keys

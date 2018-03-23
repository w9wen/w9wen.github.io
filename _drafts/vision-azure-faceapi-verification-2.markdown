---
title: "[Vision] Azure Face API 臉部驗證 (二) RESTful API Reference"
date: "2018-03-21 06:24"
---

本篇開始介紹如何使用Microsoft Face API，參照[Face API](https://azure.microsoft.com/en-us/services/cognitive-services/face/?v=18.09)可以知道有哪些功能可以使用。

### API Reference
當然為了開發者方便，微軟對於自家產品，支援了各平台的SDK，[Face API Documentation](https://docs.microsoft.com/en-us/azure/cognitive-services/face/)
![Face API Documentation](/images/2018/03/face-api-documentation.png)
但由於去年再拿起半年沒用的GCP SDK套件，以及Azure的ProjectOxford SDK套件，結果不是過時了，就是有新的SDK，由那時起，就統一採用RESTful API存取，至少大部分服務都提供這樣的通訊格式，短時間不會再背叛我。😢

#### 使用 Face Verify 流程
要使用Face Verify，需要先取得這張圖片辨識結果的Face ID。
1. 先使用[Face Detect API](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236)進行臉部辨識，成功會回傳年紀、表情、性別等欄位，但在這邊我們只要留著Face ID備用。
2. 將要比對的相片也做一次Face Detect後保留Face ID。
3. 接著就可以用這以上兩個Face ID串到[Face Verify API](https://eastasia.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039523a)。
4. 要注意上傳的圖片檔案不能超過4MB，檔案也於24小時後銷毀，也就是說，辨識過的Face ID在24小時內可重複Request，24小時後就會失效。

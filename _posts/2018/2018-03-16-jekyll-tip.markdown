---
title: Jekyll Tip
date: '2018-03-16 01:50'
---

我的部落格是由jekyll建置，使用了theme:Minimal Mistakes，內容如下

### Jekyll
[Jekyll](https://jekyllrb.com)是一套靜態網頁編輯器，有以下的特點
* 文件可以使用Markdown語法撰寫，每篇文章都是一個Markdown檔案。
* 純靜態網頁，完全不使用資料庫，因此效能非常好。
  - 我這樣算，一天一篇文章，一年不過365篇，也只是一個365個文檔的網站(人生能有幾個365天❓)。
* 可以自己編寫網站的HTML、CSS來設計自己的風格，不過我實在很懶，寧願花兩、三個月的時間找Template，也不想自己設計😄；找到自己屬意的範本後，可以在HTML與CSS進行微調。
* 適合程式技術人員使用開發工具一顆熱血的心❤️(這邊就要貼個圖展示一下，不是蓋的，寫文章就像寫程式，左邊有專案結構，文章就在中間撰寫，右邊有預覽，下方的窗格可以使用命令列，在狀態列也可以看到GitHub的命令操作，是不是很變態~~)。
![Jekyll Tip 1](/assets/images/posts/jekyll-tip1.png)
* GitHub官方完全支援，具有兩種模式(用我自己的方式敘述)
  1. 帳戶的部落格形式，用master的branch就可以在GitHub上自動編譯，編譯有問題還會回報到你的信箱。
  2. 專案的部落格，要建立gh-pages的branch來commit自己的jekyll網站。
* 有超多超讓你暈眩的Template，但如第一篇文章所述，要先設定好自己部落格想要的形式，再來找適合的Template。

Jekyll是由Ruby語言撰寫，所以要使用Jekyll，就要安裝Ruby、Gem、Bundle(請不要問我這些是什麼，我只是為了Jekyll、所以安裝~~我不是在唱歌)

#### Ruby

##### macOS

##### Windows
>ruby 2.5.0p0 (2017-12-25 revision 61468) [x64-mingw32]

Ruby官方並不支援Windows，所以要另外使用[RubyInstaller](https://rubyinstaller.org/)來安裝，現在已經不需要再另外安裝DevKit，比以前簡單多了。

#### Jekyll
有了Ruby，你只要`jekyll new myBlog`，就建立起了我的部落格了。
#### Minimal Mistakes Jekyll Theme
這是我一直提到、我找到最滿意最滿意的Template，提供了以下的服務
##### 積極的更新
##### Skin的選項
##### 搜尋服務的選項
##### 留言管理的選項
##### 社群分享的選項
##### 分析服務的選項

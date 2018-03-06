---
title: My blog created using Jekyll
categories:
  - jekyll
---

想要為自己留下一些足跡，建立自己部落格的心願已經很久了；有許多非常流行的部落格，提供技術人員紀錄開發日誌，如[DotBlog](https://dotblogs.com.tw/)、[隨意窩](http://blog.xuite.net/)。

不過，每個部落格都有自己的編輯器、自己的範本套用以及特殊的文字表現方式，一方面覺得好像和技術人員所學不太相符(我連寫文章也想要`git commit -m "新的文章出爐囉。"`)，一方面其實也是懶得學習進取😵。

## 開發人員平台
開發人員非常需要網路資源，有了技術上的問題，大多會求助[Google](https://google.com)大神，而其實這些搜尋大多導到[CodeProject](https://www.codeproject.com)、[Stack Overflow](https://stackoverflow.com)這些開發平台，而我也一一建立了帳號，曾有雄心壯志寫些技術性的文章，但懶得學編輯器的個性依舊，當然也是失敗收場😞。

## GitHub
多年之後，開源程式碼流行了起來，各式開源網站蔚為風潮，其中[GitHub](https://github.com)的崛起，等同新創代名詞之後，開發技術的查詢，有很大一部份都轉移到這個開發者平台，當時的我，連git是什麼，都還不知道。

## 程式碼版控
我在[裕隆電能](https://www.yulon-energy.com/tw/evOfficial/)期間，是學習Web以及Windows Forms以外技術的開始，當時的是一人技術團隊，自以為好大的Team，自己架了[VisualSVN](https://www.visualsvn.com)的Server，自己建帳號、自己管理自己，一堆log message清一色是William😄。

#### 開始我的git人生
在懵懵懂懂之中，進入了[緯創資通](https://wistron.com)，所屬部門早已使用git進行版本控管，git和svn觀念完全不同，卻使用相同的comment，沒學過卻直接上戰場，當然處處是地雷💥；於是下定決心要把git練起來，[30 天精通 Git 版本控管-Will保哥](https://github.com/doggy8088/Learn-Git-in-30-days)，就成為入門關鍵，為了專案快馬加鞭將練習走一次，縮短為10日完成，那個`git push`的日子還好過下去了。

## 靜態部落格編輯器

#### **離題了嗎**
其實並沒有，寫文章的雄心壯志仍在我心💙，當知道了git，一堆技術部落格(尤其是專案程式部落格)都用了一種特殊簡潔的語法[Markdown](https://en.wikipedia.org/wiki/Markdown)
* _git_ - 版本控管。
* _Markdown_ - 統一簡潔的文章編輯語法。
這都是我要的，事情就結束了嗎?並沒有，尋尋覓覓又一堆技術與我相見歡

#### MDwiki
這是我第一個找的和我需求相符合的套件，可以用Markdown撰寫技術文章，可做出很酷的文件網頁，又可自訂網站色彩，但是新的文章上板有點麻煩，重點是此套件更新速度很慢，當時我還以為已經掛點了，因此就放棄了。
> 最近發現此作者又活過來了，有興趣的可以試試喔[MDwiki](http://dynalon.github.io/mdwiki/#!index.md)，但也已經是一個月前的事，一個人的力量總是薄弱的，更新慢是正常的

#### Jekyll
>這篇文章的重點🌋，文章也快要尾聲了

當然還有一堆靜態網頁編輯器，但[Jekyll](https://jekyllrb.com/)算是第一名👍，而且研究後發現，天啊，怎麼有這種超強部落格產生器。
1. 只要輸入`jekyll new myBlog`，就產生了您的第一個網站。
2. 可以制定自己的Theme，官方提供了相當豐富的[Jekyll Template](https://jekyllrb.com/docs/templates/)，您也可以上網搜尋，真不知道為什麼這麼多人有時間做這些範本。
3. GitHub官方完全支援，請參考[GitHub Pages using Jekyll](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/)，我的部落格就是架在上面。
4. 全靜態網頁，完全不使用資料庫。
5. 第三方套件，如[Disqus](https://disqus.com)您就可以在文章下面留言給我喔、[Algolia](https://www.algolia.com/)等，而且設定相當方便。
6. 資料夾有分_posts、drafts、pages_等，也就是說，您可以撰寫部落格的文章，也可以寫草稿，也可以設計頁面，並且使用程式碼編輯器撰寫並維護文章。
7. 應該還有，日後讓我慢慢到來

>以上是我敘述的好處，但困難與痛點卻也遍地開花:sunflower:

使用Jekyll的好處之前，要先經歷一翻磨難😱
1. 先裝個[Ruby](https://www.ruby-lang.org/en/)吧。
  * macOS：作業系統已有預帶，但系統會升級，Ruby當然也要升級，我是用Homebrew，可是升級步驟現在在我腦袋是一片空白😫，這是建立部落格紀錄的好處~~。
  * Windows：不知道微軟得罪多少人，Ruby官方並不支援；要由[RubyInstaller for Windows](https://rubyinstaller.org/)下載安裝，還好去年的新版，已經進步多了，步驟上簡化許多，這些人真是佛心來著。
2. 選個適合自己的程式碼編輯器吧，我最❤️[Atom](https://atom.io/)，現在支援macOS與Windows雙系統的應用程式已經是基本的，重要的是我非常喜灣這個編輯器的版面配置、以及套件非常豐富。
3. 彈性大，表示有一定的學習空間，才能隨心所欲地並發揮工具的好處，於是我在Udemy找了一個課程[Jekyll: make fast, secure static sites and blogs with Jekyll](https://www.udemy.com/static-website-generator-fast-secure-sites-blogs-with-jekyll/learn/v4/announcements?ids=759304)練習了一次，後來又在YouTube找到一位打扮很酷的講師，這個課程免費喔[Jekyll - Static Site Generator ](https://youtu.be/T1itpPvFWHI)，然後我又走了一遍。
4. 豐富的Template，卻是我卡關最久的部分，甚至一度想放棄，原因是這麼多的Template，要如何找到適合你的，尤其是又要發布文章，又要寫文件，真的茫茫大海，一直沒遇到我要的，就這樣經過了一年，當中停滯了10個月~~，真是浪費我上課的錢；技術人員沒有自己的部落格要怎麼紀錄自己走過的路呢，今年又重拾jekyll，先把自己想要的部落格樣子畫在紙上，拿著這個藍圖，上網尋找，終於找到了😍，請看下文介紹。

## [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/)
這真是個偉大的作品，作者非常勤勞的更新程式，每次上GitHub看到作品的commit幾乎都是幾小時前；我的部落格就是用這個Template。
* 建立這個部落格時，本想完全用英文撰寫，因為希望走上國際舞台(想太多了，想用英文撰寫也是卡關原因之一，現在用中文撰寫暢快多了)，而這這個範本多語系，竟然可以設定繁體中文，若沒有這個選項，我也不會選用了。
* 符合我想要撰寫文章，又可編寫文件的需求。
* 提供了文章搜尋功能，使用了很時髦的Algolia(雖然目前使用上有問題，但有個Mark感覺還是很酷🆒)。
* 簡潔清晰的頁面操作。
* 待我繼續敘述，先上我發布文章吧

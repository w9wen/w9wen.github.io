---
title: 解決更新Ruby Sass後Jeklly編譯的錯誤
categories: jekyll ruby sass
---

更新Ruby的套件
```ruby
gem update bundle
```
只要更新到sass的套件，都會出現下列的錯誤
![solved-update-01](/images/2018/04/solved-update-01.png)

其實看這樣的訊息，只知道應該是css編碼錯誤，但完全不知道從何查起，後來終於搜尋到這篇文章[解決中文註解發生錯誤](http://jsnwork.kiiuo.com/archives/1723/sass-scss-compass-susy2-ruby-%E8%A7%A3%E6%B1%BA%E4%B8%AD%E6%96%87%E8%A8%BB%E8%A7%A3%E7%99%BC%E7%94%9F%E9%8C%AF%E8%AA%A4)，才找到了方向，原來是升級了sass，預設沒有UTF-8，於是在以下路徑找到sass.rb
```
D:\Ruby25-x64\lib\ruby\gems\2.5.0\gems\sass-3.5.6\lib\sass.rb
```
設定指令加到最後一行
```
Encoding.default_external = Encoding.find('utf-8')
```
重新執行
```
jekyll serve --draft
```
完成
![solved-update-02](/images/2018/04/solved-update-02.png)

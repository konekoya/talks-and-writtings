
# 元素面版 - 檢查元素樣式
我們用了兩天的時間把如何透過元素面版來動態編輯文件物件模型 (DOM) 講完了，今天我們要一起看的功能是動態編輯元素的樣式。樣式控制台 (Styles pane) 的位置就在元素面版中，通常它會出現在文件物件模型樹區塊 (DOM tree)　的下面，但是如果你的螢幕空間夠大的話，它會改變排版的方式，成為與文件模型樹區塊併排。

![樣式控制台擷圖](https://www.dropbox.com/s/tvw7z8wtuqkjjb6/styles-pane.jpg?raw=1)
> 樣式控制台的位在元素面版的右邊，但是當你的開發者工具寬度太小時，它會改變排版並成為垂直的排版

## 檢查元素樣式
要開始查看一個元素的樣式很簡單，我想可能有些人在前面操作編輯文件物件模型的時候就有注意到了。當你[選擇一個元素](https://github.com/konekoya/talks/blob/master/intro-to-chrome-devtools-triathlon/day-7.md#%E5%B0%8B%E6%89%BE%E5%85%83%E7%B4%A0)之後，這時在樣式控制台裡就可以看到現在所選擇元素的所有樣式。我們來介紹一下這個樣式控制台的內容：

- 樣式排序：首先，所有的樣式排序方式是按樣式繼承的方式來排的，最靠近螢幕方向的這樣式是最底層的樣式 (像是來自 html 或是 body 的樣式)，越往上就是靠近目前這個元素的父元素，一直到最後就是元素自己本身的樣式。然後最後一個是 `element.style {}` 這個表示的是這一個元素的行內樣式 (Inline styles)。

![樣式排序擷圖](https://www.dropbox.com/s/g2u507v0rijsyq2/from-top-to-bottom.jpg?raw=1)

- 有衝突的樣式：在看過幾個元素的樣式後，你一定會看到一些元素的某個樣式定義是被劃掉的，這是代表這個樣式的定義與其他的樣式定義有衝突，而最後因為這個定義的權重 (Specificity) 比較低，所以就沒有套用到這個元素上。另一種同樣會被劃掉的樣式是不正確的樣式屬性 (Property) 或是值 (value) ，也就是說樣式寫錯了XD，瀏覽器沒辦法成功的渲染它，所以它會跳過。而這種不正確的樣式前還會多有一個警示小圖示。  

  ![有衝突的樣式擷圖](https://www.dropbox.com/s/qa7iagqibn2s49w/css-conflict.jpg?raw=1)  
  > 有衝突而被蓋過的樣式
  
  ![不正確的樣式擷圖](https://www.dropbox.com/s/np7y8sv5mpl0sys/invalid-styles.jpg?raw=1)  
  > 不正確的樣式  

  > 如果你不知道 CSS 權重是什麼，強烈建議你一定要了解一下，這是 CSS 的核心概念之一，MDN上有一篇說明[權重的文件](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity)


- 樣式來源：所有的樣式都會有來源，其中最明顯的就是來自於開發者也就是你所寫的樣式表，這個來源的資訊會放在每一段樣式的右上角。當你點下來源後，開發者工具會帶你到原始碼面版 (Sources panel) 裡的樣式表檔案裡，你可以在這裡面編輯及更新你的樣式表，這個我們之後介紹原始碼面版後會再介紹。另外一個值得一提的來源是 user agent stylesheet，這代表這些樣式來自於瀏覽器本身所定義的。

  ![樣式來源擷圖](https://www.dropbox.com/s/6hmizs8kmsxstmd/source-url.jpg?raw=1)  
  > 樣式的來源會列在樣式宣告的右上角

- 區塊模型 (Box model) 模擬圖：在元素樣式的最下方，會有一個區塊模型模擬圖，這個模擬圖會有目前這個元素的 `width`, `height`, `padding`, `border` 及 `margin`，裡面的單位都是 `px` (Pxiel)

  ![區塊模型擷圖](https://www.dropbox.com/s/yj2kfw0jv2ig3en/box-modal.jpg?raw=1)
  > 元素的區塊模型

- hover 樣式：我們在討論編輯文件物件模型的時候有提到，有些元素有擬類別選取項 (Pseudo classes)，在一般的狀態下在樣式中是看不到的。但在樣式控制台的右上角有一個 `:hov` 的小圖示，當你點下這個圖示後，它會打開一個下拉選單，這個選單裡有幾種我們先前有提到的擬類別選取項 (:active, :hover, :focus 跟 :visited)，當你勾選這裡面的項目後，如果這個元素有定義這些選取項的樣式，它就會出現在樣式控制台中。

  ![hover下拉選單擷圖](https://www.dropbox.com/s/s76d8zkfr1bn8kg/hov-dropdown.jpg?raw=1)  
  > :hov 的下拉選單

- 搜尋樣式：當你的專案比較大的時候或是你使用了一些 framework 像是 Bootstrap ，一個很簡單的元素可能藏著一堆樣式宣告，在這些被複雜的樣式中要找到特定屬性真的不是好玩的，這時候，這個搜尋 (雖然它是用一個 filter 圖示…) 的功能就很方便，它可以快速的幫你找到特定的屬性。

## 小結
今天其實本來想一口氣把檢查元素樣式還有編輯全部講完的，但是寫到一半後就想說還是拆成兩天好了，內容實在太多而且也想多跟大家介紹一點觀念上的東西。所以明天我們會繼續一起討論樣式控制台，把如何動態編輯 CSS 介紹完。

# 控制台面版 1 - 讀取-求值-輸出循環
今天我們要一起來討論的 Chrome 開發者工具的控制台面版 (Console panel)，這個面版我們在前面有很[簡單的介紹過](https://github.com/konekoya/talks/blob/master/intro-to-chrome-devtools-triathlon/day-3.md#%E6%8E%A7%E5%88%B6%E5%8F%B0%E9%9D%A2%E7%89%88-console-panel)，其實它就像是一個讀取-求值-輸出循環 (Read-Eval-Print Loop, REPL)，你可以在控制台裡面輸入 JavaScript 的指令，它就會執行並把內容印出來到控制台中。因為這一次的鐵人賽，我開始讀了一些官方的文件，發現控制台面版其實是很複雜的 (真的！相信我XD)，但是我用過的功能只有一小部份，所以我會針對我比較有了解的部份做介紹，剩下的，如果有興趣的朋友，可以到[官方文件](https://developers.google.com/web/tools/chrome-devtools/console/)去讀，我相信是可以挖到很多寶的。

## 使用控制台
控制台使用的方法有兩種，第一種是在打開開發者工具 (參考之前提到的[快捷鍵](https://developers.google.com/web/tools/chrome-devtools/console/)) 後，直接切換到控制台面版。另一種方法則是在任何面版中打開成為一個抽屜 (Drawer)，這種作法是我比較常使用的，並且我會搭配元素 (Elements panel) 跟原始碼(Sources panel) 面版一起使用。跟元素面版一起使用的方法我晚點會說明，與原始碼面版搭配則是要拿來除錯，這一部份我們就留到等介紹原始碼面版時再一併討論。

![控制台面版擷圖](https://www.dropbox.com/s/wfx5956ie38mf4o/console.jpg?raw=1)  
**圖 1**: 控制台面版

![控制台抽屜擷圖](https://www.dropbox.com/s/f4vhav1kxeljp30/console-drawer.jpg?raw=1)  
**圖 2**: 在元素面版打開的控制台抽屜


## 讀取-求值-輸出循環
這裡簡單的介紹如何使用這個面版來做讀取-求值-輸出循環。在打開面版之後如果你的面版裡有其它的 Log，你可以用左上角的小圖示![清除擷圖](https://www.dropbox.com/s/gruwkjd7ct8m3p3/clear.jpg?raw=1) (或是使用快捷鍵Ctrl+L)先把它先清除，清除後我們就可以開始來寫一點簡單的 JavaScript。  

你可以用這個面版來做數值的運算，就像是在 JavaScript 裡一樣：在面版中輸入 `5+5` 再按下 enter 鍵你應該會得到 `10` ，結果應該會出現在輸入的程式正下方。題外話一下，我常常用控制台來做我的小算盤XD


![5+5在控制台輸出的結果擷圖](https://www.dropbox.com/s/hnwwayx5bk0plgk/5%2B5.jpg?raw=1)  
**圖 3**: 5+5 在控制台輸出的結果

你可以宣告變數，重新指定值 (assign)：
```js
// 宣告一個算數
var x = 10;

// 重新指定值
x = function() {
  console.log('Hello world from console!');
}

x(); // 會印出 Hello world from console!
```


> 當你執行上面這一段程式後，除了會得到 `Hello world from console!` 在控制台面版中，應該還會得到一個 `undefined`，這是因為當呼叫一個方法時，控制台面版也會把這個方法的傳回值 (return) 回傳回來。而因為我們定義的方法 `x` 並沒傳回任何值，所以回傳的預設值就是 `undefined`

![Hello-world結果擷圖](https://www.dropbox.com/s/dtuecpak37w20l7/hello-world.jpg?raw=1)  
**圖 4**: `x()` 執行後的結果

進行到這邊我想你會發現，其實我們可以用這個讀取-求值-輸出循環來做很多事。沒錯，常常我會用它來寫一些 JavaScript，來快速的知道某些程式是不是按照我所想的邏輯運作。

你也可以寫像是迴圈這種比較複雜的程式
```js
// 印出 "Hello world from console!" 五次
for (var i = 0; i < 5; i++) {
  console.log('Hello world from console!')
}
```

> 如果印出的訊息是重覆的，控制台面版會幫你整理成一個集合。

![for迴圈結果擷圖](https://www.dropbox.com/s/j6gncr2s1ts9eki/for.jpg?raw=1)  
**圖 5**: `for` 迴圈執行後的結果

當然你也可以使用原生的 JavaScript 方法，像是：
```js
new Date().toLocaleString(); // 得到現在的時間 2017/12/6 上午6:32:23
```
![new-Date結果擷圖](https://www.dropbox.com/s/x9hcgmu2k6isxfa/date.jpg?raw=1)  
**圖 6**: `new Date()` 執行後的結果

或甚至直接存取現在頁面的 DOM 元素

```js
document.body // 整個 DOM 樹會印出來在面版中，並且可以展開及檢視
```
![document-body結果擷圖](https://www.dropbox.com/s/8d6frx5kgli7sbx/dom.jpg?raw=1)  
**圖 7**: `document.body` 執行後的結果

> 我們明天會再介紹如果透過控制台面版提供的一些 API 來快速的選取 DOM 元素

# 小結
我們今天很簡單的介紹了控制台面版的讀取-求值-輸出循環功能，就像你所看到的，你可以在控制台面版裡執行大部份的 JavaScript 程式 (當然是前提 Chrome 要有支援，一些太新的 ES 規範就不保證有支援) 並且馬上就可以看到執行的結果。常常我會用這個面版來執行一些程式片段，比如說在 [stackoverflow](https://stackoverflow.com/) 上看到別人的解法，想要驗證一下程式執行的結果，如果不是太複雜的程式，我們就不用再打開文字編輯器或是像 [codepen](https://codepen.io/) 或 [jsbin](https://jsbin.com/) 的工具來執行。而是直接貼到控制台面版就可以啦。是不是很方便呢？明天我們會接著介紹一些這個面版所提供的 API 還有它如何跟元素面版一起結合使用。



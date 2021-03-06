# 開發者工具快捷鍵跟設定


## 幾個常用的快捷鍵

在這裡我想分享幾個我最常用到的快捷鍵，強迫自己使用快捷鍵可以讓自己的工作速度提昇，強列建議大家可以把你常用的快捷鍵背起來。如果你想要找特定的快捷鍵，官方文件有所有可用[快捷鍵的列表](https://developers.google.com/web/tools/chrome-devtools/shortcuts)。而在開發者工具裡也有快捷鍵的列表，我們下面會提到。

> 我們今天介紹的快捷鍵是全域 (Global) 的，有些快捷鍵是在特定的面版才有，這些快捷鍵我們會留著等在介紹各別面版時一起介紹

* 打開 Chrome 開發者工具 ( 打開後的面版會是上一次你離開開發者工具時正在使用的的那個面版 )： Mac 使用 `Cmmand+Option+I`， Windows 使用 `F12 或  Control+Shift+I`

  > 一個小技巧：打開開發者工具後，在任何面版，只要使用 `Esc` 鍵就可以打開開發者工具下的抽屜 (Drawer)，我通常使用這個指令來打控制台面版 (Console panel)

* 進入元素面版 (Elements panel)，並檢查頁面上的元素： Mac 使用 `Command+Shift+C`， Windows 使用 `Control+Shift+C`
* 搜尋面版： 我最常用於元素面版 (Elements panel) 及原始碼面版 (Sources panel)： Mac 使用 `Command+F`， Windows 使用 `Control+F`
  > 這個指令有幾個面版不支援：審查 (Audits) ，應用 (Application) 及安全性 (Security panels)

* 進入偏好設定頁面：Mac 使用 `? or Function+F1`， Windows 使用 `? or F1`

## 偏好設定

![設定頁面擷圖](https://www.dropbox.com/s/dp3sgpx2a6w7lwk/settings.jpg?raw=1)

在這頁面中你可以調整很多設定來符合你個人的偏好，我會說明幾個我自己常用的，開啟設定頁面的方式：在使用開發者工具的右上角的三點小點圖示上 ![更多選項擷圖](https://www.dropbox.com/s/4hgosdq1e86gp0f/three-dots.jpg?raw=1) 用滑鼠左鍵點擊一下打開下拉選單，然後再從選單中選擇 Settings。

眼尖的朋友應該也有看到，除了 Settings 外，這個下拉選單裡還有一些其他選項，下面我們就來介紹一下：  

![更多選項擷圖](https://www.dropbox.com/s/vzucxz0eie28950/more-options.jpg?raw=1)

- Dock side: 選擇開發工具在頁面上的位置，依序是：獨立視窗、在畫面的左邊、在畫面下面、在畫面右邊
- Hide console drawer: 這我們前面有提過，可以在任何面版中打開控制台抽屜，我通常都用快捷鍵 ESC 開關
- Search all files: 全域搜尋，我沒有用過這個功能，因為各個面版都有自己的搜尋工具可以用
- Open file: 打開檔案，這個我也沒用過，通常需要打開檔案的時機都在原始碼面版，我們後面會介紹
- More tools: 我們昨天有一起看過這個選項裡的一些功能
- Shortcuts: 所有開發者工具內可用的快捷鍵
- Settings: 我們下面會介紹
- Help: 幫助，通常我都直接 Google 比較快XD

下面我們就開始介紹設定的部份：

* 快觀 (Appearance)：

  * 主題 Theme：主題有兩種可以選，如我個人偏好黑色的主題 (Dark) ，所以通常我會改成黑色的。如果想要其他主題，可以參考這個外掛 [DevTools Author](https://github.com/micjamking/devtools-author)

* 原始碼 (Sources)：

  * Enable JavaScript source maps ：這應該是預設打開的，如果沒請記得打開，這樣可以讓你在除錯的時候可以看到還未打包成一個檔案前的檔案。如果你想了解更多關於，官方文件上[有一篇說明](https://developers.google.com/web/tools/chrome-devtools/javascript/source-maps)
  * Enable CSS source maps：應該預設是打開的，這個也是最好要保持打開的選項，這個功能是當你使用一些預處理器 (Preprocessors) 像是 SCSS 的時候，可以在開發者工具裡看到編譯前的 .scss 檔，而不是編譯完後的檔案。

* 元素 (Elements)：

  * Color format ：預設是按照來源 (As authored)，你也可以改成你偏好的顏色模式像是 HEX 或是 RGB

* 網路 (Network)
  * Disable cache (while DevTools is open)：關閉快取這個功能我都會打開，在開發時如果快取沒有每次清，常常會遇到很怪的問題，所以我強列建議一定要打開這個選項，這個功能只有在開發者工具是打開時才有效。
* 控制台 (Console)

  * Preserve log upon navigation：這個功能讓你可以在切換不同頁面時仍然可以看到先前頁面的 logs ，除錯的時候很方便，但是通常我不會打開，有需要時才會打開，不然頁面會有一堆 logs

* 除錯 (Debugger)
  * Disable JavaScript：關閉 JS，在除錯時，關閉 JS 可以讓你縮小錯誤範圍，知道說這個臭蟲是從 JS 來還是 CSS 來的 ( 通常都是 JS XD)，另外如果你有做像是伺服器端渲染 (Server side rendering) 的時候也可以拿來測試從伺服器那裡拿到的頁面是長怎麼樣子。

## 小結

今天我們簡單的介紹幾個常用的快捷鍵跟開發者工具的偏好設定，要記得我們介紹的這幾項功能都只是筆者常用的，還有很多的快捷鍵跟偏好設定是你可以自行設定的。好，接下來我們就要開始詳細的介紹各個面版，明天我們要介紹的是元素面版 (Elements panel)

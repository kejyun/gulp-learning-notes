# 安裝 gulp

> gulp 為 Node.js 的套件，所以安裝 gulp 前請先安裝 Node.js 喔～

## 在全域安裝 gulp 套件

```shell
$ npm install -g gulp
```

## 在要套用 gulp 的專案下安裝 gulp 套件

```shell
~/Code/gulp-project$ npm install gulp
```

## 在專案下的根目錄建立 `gulpfile.js`

在安裝完 gulp 後，我們必須要在我們要套用 gulp 專案下的根目錄建立 `gulpfile.js` 檔案，之後再專案下面執行 gulp 後，gulp 會直接讀取 `gulpfile.js` 檔案去運行

## 第一個 gulp 程式

```js
// 引用 gulp plugin
var gulp = require('gulp');

// 建立預設 gulp task
gulp.task('default', function () {
    console.log('hi~hi~hi~~~');
});
```
gulp 可以將每一個你要執行的工作做命名，而預設會運行 `default` 的工作，所以我們先使用預設的工作進行 gulp 程式的測試，然後再專案的根目錄執行 `gulp` 指令：

```
~/Code/gulp-project$ gulp
[22:26:31] Using gulpfile ~/Code/gulp-project/gulpfile.js
[22:26:31] Starting 'default'...
hi~hi~hi~~~
[22:26:31] Finished 'default' after 126 μs
```

這樣我們就會看到 gulp 的執行結果了！！


## 參考資料
* [Learning Gulp #1 - Installing & Introducing Gulp](https://www.youtube.com/watch?v=wNlEK8qrb0M&list=PLLnpHn493BHE2RsdyUNpbiVn-cfuV7Fos&index=1)

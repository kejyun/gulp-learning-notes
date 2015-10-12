# gulp-notify

> gulp 處理通知

## 前言

當 gulp 處理完檔案後，如果我們需要 gulp 告知我們處理結束了，可以使用 gulp-notify 告知我們處理狀況

## 安裝

```shell
$ npm install --save-dev gulp-notify
```

## JavaScript 最小化加入處理通知

在 JavaScript 最小化後，我們希望 gulp 通知我們 `Minify JavaScript Finish` 的訊息

```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpUglify = require('gulp-uglify'),  // 載入 gulp-uglify
    gulpNotify = require("gulp-notify");  // 載入 gulp-notify

gulp.task('watch', function () {
    gulpLivereload.listen();
    gulp.watch('javascript/original/*.js', ['scripts']);
});

gulp.task('script', function () {
    gulp.src('javascript/original/*.js')        // 指定要處理的原始 JavaScript 檔案目錄
        .pipe(gulpUglify())                     // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify')),  // 指定最小化後的 JavaScript 檔案目錄
        .pipe(gulpNotify("Minify JavaScript Finish"));  // 處理結束通知訊息
});
```

## 通知訊息

之後在 gulp 最小化 JavaScript 後就會出現像這樣的通知訊息了

![JavaScript 最小化通知](images/gulp-notify-javascript-minify.png)


## 參考資料
* [gulp-notify](https://www.npmjs.com/package/gulp-notify/)

# gulp-uglify

> 最小化 JavaScript

## 安裝

```shell
$ npm install --save-dev gulp-uglify
```

## 最小化 JavaScript

將要最小化的 JavaScript 檔案目錄指定為專案 `javascript/original` 目錄下的所有 `.js` 的檔案

並將最小化後的 JavaScript 檔案指定放在 `javascript/minify` 目錄下

```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpUglify = require('gulp-uglify');  // 載入 gulp-uglify

gulp.task('script', function () {
    gulp.src('javascript/original/*.js')        // 指定要處理的原始 JavaScript 檔案目錄
        .pipe(gulpUglify())                     // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify'));  // 指定最小化後的 JavaScript 檔案目錄
});
```

## 執行 JavaScript 最小化

```shell
$ gulp script
[17:31:07] Using gulpfile ~/Code/Project/gulpfile.js
[17:31:07] Starting 'default'...
[17:31:07] Finished 'default' after 12 ms
```

執行完畢就可以到 `javascript/minify` 目錄看最小化後檔案的成果了！


## 加入監看工作

我們加入監看檔案異動狀況的 watch 工作

```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpUglify = require('gulp-uglify');  // 載入 gulp-uglify

gulp.task('watch', function () {
    gulp.watch('javascript/original/*.js', ['scripts']);
});

gulp.task('script', function () {
    gulp.src('javascript/original/*.js')        // 指定要處理的原始 JavaScript 檔案目錄
        .pipe(gulpUglify())                     // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify'));  // 指定最小化後的 JavaScript 檔案目錄
});
```

執行 watch 工作後，在每次我們異動 `javascript/original/*.js` 中的所有 JavaScript 檔案時，我們都會重新執行 `script` 的工作

```shell
$ gulp watch
[19:01:30] Using gulpfile ~/Code/Project/gulpfile.js
[19:01:30] Starting 'watch'...
[19:01:30] Finished 'watch' after 14 ms
[19:01:44] Starting 'scripts'...
[19:01:44] Finished 'scripts' after 13 ms
[19:01:52] Starting 'scripts'...
[19:01:52] Finished 'scripts' after 3.88 ms
```

## 參考資料
* [gulp-uglify](https://www.npmjs.com/package/gulp-uglify/)
* [Learning Gulp #2 - Using Plugins & Minifying JavaScript](https://www.youtube.com/watch?v=Kh4eYdd8O4w&list=PLhIIfyPeWUjoySSdufaqfaSLeQDmCCY3Q)

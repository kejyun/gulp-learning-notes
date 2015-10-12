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

gulp.task('default', function () {
    gulp.src('javascript/original/*.js')        // 指定要處理的原始 JavaScript 檔案目錄
        .pipe(gulpUglify())                     // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify'));  // 指定最小化後的 JavaScript 檔案目錄
});
```

## 執行 JavaScript 最小化

```shell
$ gulp
[17:31:07] Using gulpfile ~/Code/Project/gulpfile.js
[17:31:07] Starting 'default'...
[17:31:07] Finished 'default' after 12 ms
```

執行完畢就可以到 `javascript/minify` 目錄看最小化後檔案的成果了！

## 參考資料
* [gulp-uglify](https://www.npmjs.com/package/gulp-uglify/)
* [Learning Gulp #2 - Using Plugins & Minifying JavaScript](https://www.youtube.com/watch?v=Kh4eYdd8O4w&list=PLhIIfyPeWUjoySSdufaqfaSLeQDmCCY3Q)

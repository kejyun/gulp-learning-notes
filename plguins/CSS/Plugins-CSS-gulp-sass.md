# gulp-sass

> 編譯 sass/scss 檔案

## 安裝

```shell
$ npm install gulp-sass --save-dev
```

## 編譯 Scss 檔案

將要編譯 Scss 檔案目錄指定為專案 `scss/**/*.scss` 目錄下的所有 `.scss` 的檔案（包含所有階層目錄的檔案）

並將編譯後的 css 檔案指定放在 `css` 目錄下

```javascript
var gulp = require('gulp'),             // 載入 gulp
    gulpSass = require('gulp-sass');    // 載入 gulp-sass

gulp.task('styles', function () {
    gulp.src('scss/**/*.scss')    // 指定要處理的 Scss 檔案目錄
        .pipe(gulpSass())         // 編譯 Scss
        .pipe(gulp.dest('css'));  // 指定編譯後的 css 檔案目錄
});
```

## 執行編譯 Scss

```shell
$ gulp styles
[17:31:07] Using gulpfile ~/Code/Project/gulpfile.js
[17:31:07] Starting 'default'...
[17:31:07] Finished 'default' after 12 ms
```

執行完畢就可以到 `css` 目錄看編譯後的檔案的成果了！

## 壓縮 css 檔案

我們在 scss 壓縮工具中加入參數 `{outputStyle: 'compressed'}`，這樣在編譯出來後的 css 檔案就會是壓縮過後的狀態

```javascript
gulp.task('styles', function () {
    gulp.src('scss/**/*.scss')    // 指定要處理的 Scss 檔案目錄
        .pipe(gulpSass({          // 編譯 Scss
            outputStyle: 'compressed'
        }))
        .pipe(gulp.dest('css'));  // 指定編譯後的 css 檔案目錄
});
```

## 加入監看工作

我們加入監看檔案異動狀況的 watch 工作

```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpSass = require('gulp-sass');    // 載入 gulp-sass

gulp.task('watch', function () {
    gulp.watch('scss/**/*.scss', ['styles']);
});

gulp.task('styles', function () {
    gulp.src('scss/**/*.scss')    // 指定要處理的 Scss 檔案目錄
        .pipe(gulpSass({          // 編譯 Scss
            outputStyle: 'compressed'
        }))         
        .pipe(gulp.dest('css'));  // 指定編譯後的 css 檔案目錄
});
```

執行 watch 工作後，在每次我們異動 `scss/**/*.scss` 中的所有 Scss 檔案時，我們都會重新執行 `styles` 的工作

```shell
$ gulp watch
[19:51:30] Using gulpfile ~/Code/Project/gulpfile.js
[19:51:30] Starting 'watch'...
[19:51:30] Finished 'watch' after 14 ms
[19:51:50] Starting 'styles'...
[19:51:50] Finished 'styles' after 2.21 ms
[19:51:57] Starting 'styles'...
[19:51:57] Finished 'styles' after 1.45 ms
```

## 參考資料
* [Learning Gulp #5 - Compiling Sass With Gulp](https://www.youtube.com/watch?v=cg7lwX0u-U0&index=5&list=PLhIIfyPeWUjoySSdufaqfaSLeQDmCCY3Q)
* [gulp-sass](https://www.npmjs.com/package/gulp-sass/)

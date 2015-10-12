# gulp-livereload

> 當 HTML, CSS 或 JavaScript 異動時，自動重新載入頁面

## 前言

當我們異動 HTML, CSS 或 JavaScript 檔案時，我們通常要到頁面重新整理才可以看到新的結果，而 livereload 套件可以自動幫我們完成 `重新整理` 這個動作

## 安裝

```shell
$ npm install --save-dev gulp-livereload
```

## 使用 livereload

我們在 gulp watch 的時候，啟動 Livereload server，並在 CSS 或 JavaScript 異動時，使用 `pipe(gulpLivereload())` 自動重新載入頁面

```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpUglify = require('gulp-uglify'),  // 載入 gulp-uglify
    gulpSass = require('gulp-sass'),      // 載入 gulp-sass
    gulpPlumber = require('gulp-plumber'),// 載入 gulp-plumber
    gulpLivereload = require('gulp-livereload');  // 載入 gulp-livereload

gulp.task('watch', function () {
    gulpLivereload.listen();
    gulp.watch('javascript/original/*.js', ['scripts']);
    gulp.watch('scss/**/*.scss', ['styles']);
});

gulp.task('script', function () {
    gulp.src('javascript/original/*.js')        // 指定要處理的原始 JavaScript 檔案目錄
        .pipe(gulpPlumber())                    // 使用 gulp-plumber 處理例外
        .pipe(gulpUglify())                     // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify')),  // 指定最小化後的 JavaScript 檔案目錄
        .pipe(gulpLivereload());                // 當檔案異動後自動重新載入頁面
});

gulp.task('styles', function () {
    gulp.src('scss/**/*.scss')    // 指定要處理的 Scss 檔案目錄
        .pipe(gulpPlumber())      // 使用 gulp-plumber 處理例外
        .pipe(gulpSass({          // 編譯 Scss
            outputStyle: 'compressed'
        }))
        .pipe(gulp.dest('css')).  // 指定編譯後的 css 檔案目錄
        .pipe(gulpLivereload());  // 當檔案異動後自動重新載入頁面
});
```

## 開啟 gulp watch 及 livereload server

```shell
$ gulp watch
[22:08:31] Using gulpfile ~/Code/italkjob/gulpfile.js
[22:08:31] Starting 'watch'...
[22:08:31] Finished 'watch' after 23 ms
[22:08:31] Starting 'default'...
[22:08:31] Finished 'default' after 22 μs
[22:08:31] /Users/kejyun/Project/css/test.css reloaded.
[22:08:31] /Users/kejyun/Project/javascript/minify/test.js reloaded.
```

## 安裝 Chrome Livereload 套件

我們開啟 Chrome 安裝[Livereload Chrome 套件](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei?hl=zh-TW)，之後會在瀏覽器的右上角看到 Livereload 套件的圖示，示意如下：

![Chrome Livereload 圖示(關閉)](./images/chrome-livereload-off-icon.png)

之後我們點選此 icon，會看到中間空心圓變成實心圓，這樣的話表示開啟成功

![Chrome Livereload 圖示(開啟)](./images/chrome-livereload-on-icon.png)

之後我們異動任何的 CSS 或 JavaScript，瀏覽器就可以幫我們自動重新載入摟，Enjoy it～

## 參考資料
* [gulp-livereload](https://www.npmjs.com/package/gulp-livereload/)
* [Livereload Chrome 套件](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei?hl=zh-TW)

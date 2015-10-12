# gulp-plumber

> 例外處理，避免例外導致 gulp watch 失效中斷

## 前言

當我們在使用 gulp watch 監看 [gulp-sass](../CSS/Plugins-CSS-gulp-sass.md) 編譯 Scss 或 [gulp-uglify](../JavaScript/Plugins-JavaScript-gulp-uglify.md) 去最小化 JavaScript 時，當 CSS 或 JavaScript 程式寫錯時，gulp 在處理 Scss 跟 JavaScript 會丟出例外，並中斷執行 gulp watch 的監看

但我們程式寫錯是無法避免的，而我們希望 gulp watch 能夠在我們把程式錯誤改回來後，繼續做監看的動作，我們就可以使用 gulp-plumber

#### gulp watch 例外錯誤

```shell
$ gulp watch
[19:51:45] Using gulpfile ~/Code/Project/gulpfile.js
[19:51:50] Starting 'styles'...
[19:51:50] Finished 'styles' after 2.21 ms
[19:51:57] Starting 'styles'...
[19:51:57] Finished 'styles' after 1.45 ms
[20:00:32] Starting 'styles'...
[20:00:32] Finished 'styles' after 2.74 ms

events.js:141
      throw er; // Unhandled 'error' event
      ^
Error: /scss/test.scss
  29:1  invalid top-level expression
    at options.error (/Users/kejyun/Project/node_modules/gulp-sass/node_modules/node-sass/lib/index.js:277:32)
```

## 安裝

```shell
$ npm install --save-dev gulp-plumber
```

## 使用 gulp-plumber

我們可以在編譯 Scss 及最小化 JavaScript 的時候使用加入 `pipe(gulpPlumber())` 去使用 gulp-plumber

> 注意：`pipe(gulpPlumber())` 一定要在編譯 Scss 及最小化 JavaScript之前就優先加入（加入順序有差異），否則會無法起到作用

```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpUglify = require('gulp-uglify'),  // 載入 gulp-uglify
    gulpSass = require('gulp-sass'),      // 載入 gulp-sass
    gulpPlumber = require('gulp-plumber');// 載入 gulp-plumber

gulp.task('watch', function () {
    gulp.watch('javascript/original/*.js', ['scripts']);
    gulp.watch('scss/**/*.scss', ['styles']);
});

gulp.task('script', function () {
    gulp.src('javascript/original/*.js')        // 指定要處理的原始 JavaScript 檔案目錄
        .pipe(gulpPlumber())                    // 使用 gulp-plumber 處理例外
        .pipe(gulpUglify())                     // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify'));  // 指定最小化後的 JavaScript 檔案目錄
});

gulp.task('styles', function () {
    gulp.src('scss/**/*.scss')    // 指定要處理的 Scss 檔案目錄
        .pipe(gulpPlumber())      // 使用 gulp-plumber 處理例外
        .pipe(gulpSass({          // 編譯 Scss
            outputStyle: 'compressed'
        }))
        .pipe(gulp.dest('css'));  // 指定編譯後的 css 檔案目錄
});
```

## 使用 gulp-plumber 監看

在發生例外時，gulp watch 會顯示例外資訊，當我們重新修正程式後，gulp 就會繼續自己重新編譯 Scss 或最小化 JavaScript

這樣就不會在手殘時還需要重新做 gulp watch 去監看所有 gulp 的工作了，Enjoy it～

```shell
$ gulp watch
[20:13:44] Using gulpfile ~/Code/italkjob/gulpfile.js
[20:13:44] Starting 'scripts'...
[20:13:44] Finished 'scripts' after 15 ms
[20:13:44] Starting 'styles'...
[20:13:44] Finished 'styles' after 5.89 ms
[20:13:44] Starting 'watch'...
[20:13:44] Finished 'watch' after 19 ms
[20:13:44] Starting 'default'...
[20:13:44] Finished 'default' after 23 μs
[20:13:50] Starting 'styles'...
[20:13:50] Finished 'styles' after 3.65 ms
[20:13:51] Plumber found unhandled error:
 Error in plugin 'gulp-sass'
Message:
    scss/test.scss
  29:1  invalid top-level expression
Details:
    column: 1
    line: 29
    file: stdin
    status: 1
    messageFormatted: scss/test.scss
  29:1  invalid top-level expression
[20:13:53] Starting 'styles'...
[20:13:53] Finished 'styles' after 2.26 ms
```

## 參考資料
* [Learning Gulp #6 - Keep Gulp Running With Plumber](https://www.youtube.com/watch?v=rF6niaDKcxE&index=6&list=PLhIIfyPeWUjoySSdufaqfaSLeQDmCCY3Q)
* [gulp-plumber](https://www.npmjs.com/package/gulp-plumber/)

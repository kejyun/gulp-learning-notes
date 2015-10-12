# 例外處理

當我們使用  [gulp-plumber](../plguins/Tool/Plugins-Tool-gulp-plumber.md) 去做例外處理時，我們也可以使用內建的例外處理函式去處理


```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpUglify = require('gulp-uglify'),  // 載入 gulp-uglify
    gulpSass = require('gulp-sass');      // 載入 gulp-sass

gulp.task('watch', function () {
    gulp.watch('javascript/original/*.js', ['scripts']);
    gulp.watch('scss/**/*.scss', ['styles']);
});

gulp.task('script', function () {
    gulp.src('javascript/original/*.js')            // 指定要處理的原始 JavaScript 檔案目錄
        .on('error', console.error.bind(console))   // 使用錯誤事件處理例外
        .pipe(gulpUglify())                         // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify'));      // 指定最小化後的 JavaScript 檔案目錄
});

gulp.task('styles', function () {
    gulp.src('scss/**/*.scss')                      // 指定要處理的 Scss 檔案目錄
        .on('error', console.error.bind(console))   // 使用錯誤事件處理例外
        .pipe(gulpSass({                            // 編譯 Scss
            outputStyle: 'compressed'
        }))
        .pipe(gulp.dest('css'));                    // 指定編譯後的 css 檔案目錄
});
```


## 監看 gulp 工作

當我們在兼看工作時發生例外，這樣也可以僅顯示錯誤例外的訊息而不中斷程式

```shell
$ gulp
[20:36:08] Using gulpfile ~/Code/Project/gulpfile.js
[20:36:08] Starting 'scripts'...
[20:36:08] Finished 'scripts' after 12 ms
[20:36:08] Starting 'styles'...
[20:36:08] Finished 'styles' after 4.73 ms
[20:36:08] Starting 'watch'...
[20:36:08] Finished 'watch' after 17 ms
[20:36:08] Starting 'default'...
[20:36:08] Finished 'default' after 18 μs
[20:36:13] Starting 'styles'...
[20:36:13] Finished 'styles' after 3.06 ms
{ [Error: resources/public/scss/test.scss
  29:1  invalid top-level expression]
  message: 'scss/test.scss\n  29:1  invalid top-level expression',
  column: 1,
  line: 29,
  file: 'stdin',
  status: 1,
  messageFormatted: '\u001b[4mscss/test.scss\u001b[24m\n\u001b[90m  29:1\u001b[39m  invalid top-level expression',
  name: 'Error',
  stack: 'Error: scss/test.scss\n  29:1  invalid top-level expression\n    at options.error (/Users/kejyun/Project/node_modules/gulp-sass/node_modules/node-sass/lib/index.js:277:32)',
  showStack: false,
  showProperties: true,
  plugin: 'gulp-sass' }
[20:36:22] Starting 'styles'...
[20:36:22] Finished 'styles' after 1.58 ms
```

## 定義紀錄例外錯誤函式

因為例外錯誤處理我們可能很多地方都會用到，所以我們可以將它定義成函式讓每個地方都可以呼叫使用

```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpUglify = require('gulp-uglify'),  // 載入 gulp-uglify
    gulpSass = require('gulp-sass');      // 載入 gulp-sass

// 紀錄例外錯誤函式
function errorLog(error) {
  console.error(error);
  this.emit('end');
}

gulp.task('watch', function () {
    gulp.watch('javascript/original/*.js', ['scripts']);
    gulp.watch('scss/**/*.scss', ['styles']);
});

gulp.task('script', function () {
    gulp.src('javascript/original/*.js')            // 指定要處理的原始 JavaScript 檔案目錄
        .on('error', errorLog)                      // 使用錯誤事件處理例外
        .pipe(gulpUglify())                         // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify'));      // 指定最小化後的 JavaScript 檔案目錄
});

gulp.task('styles', function () {
    gulp.src('scss/**/*.scss')                      // 指定要處理的 Scss 檔案目錄
        .on('error', errorLog)                      // 使用錯誤事件處理例外
        .pipe(gulpSass({                            // 編譯 Scss
            outputStyle: 'compressed'
        }))
        .pipe(gulp.dest('css'));                    // 指定編譯後的 css 檔案目錄
});
```

## 參考資料
* [Learning Gulp #7 - Handling Errors Without Plumber](https://www.youtube.com/watch?v=o24f4imRbxQ&list=PLLnpHn493BHE2RsdyUNpbiVn-cfuV7Fos&index=7)

# 監看

在我們使用「[gulp-uglify](../plguins/JavaScript/Plugins-JavaScript-gulp-uglify.md)」去最小化 JavaScript 時，我們可能會希望在每次我們異動 JavaScript 檔案的時候，gulp 可以自動幫我們執行最小化的動作。

原始的最小化 JavaScript 程式會像這樣

```javascript
var gulp = require('gulp'),               // 載入 gulp
    gulpUglify = require('gulp-uglify');  // 載入 gulp-uglify

gulp.task('script', function () {
    gulp.src('javascript/original/*.js')        // 指定要處理的原始 JavaScript 檔案目錄
        .pipe(gulpUglify())                     // 將 JavaScript 做最小化
        .pipe(gulp.dest('javascript/minify'));  // 指定最小化後的 JavaScript 檔案目錄
});
```

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

## 指定所有檔案異動就做 gulp 工作

我們也可以使用 `**` 指定任何檔案做異動時就執行 gulp 指令

```javascript
gulp.task('watch', function () {
    gulp.watch('javascript/original/**', ['scripts']);
});
```

## 指定使用預設工作去執行監看工作，並預先執行指定工作

我們可以在預設的工作加入所有要執行的工作，並在最後指定執行 `watch` 監看的工作，這樣我們就可以輸入 gulp 指令去執行所有工作

```javascript
gulp.task('default', ['scripts', 'styles', 'watch']);
```

```shell
$ gulp
[19:01:30] Using gulpfile ~/Code/Project/gulpfile.js
[19:15:20] Starting 'scripts'...
[19:15:20] Finished 'scripts' after 12 ms
[19:15:20] Starting 'styles'...
[19:15:20] Finished 'styles' after 58 μs
[19:15:20] Starting 'watch'...
[19:15:25] Finished 'watch' after 4.27 s
[19:15:25] Starting 'default'...
[19:15:25] Finished 'default' after 17 μs
[19:15:25] Starting 'scripts'...
```

# 工作

gulp 可以讓你對不同的工作進行命名，`default` 是預設的工作名稱，如果你在執行 gulp 指令時沒有指定要執行哪個工作名稱，gulp 會預設執行 `default` 的工作

```javascript
// 載入 gulp
var gulp = require('gulp');

// 定義名稱為 default 的 gulp 工作
gulp.task('default', function () {
    console.log('Hello Gulp Default Task');
});

// 定義名稱為 other 的 gulp 工作
gulp.task('other', function () {
    console.log('Hello Gulp Other Task');
});
```

## 執行指定的 gulp 工作

我們定義 2 個 gulp 工作，名稱分別為 `default` 及 `other`

### 執行預設 `default` 的 gulp 工作

```shell
$ gulp
[16:44:21] Using gulpfile ~/Code/Project/gulpfile.js
[16:44:21] Starting 'default'...
Hello Gulp Default Task
[16:44:21] Finished 'default' after 139 μs
```

### 執行指定的 `other` gulp 工作

```shell
$ gulp
[16:44:21] Using gulpfile ~/Code/Project/gulpfile.js
[16:44:21] Starting 'default'...
Hello Gulp Other Task
[16:44:21] Finished 'default' after 139 μs
```


## 指定預設工作執行多個工作

假如我們有多個工作想要執行，我們可以在預設 `default` 的工作指定想要執行的工作名稱陣列，像是 `['other', 'scripts']`，這樣在執行 `default` 工作時，gulp 就會依序的執行 `other` 及 `scripts` 的工作了。

```javascript
// 載入 gulp
var gulp = require('gulp');

// 定義名稱為 default 的 gulp 工作
gulp.task('default', ['other', 'scripts']);

// 定義名稱為 other 的 gulp 工作
gulp.task('other', function () {
    console.log('Hello Gulp Other Task');
});

// 定義名稱為 scripts 的 gulp 工作
gulp.task('scripts', function () {
    console.log('Hello Gulp Scripts Task');
});
```

執行多個工作

```shell
$ gulp
[18:54:40] Using gulpfile ~/Code/Project/gulpfile.js
[18:54:40] Starting 'other'...
Hello Gulp Other Task
[18:54:40] Finished 'other' after 127 μs
[18:54:40] Starting 'scripts'...
Hello Gulp Scripts Task
[18:54:40] Finished 'scripts' after 44 μs
[18:54:40] Starting 'default'...
[18:54:40] Finished 'default' after 9.42 μs
```

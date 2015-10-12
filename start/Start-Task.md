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

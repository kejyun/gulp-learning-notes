# browser-sync

> 瀏覽器同步檢視

## 前言

如果我們在修改頁面時，想要同時知道不同瀏覽器畫面的瀏覽狀況時，可以透過 browser-sync 去達到同時瀏覽畫面的效果

## 安裝

```shell
$ npm install --save-dev browser-sync
```

## 啟動 BrowserSync 服務

啟動 BrowserSync 的服務時，指定去監控 hostname 為 `kejyun.dev` 的網頁
然後監看我們任何網頁的 html 或 css 檔案做異動的時候，自動重新讀取頁面

> `kejyun.dev` 為我在 `/etc/hosts` 裡面自訂的網域，連到自己本機的主機


```javascript
var gulp        = require('gulp');
var browserSync = require('browser-sync').create();
var sass        = require('gulp-sass');

// 服務
gulp.task('serve', ['sass'], function () {
    browserSync.init({
        proxy: "kejyun.dev"   // hostname
    });
});

// 監看工作
gulp.task('watch', function () {

    gulp.watch("app/scss/*.scss", ['sass']);
    gulp.watch("app/*.html").on('change', browserSync.reload);
});

// 編譯 SASS 檔案
gulp.task('sass', function() {
    return gulp.src("app/scss/*.scss")
        .pipe(sass())
        .pipe(gulp.dest("app/css"))
        .pipe(browserSync.stream());
});

gulp.task('default', ['serve', 'watch']);
```

## 啟動 gulp

啟動 gulp 後，BrowserSync 會自動開啟瀏覽器，並開啟 `http://localhost:3000/` 網址，之後只要再自己用瀏覽器分頁手動開啟 `http://localhost:3000/`，BrowserSync 自己就會做畫面同步的動作了，這樣在不同畫面解析度就能夠同時開發了，Enjoy it～

```javascript
$ gulp dev
[19:00:37] Using gulpfile ~/Project/gulpfile.js
[19:00:38] Starting 'serve'...
[19:00:38] Finished 'serve' after 7.66 μs
[BS] Proxying: http://kejyun.dev
[BS] Access URLs:
 --------------------------------------
       Local: http://localhost:3000
    External: http://192.168.1.105:3000
 --------------------------------------
          UI: http://localhost:3001
 UI External: http://192.168.1.105:3001
 --------------------------------------
 [19:00:38] Starting 'watch'...
 [19:00:38] Finished 'watch' after 657 ms
```


## 參考資料
* [Browsersync + Gulp.js](http://www.browsersync.io/docs/gulp/)
* [Browsersync - Time-saving synchronised browser testing](http://www.browsersync.io/)
* [browser-sync](https://www.npmjs.com/package/browser-sync)

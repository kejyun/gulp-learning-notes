# gulp-imagemin

> 壓縮圖片

## 前言

我們網站的圖片有時候沒有最佳化，圖片的大小可能會很大，為的能夠讓使用者瀏覽的體驗能夠變好，我們通常希望圖片的檔案越小越好，此時我們可以用 gulp-imagemin 去自動壓縮圖片檔案

> 支援圖片類型 gif, jpg, png, svg

## 安裝

```shell
$ npm install --save-dev gulp-imagemin
```

## 使用 gulp-imagemin 壓縮圖片

我們指定 `images/original/**` 的所有圖片都壓縮，並將壓縮的檔案都儲存到 `images` 資料夾

```javascript
var gulp = require('gulp'),
    gulpImagemin = require('gulp-imagemin');

gulp.task('image', function () {
    gulp.src('images/original/**')
        .pipe(gulpImagemin())
        .pipe(gulp.dest('images'));
});
```

## 壓縮圖片

執行 `gulp image` 進行圖片的壓縮

```shell
$ gulp image
[22:31:35] Using gulpfile ~/Code/italkjob/gulpfile.js
[22:31:35] Starting 'image'...
[22:31:35] Finished 'image' after 11 ms
[22:31:38] gulp-imagemin: Minified 2 images (saved 166.29 kB - 23.5%)
```

壓縮完畢我們就可以到 `images` 資料夾去看壓縮處理後的圖片了，Enjoy it～

## 參考資料
* [Learning Gulp #9 - Easy Image Compression](https://www.youtube.com/watch?v=oXxMdT7T9qU&index=8&list=PLLnpHn493BHE2RsdyUNpbiVn-cfuV7Fos)
* [gulp-imagemin](https://www.npmjs.com/package/gulp-imagemin/)

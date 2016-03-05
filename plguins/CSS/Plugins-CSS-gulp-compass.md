# gulp-compass

> 編譯 sass/scss 檔案

## 安裝

```shell
$ npm install gulp-compass --save-dev
```

## 編譯 Scss 檔案

把原先在 `config.rb` 的設定設定到 gulp-compass 的參數中

```javascript
var gulp           = require('gulp'),
    gulpCompass    = require('gulp-compass');

gulp.task('styles', function () {
    gulp.src('resources/assets/sass/**/*.sass') // sass 來源路徑
        .pipe(gulpCompass({
            css: 'public/assets/css',           // compass 輸出位置
            sass: 'resources/assets/sass',      // sass 來源路徑
            image: 'resources/assets/images',   // 圖片來源路徑
            style: 'compressed',                // CSS 處理方式，預設 nested（expanded, nested, compact, compressed）
            comments: false,                    // 是否要註解，預設(true)
            require: ['susy'],                  // 額外套件 susy
        }));
        // .pipe(gulp.dest('app/assets/temp')); // 輸出位置(非必要)
});
```

## 執行 gulp-compass 處理 CSS

```shell
$ gulp styles
[15:23:21] Using gulpfile ~/Project/gulpfile.js
[15:23:21] Starting 'styles'...
[15:23:21] Finished 'styles' after 14 ms
    write public/assets/css/app.css
```

## 參考資料
* [gulp-compass](https://www.npmjs.com/package/gulp-compass)
* [Gulp RUN ruby-compass](http://wcc723.github.io/gulp/2014/11/07/gulp-on-diff-os/)

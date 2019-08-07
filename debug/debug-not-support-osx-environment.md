# Node Sass does not yet support your current environment: OS X 64-bit with Unsupported runtime

*錯誤訊息*

```
$ gulp
/Users/kejyun/Code/laravel/node_modules/node-sass/lib/binding.js:13
      throw new Error(errors.unsupportedEnvironment());
      ^

Error: Node Sass does not yet support your current environment: OS X 64-bit with Unsupported runtime (64)
For more information on which environments are supported please see:
https://github.com/sass/node-sass/releases/tag/v3.13.1
    at module.exports (/Users/kejyun/Code/laravel/node_modules/node-sass/lib/binding.js:13:13)
    at Object.<anonymous> (/Users/kejyun/Code/laravel/node_modules/node-sass/lib/index.js:14:35)
    at Module._compile (internal/modules/cjs/loader.js:776:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:787:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)
    at Module.require (internal/modules/cjs/loader.js:690:17)
    at require (internal/modules/cjs/helpers.js:25:18)
    at Object.<anonymous> (/Users/kejyun/Code/laravel/node_modules/gulp-sass/index.js:187:21)
```

*解決辦法*


1. 移除 `node_modules` 資料夾重新安裝套件即可

```
rm node_modules
npm install
```

2. 重建建立 sass 套件

```
npm rebuild node-sass
```


## 參考資料
* [\[Unsupported\] Installing node-sass 3.10.1 on Node 7 · Issue \#1764 · sass/node-sass](https://github.com/sass/node-sass/issues/1764)

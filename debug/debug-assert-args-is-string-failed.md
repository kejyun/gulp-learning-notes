# gulp[89743]: ../src/node_contextify.cc:635:static void node::contextify::ContextifyScript::New(const FunctionCallbackInfo<v8::Value> &): Assertion \`args[1]->IsString()' failed.


*錯誤訊息*

```
$ gulp
gulp[89743]: ../src/node_contextify.cc:635:static void node::contextify::ContextifyScript::New(const FunctionCallbackInfo<v8::Value> &): Assertion `args[1]->IsString()' failed.
 1: 0x10003cf99 node::Abort() [/Users/kejyun/.nvm/versions/node/v10.16.0/bin/node]
 2: 0x10003bfbb node::AddEnvironmentCleanupHook(v8::Isolate*, void (*)(void*), void*) [/Users/kejyun/.nvm/versions/node/v10.16.0/bin/node]
 3: 0x1000674c2 node::contextify::ContextifyScript::New(v8::FunctionCallbackInfo<v8::Value> const&) [/Users/kejyun/.nvm/versions/node/v10.16.0/bin/node]
 4: 0x100242aaf v8::internal::FunctionCallbackArguments::Call(v8::internal::CallHandlerInfo*) [/Users/kejyun/.nvm/versions/node/v10.16.0/bin/node]
 5: 0x100241c4b v8::internal::MaybeHandle<v8::internal::Object> v8::internal::(anonymous namespace)::HandleApiCallHelper<true>(v8::internal::Isolate*, v8::internal::Handle<v8::internal::HeapObject>, v8::internal::Handle<v8::internal::HeapObject>, v8::internal::Handle<v8::internal::FunctionTemplateInfo>, v8::internal::Handle<v8::internal::Object>, v8::internal::BuiltinArguments) [/Users/kejyun/.nvm/versions/node/v10.16.0/bin/node]
 6: 0x100241667 v8::internal::Builtin_Impl_HandleApiCall(v8::internal::BuiltinArguments, v8::internal::Isolate*) [/Users/kejyun/.nvm/versions/node/v10.16.0/bin/node]
 7: 0x24595e3dbe3d
Abort trap: 6
```

*解決辦法*

使用下列指令安裝即可解決

```
npm i natives
```


## 參考資料
* [node asserts in node_contextify.cc:631 Assertion \`args[1]->IsString()' failed · Issue #20325 · nodejs/node](https://github.com/nodejs/node/issues/20325)

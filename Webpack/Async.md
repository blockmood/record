## 异步加载流程

### webpack_require

> 通过 webpack_require 加载模块

### webpack_require_e

> 类似 jsonp 的形式 (具体实现函数 jsonpScriptSrc)

```
function jsonpScriptSrc(chunkId) {
  return __webpack_require__.p + publicPath + ({}[chunkId] || chunkId) + ".bundle.js";
}

```

### webpackJsonp

> 全局变量 有俩个参数 [ chunkId, ()=> {}] 1 chunkId 2 模块列表

### webpackJsonpCallback

> 安装异步模块

## 实现流程

通过 webpack_require 加载主程序代码

碰到异步代码，通过 publicPath 和 chunId 找到异步的文件地址

webpack_require_e 通过找到的异步文件地址发起 Jsonp，得到对应的 chunk

webpackJsonp push chunkId 和得到的模块列表

保存触发 webpackJsonpCallback 安装模块列表

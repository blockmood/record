## 打包的主要流程

- 读取到入口文件的内容
- 分析入口文件，递归寻找所有模块的依赖，生成 AST 树
- 根据 AST 生成浏览器可识别的代码

## 细节

- 获取主模块的内容
- 分析模块
  - @babel/parser (转 AST)
- 对模块进行处理
  - @babel/traverse (收集依赖)
  - @babel/core @babel/preset-env (es6 转 es5)
- 递归所以模块
- 生成最终代码

[手写 webpack 核心原理，再也不怕面试官问我 webpack 原理](https://juejin.im/post/6854573217336541192#heading-2)

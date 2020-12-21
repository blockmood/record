## react setState 同步和异步

> isBatchingUpdates = false 标志位

凡是由 react 合成事件触发的 都会触发 batchUpdates 函数，把 isBatchingUpdates 设置为 true , 把组件放入到 dirtyComponet 队列，然后直接遍历组件执行更新 （willReciveComponents）等流程

### 为什么

因为 React 更新是基于事务的 （ Transaction）， Transaction 就相当于给目标执行函数包裹了一层，加上前置的 hook 和后置的 hook，再搭配 isBatchingUpdates 这样的标志位，就可以实现整个函数调用栈内多次调用 setState 放到同一的队列，最后统一批量处理。

为什么 setTimeout 却不起作用呢 因为绕过了事务 ，react 管控不到。

### React.useMemo()

```
const test = React.useMemo(() => xxxx ,[])
```

某个值改变之后才执行某个函数，父子组件，父组件 render,子组件函数一直 render，可通过[]优化执行函数。

## Hooks 的好处

> 逻辑复用更加简单 通过对象 {} 解构的方式

> useState useEffect 虽然依赖组件，但是可以在组件外部定义 这是 class compoent 做不到的,无法在外部声明 state 和 componentDidMount

注意: render props 和 Hoc 也可以做到，但是 hooks 的代码量更少

## 缺点

> 必须清楚 useCallback 等的参数或者改变时机

> 状态不同步(函数的运行是独立的,变量保存在独立的函数作用域中)

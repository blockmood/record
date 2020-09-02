## 通用版柯里化

```
function curry(fn){
  let args = []
  return function temp(...newArgs){
    if(newArgs.length){
      args = [
        ...args,
        ...newArgs
      ]
      return temp
    }else{
      let val = fn.apply(this,args);
      args = []
      return val
    }
  }
}
```

## componse 实现

```
const compose = (...funcs) => {
  return initialVal => {
    return funcs.reduceRight((a,b)=>b(a),initialVal)
  }
}
```

## pipe 实现

```
const pipe = (...funcs) => {
  return initialVal => {
    return funcs.reduce((a,b)=>b(a),initialVal)
  }
}
```

## 通用版柯里化

```
function curry(fn){
  let args = []
  return function temp(...newArgs){
    if(args.length){
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

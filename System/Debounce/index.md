## 防抖

```
function debounce(fn,await){
  var timer = null
  return function(){
    var context = this,args = arguments;
    if(timer){
      clearTimeout(timer)
      timer = null
    }
    timer = setTimeout(()=>{
      fn.apply(context,args)
    },await)
  }
}
```

## 节流

```
function throttle(fn,await){
  const initialTime = +new Date()
  return function(){
    var context = this,args = arguments;
    const nowTime = +new Date()
    if(nowTime - initialTime >= await){
      fn.apply(context,args)
      initialTime = +new Date()
    }
  }
}
```

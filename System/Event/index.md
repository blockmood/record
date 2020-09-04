## 发布订阅

```
var event = {
  list:{},
  on(key,cb){
    if(!this.list[key]){
      this.list[key] = []
    }
    this.list[key].push(cb)
  },
  emit(){
    let key = [].shift.call(arguments),
      fns = this.list[key]
    fns.forEach(fn =< {
      fn.apply(null,arguments)
    }>)
  },
  remove(key,cb){
    if(!key){
      return
    }
    if(!fn){
      this.list[key] = []
    }
    let fns = this.list[key]
    fns.forEach((fn,index) => {
      if(fn == cb){
        fns.splice(0,index)
      }
    })
  }
}
```

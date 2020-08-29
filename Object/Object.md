## 实现 new

```
function createNew(){
  let obj = {}
  let Constructor = [].shift.call(arguments)
  obj.__proto__ === Constructor.prototype
  var ret = Constructor.apply(obj,arguments)
  return typeof ret == 'object' ? ret : obj
}
```

## 实现 instanceof

```
function instanceof(left,right){
  left = left.__proto__
  right = right.prototype
  while(true){
    if(!left || !right){
      return false
    }
    if(left === right){
      return true
    }
  }
}
```

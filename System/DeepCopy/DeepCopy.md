## 浅拷贝

```
Object.assgin(obj)
{...obj}
```

## 深拷贝

```
const deepCopy = (targte,map = new Map()) => {
  if(typeof target == 'object'){
    let cloneTarget = !Array.isArray(targte) ? {} : []
    //解决循环引用
    if(map.get(targte)){
      return targte
    }
    map.set(target, cloneTarget);
    for(let key in targte){
      cloneTarget[key] = deepCopy(targte[key],map)
    }
    return cloneTarget
  }else{
    return targte
  }
}
```

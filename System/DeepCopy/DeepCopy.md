## 浅拷贝

```
Object.assgin(obj)
{...obj}
```

## 深拷贝

```
const deepCopy = (targte,map = new Map()) => {
  if(typeof target == 'object'){
    let cloneObj = !Array.isArray(targte) ? {} : []
    //解决循环引用
    if(map.get(targte)){
      return targte
    }
    for(let key in targte){
      cloneObj[key] = deepCopy(targte[key],map)
    }
  }else{
    return targte
  }
}
```

## 原生 map 实现

```
function mapArr(arr,callback){
    if(!Array.isArray(arr) && typeof callback !== 'function') return
    let result = [];
    for(let i=0;i<arr.length;i++){
        result.push(callback(arr[i],i,arr))
    }
    return result
}
```

## 原生 filter 实现

```
function filter(arr,callback){
    if(!Array.isArray(arr) && typeof callback !== 'function') return
    let result = [];
    for(let i=0;i<arr.length;i++){
        if(callback(arr[i],i,arr)){
            result.push(arr[i])
        }
    }
    return result
}
```

## 原生 reduce 实现

```
function reduce(arr,reduceCallback,initialValue){
  if(!Array.isArray(arr) || !arr.length || typeof reduceCallback !== 'function'){
    return []
  }else{
    let hasInitialValue = initialValue !== undefined
    let value = hasInitialValue ? initialValue : arr[0]
    for(let i= hasInitialValue ? 1 : 0; i < arr.length;i++){
      value = reduceCallback(value,arr[i],i,arr)
    }
    return value
  }
}
```

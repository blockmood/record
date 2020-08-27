## 原生 map 实现

```
function mapArr(arr,callback){
    if(!Array.isArray(arr)) return
    let result = [];
    for(let i=0;i<arr.length;i++){
        result.push(callback(arr[i],i,arr))
    }
    return result
}
```

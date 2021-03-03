## call 实现

```
Function.prototype.call = function(content){
  content = content || window
  args = [].slice.call(arguments,1)
  content.fn = this
  var result = content.fn(...args)
  delete content.fn
  return result
}
```

## apply 实现

```
Function.prototype.apply = function(content,args){
	content = content || window
	content.fn = this
	var result;
	if(!args){
		result = content.fn()
	}else{
		var newArgs = []
		for(let i=0;i<args.length;i++){
			newArgs.push(args[i])
		}
		result = content.fn(...newArgs)
	}
	delete content.fn
	return result
}
s

```

## bind 实现

```
Function.prototype.bind2 = function(context){
	var args = [].slice.call(arguments,1)
	var self = this
	return function(){
		return self.apply(context,[...args,...arguments])
	}
}

```

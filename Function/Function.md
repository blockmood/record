## call 实现

```
Function.prototype.call = function(content,...args){
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
Function.prototype.apply = function(context){
	context = context || window
	args = [...arguments][1]
	context.fn = this
	const result = context.fn(...args)
	delete context[fn];
	return result
}

```

## bind 实现

```
Function.prototype.bind2 = function(context){
	var args = [].splice.call(arguments,1)
	var self = this
	return function(){
		return self.apply(context,[...args,...arguments])
	}
}

```
## 二者的区别

- 观察者模式是观察者和被观察者直接交互，发布订阅而是由统一的调度中心去处理，实现了解耦，还有就是可以更细粒度的做一些控制，比如发布了的很多事件，但是不想让所有的订阅者都收到，就可以在调度中心去做权限控制等等。

## 发布订阅模式

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
    fns.forEach(fn => {
      fn.apply(null,arguments)
    })
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

function test(a){
  console.log('test',a)
}
event.on('one',test)
event.emit('one',2)

```

## 观察者模式

```
class Subject {
  constructor(){
    this.state = 0;
    this.observers = []
  }
  getState(){
    return this.state
  }
  setState(state){
    this.state = state
    this.notifyAllObservers()
  }
  attach(observer){
    this.observers.push(observer)
  }
  notifyAllObservers(){
    this.observers.forEach(observer => observer.update())
  }
}

class Observer {
  constructor(name,subject){
    this.name = name
    this.subject = subject
    this.subject.attach(this)
  }
  update(){
    console.log(`${this.name} update, state: ${this.subject.getState()}`)
  }
}


let s = new Subject()
let o1 = new Observer('o1', s)
s.setState(1)
```

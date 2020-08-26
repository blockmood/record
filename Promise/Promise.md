## Promise 实现

```
class MyPromise {
    constructor(callback){
        this.status = 'pending'
        this.value = undefined
        this.error = undefined

        this.onFullArray = []
        this.onRejectArray = []

        const resolve = (value) => {
            if(this.status == 'pending'){
                this.value = value
                this.status = 'resolved'
                this.onFullArray.forEach(callback => {
                    callback(this.value)
                })
            }
        }

        const reject = (error) => {
            if(this.status == 'pending'){
                this.error = error
                this.status = 'rejected'
                this.onRejectArray.forEach(callback => {
                    callback(this.error)
                })
            }
        }

        try{
            callback(resolve,reject)
        }catch(error){
            reject(error)
        }
    }

    then(onFulfilled, onRejected){
        if(this.status == 'pending'){
            this.onFullArray.push(()=>{
                onFulfilled(this.value)
            })
            this.onRejectArray.push(()=>{
                onRejected(this.error)
            })
        }
        if(this.status == 'resolved'){
            onFulfilled(this.value)
        }
        if(this.status == 'rejected'){
            onRejected(this.error)
        }
    }
}


new MyPromise((resolve, reject)=>{
    setTimeout(()=>{
        resolve(2)
    },2000)
}).then(res => {
    console.log(res)
})
```

## Promise.all

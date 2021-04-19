```js
function promiseAll(arr){
    return new Promise((resolve,reject)=>{
        if(!Array.isArray(arr)){
            reject(new TypeError('arguments must be an array'))
            return;
        }
        
        let promiseResults=[];
        for(let i=0;i<arr.length;i++){
            (function(i){
                arr[i].then(result=>{
                    promiseResults.push(result);
                    if(i+1==arr.length){
                        resolve(promiseResults);
                    }
                }).catch(error=>{
                    reject(error)
                })
            })(i)
        }
    })
}
```


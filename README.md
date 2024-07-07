# Asynchronous-JavaScript
## async await >> prompt chains >> callback hell
#### Synchronous JavaScript runs code line-by-line, one task at a time ⏳. Each operation waits for the previous one to finish before starting the next 📋➡️📋.

#### Asynchronous JavaScript runs tasks independently ⏩. Some tasks start and finish later ⏳, allowing others to proceed without waiting. This keeps things moving smoothly 🚀.

# Callback
A callback is a function passed as an argument to another function.
```
function sum(a,b){
    console.log("Sum is a callback",a+b);
}

function cal(a,b,sum){
    console.log("Inside cal function");
    sum(a,b);
}

cal(10,20,sum)
```
# Callback Hell
Callback Hell in JavaScript is when multiple nested callbacks make code hard to read and maintain 🔄🔄🔄. It looks like a pyramid of doom 🏔️, making debugging difficult 🐛.
```
function getData(dataID, getNextData){
    setTimeout(()=>{
        console.log("Fetching data",dataID);
        if(getNextData){
            getNextData();
        }
    },2000)
}

//!Callback Hell
getData(1,()=>{
    getData(2,()=>{
        getData(3,()=>{
            getData(4,()=>{
                getData(5,()=>{
                    getData(6,()=>{
                        getData(7,()=>{
                            getData(8,()=>{
                                getData(9,()=>{
                                    getData(10,()=>{})
                                })
                            })
                        })
                    })
                })
            })
        })})})
```

# Promises
 Promises in JavaScript handle async operations more smoothly 🌟. They represent future values 🌱, allowing you to chain actions without nested callbacks, making code cleaner and easier to read 📜.

### JavaScript Promises have three states: Pending (waiting) ⏳, Fulfilled (completed successfully) 🎉, and Rejected (failed) ❌. They help handle asynchronous operations more cleanly.
```
let promise=new Promise((resolve,reject)=>{
    console.log("Inside promise");
})

const promise=()=>{
    return new Promise((resolve,reject)=>{
        console.log("Inside promise");
        resolve("Promise resolved successfully");
        //reject("Promise rejected");
    })
}
let pro=promise();
pro.then((res)=>{
    console.log("Inside then function",res);
})
pro.catch((err)=>{
    console.log("Inside catch function",err);
})
```

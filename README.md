# Asynchronous-JavaScript
## async await >> prompt chains >> callback hell
#### Synchronous JavaScript runs code line-by-line, one task at a time ⏳. Each operation waits for the previous one to finish before starting the next 📋➡️📋.

#### Asynchronous JavaScript runs tasks independently ⏩. Some tasks start and finish later ⏳, allowing others to proceed without waiting. This keeps things moving smoothly 🚀.

# Callback
A callback is a function passed as an argument to another function.
```js
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
```js
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
```js
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
# Promise chaining
Promise chaining in JavaScript means linking multiple `.then()` calls in a sequence 🔗. Each `.then()` handles the result of the previous promise, making code cleaner and easier to follow 📜.
```js
function getData(dataID, getNextData) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            console.log("Fetching data", dataID);
            resolve("success");
        }, 2000)
    })
}

console.log("fetching started");
getData(1)
    .then((res) => {
        return getData(2)
    })
    .then((res) => {
        return getData(3)
    })
    .then((res) => {
        console.log(res);
    })
```
# Async Await
`async`/`await` in JavaScript lets you write asynchronous code like it's synchronous 🧘‍♂️. Use `async` to declare a function and `await` to pause until a promise resolves ⏸️➡️✅.
`await` only works inside `async` functions.
Async functions always return a promise 🌟. Use Await to wait for the promise to resolve.
```js
function getData(dataID, getNextData) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            console.log("Fetching data", dataID);
            resolve("success");
        }, 2000)
    })
}

async function getAllData(){
    await getData(1);
    await getData(2);
    await getData(3);
    await getData(4);
    await getData(5);
    await getData(6);
    await getData(7);
    await getData(8);
    await getData(9);
    await getData(10);
}
```
# IIFE (Immediately Invoked Function Expression)
An IIFE (Immediately Invoked Function Expression) in JavaScript is a function that runs as soon as it's defined 🚀. It helps create a local scope to avoid variable conflicts 🔒.
```js
(async () => {
    await getAllData();
})()
```

---
title:  "Decentralized VueJS apps"
---

Recently I had the chance of using VueJS for a decentralized app. I want to say that I have some experience with React and Svelte but not with Vue, I was like a baby in a new world.
The only reason I used Vue is that you can just drop the script tag inside a html file and you are kinda done.

Here is what I found using vue and ethers.js.

### 1. You can't use `data()` to store the provider or a contract instance

Instead you need to initialize a property in a method like `created()` without declaring it inside the `data()` method. Is weird, I know!

```js
const App = {
    data() {
        year: 100
    },
    created() {
        this.provider = ...initialize provider
    }
}
```

### 2. Use computed properties to create a contract instance

The best way that I found to create contract instances is to use computed properties, initializing them inside `created()` creates useless boilerplate. Computed properties are cached so you don't need to worry about performances.

```js
const App = {
    computed:
        getTokenContract(){
            return new ethers.Contract(...params)
        }
}
```

### 3. Fetching data from the blockchain periodically

The dapp was interacting with a smart contract deployed on BSC, normally BSC has a block time of 3 seconds so every 3 seconds I had to fetch new data. Found a nice way to fetch data periodically without creating memory leaks.

```js
function onBlockRefresh(callback) {
    let handle = setInterval(callback, 6000);

    window.addEventListener('visibilitychange', () => {
        if (document.visibilityState === 'visible') {
            handle = setInterval(callback, 6000);
        } else {
            clearInterval(handle)
        }
    })
}
```

Normally you would use 3000 as interval but I didn't want to query the blockchain that much so I used 6000 as interval instead.

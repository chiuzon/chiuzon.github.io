# Dapps and VueJS - 2021/08/24

Recently I had the chance of using VueJS and Ethers.js to build some decentralized shit. Normally I'm a React/Svelte guy, I never used VueJS for doing any dapps but this time I wanted something more light and easier to setup. Svelte is easier to setup too, but droping ``<script src="https://unpkg.com/vue@next"></script>`` inside a html file is much easier.

Here some interesting things about Ethers.js (It can apply to web3js too) and VueJS :

## 1 You can't use `data()` to store the provider

You actually need to store it without initializing it in `data()`. The problem is that vue wraps the variable inside a proxy object so when you want to call a method you can't because the proxy doesn't have that method, the proxy wrapped object has that method too.

So is better to initialize provider in `created()`

```js
bla = {
    data() {
        year: 100
    },
    created() {
        this.provider = ...initialize provider
    }
}
```

## 2 Don't use `data()` to store your contract instances

As in the previous point, storing contracts inside `data()` properties isn't going to work. But don't worry the solution is basically the same. Create and initialize them in `created()`.

## 3 Use computed to create your contract based on dynamic variables such as `chainId`

Another way to initialize and use contract based on dynamic variables or just use them statically is to use computed properties.

Be aware that if your use a reactive property your computed property is going to update.

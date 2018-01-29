# Return.JS

## What is it?
A library for Node.JS that wraps functions and compares their return types to pre-defined expected returned types

## Why did you make it?
I do drunk programming a lot. It helps me a lot. /shrug

## How can I use it?
### It's simple:

First require the module:
```js
const {Return} = require("returnjs")
```

Second, define a function with some sort of return:
```js
const func = function(hi) {
  console.log(hi)
  return hi ? {} : []
}```

Third. instantiate an object:
```js
const returnFunc = new Return(func)
```

Now comes the fun part. You can easily declare which sort of return types you want. In our case, we want array and object.


### There are three ways you can do this:

The first way:
```js
returnFunc.array
returnFunc.object
const caller = returnFunc.done```
Which basically says that returnFunc can return either an array or object. `.done` gets an anonymous function which calls the main function

The second way:
```js
const caller = returnFunc.array.or.object.done
```
Basically, it's chained commands, saying that it can be either array or object, and to return a wrapper once it's done.

The third way is the way I prefer most, using it directly:
```js
const returnFunc = new Return(function func(hi) {
  console.log(hi)
  return hi ? {} : []
}).array.or.object.done```
This is everything above combined.

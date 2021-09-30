# frontend-quiz

### Q:What are two-way data binding and one-way data flow, and how are they different ?

One way data-binding - its MV pattern, view reacts on model changes and rerenders.
Two way data-binding - is MVVM pattern, view reacts on model changes and model reacts on view changes (example inputs/texareas etc)

### What is asynchronous programming, and why is it important in JavaScript?

Async programming is running operations without blocking the main javascript execution process (timeouts, xhr requests, fetch, promises etc). It helps do not stop user from using the website until async operations ends. So if javascript will execute async operations as sync code, it will freeze the page until operation ends and user will not be able to do anything.

### Create a function that, given a DOM Element on the page, will visit the element itself and all of its descendents (not just its immediate children). For each element visited, the function should pass that element to a provided callback function.

```javascript

const findElementDeeply = (selector, callback, rootElement = null) => {
  if (!rootElement) {
    const element = document.querySelector(selector);
    if (!element) return;
    callback(element);
    findElementDeeply(selector, callback, element);
  } else {
    const elements = rootElement.querySelectorAll(selector);
    if (!elements.length) return;
    for (let element in elements) {
      callback(element);
      findElementDeeply(selector, callback, element);
    }
  }
}
```

### Q: What is the output of the following code?

```javascript
const promise = new Promise((resolve, reject) => {
reject(Error('Some Error Occurred'));
})
.catch(error => console.log(error))
.then(error => console.log(error));
```

it will return Error in catch statement;

### Q: implement in Vue js a button that fade in and fade out a paragraph. (Vue js)

```Vue

<template>
  <div>
    <button @click="triggerParagraphVisibility">trigger</button>
    <transition name="fade">
      <p v-if="isParagraphVisible">lorem ipsum </p>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isParagraphVisible: true
    }
  }
  methods: {
    triggerParagraphVisibility() {
      this.isParagraphVisible = !this.isParagraphVisible
    }
  }
}
</script>
```


### Describe vue’s component instance lifecycle. Describe lifecycle methods, rendering process and how/when the component updates.

When vue`s component injects it has different lifecycle hooks, mostly I use: beforeMount, mounted, beforeCreate, created, destroyed, beforeDestroy, it has much more to detect render changes etc, but I dont remember their names; 
beforeCreate - before instance created
created - instance created and could use data properties
beforeMount - before vue component rendered
mounted - after vue component rendered
beforeDestroy - called before destroying the instance
destroyed - called after destroyed instance

when vue creates component it defines setters and getters for all fields existed in data property. It connects each field to special template parts and updates it each time when vue setter is called

### What will be the output executing the following code snippets ?
```javascript
doStuff(); // 5 + 5 
console.log(a) // error because a was defined as let variable inside brackets
console.log(b) // error because b was defined as var inside function scope

console.log(a) // error because a was defined as let variable inside brackets (if statement)
console.log(b) // 5 because doMoreStuff function is a hoisting scope for b
doMoreStuff(); // same as above

```

### What are the common ways in which you can reduce the load time of a web application?

1. async load components
2. load images only for special devices (image-64x64, image-128x128) etc
3. lazy loading for data
4. server side rendering
5. use cdns
6. cache data

### Q: Got the following exception , please explain the reason and how can we
solve the issue if it’s happened in a local dev environment ?

XMLHttpRequest cannot load
http://localhost:8000/api/getContentByType?category=all. No
'Access-Control-Allow-Origin' header is present on the requested resource. Origin
'http://localhost:5050' is therefore not allowed access


It means that frontend (running on port 5050) could not access remote host because of CORS erros. CORS is a browser technology which prevents doing unregistered requests to remote services to protect websites from hacks. To solve this issue server and client should allow cross origin requests 

### Q. Find unique values in large array [1,5,2,19,100000,5,19,5,...] in the most efficient way

Do the hash table:

```javascript
const hashTable = {}
array.forEach(item => {
  if (!hashTable[item]) {
    hashTable[item] = true;
  }
})
return Object.keys(hashTable);
```

### Q: Name some benefits of using webpack ?

1. easy to use and configure
2. can optimize bundle size
3. live reload, adding hash name to bundle
4. tree shaking

### Q: What is a State Management pattern? And how is it used in modern javascript frameworks ?
State management or state machine patters is a pattern which help to connect different parts of application by using simple functions to update state and state

There are couple of state management frameworks in javascript, like ngRx, Redux, Mobx, Vuex. Usually SPA applications use it for sharing global application data between components, share module data between subcomponents, sometimes developers move business logic into state and try to avoid services or logic in components and make them stateless

### Q: What is the difference between padding and margin?

padding is an inside space between content and border, adding padding makes element bigger (without using box sizing)
margin is an outside space between content and border

### Q: Define the key features of the bootstrap framework

1. good documentation 
2. easy to build startups, POC applications. it saves money/time
3. good grid system to use even if project does not use bootstrap components


### Q: What will be the output of the following code snippet ?
both will be 'ford' because let cat2 = car1 does not create a new object, it creates a link to object car1

### Q: Explain the difference between mutable and immutable objects and give an example of an immutable object in JavaScript?
immutable object does not change their properties after using 
mutable changes their properties after using;

mutable => splice function, Date instance with methods setDate etc, it changes current instance and does not returns new one
immutable => map, slice, filter, every, sort, every clear function



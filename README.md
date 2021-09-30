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
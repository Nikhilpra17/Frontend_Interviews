-  **Browser**:

    -  this === window: true in global context.

    -  globalThis === window: true.

-  **Node.js**:

    -  this: Refers to the module exports (empty {} at the top level). // VERY FREQUENT ASKED INTERVIEW QUESTION

    -  global: Node.js global object.

    -  globalThis: Standardized global object (equivalent to global).

---
### Logic of why 'This' works in Node.js
**What Happens in Node.js?**

When you write a JavaScript file and run it in Node.js, Node **does not execute the code directly**. Instead, it wraps your code in a special function called the **module wrapper**. Think of it like this:

``` ruby
(function(exports, require, module, __filename, __dirname) {
  // Your code goes here!
});
```

-  Inside this wrapper function, this refers to the **module exports object**. This is an empty object {} by default because that's what a new module starts with.

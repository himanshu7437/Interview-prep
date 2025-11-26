# ✅ **PART 2 — JavaScript (Deep Interview Answers)**

---

# ⭐ **3. JavaScript (New Questions — Deep Answers)**

---

## **A. Fundamentals**

---

### **1. What is the difference between `var`, `let`, and `const` beyond hoisting?**

In an interview I would say:

“Beyond hoisting, the biggest differences are scope and mutability.

* `var` is **function-scoped** and allows **re-declaration and re-assignment**, which often causes bugs.
* `let` is **block-scoped**, cannot be re-declared, but can be re-assigned.
* `const` is also **block-scoped**, but it cannot be re-assigned.
  However, objects declared with const **can still have their properties mutated**, because only the binding is constant, not the value itself.

`let` and `const` avoid most of the problems caused by `var`, which is why modern JavaScript heavily prefers them.”

---

### **2. What is lexical scope?**

“Lexical scope means the scope of a variable is determined by **where it is written** in the code, not where it is called.
Inner functions always have access to variables defined in their outer scopes. This is the foundation for closures.”

---

### **3. What is “strict mode” in JavaScript?**

“Strict mode enforces a cleaner version of JavaScript by preventing silent errors.

It:

* disallows using undeclared variables
* makes `this` undefined in functions (instead of window)
* prevents duplicate parameter names
* disallows deleting variables

It catches mistakes early, which improves code quality.”

Usage:

```js
"use strict";
```

---

### **4. What is the temporal dead zone (TDZ)?**

“TDZ is the period between entering a block and declaring the variable where accessing `let` or `const` causes a ReferenceError.

The variable exists but is uninitialized until its declaration is executed.

This prevents accidental usage before assignment.”

---

### **5. Difference between function declaration and function expression?**

**Function Declaration:**

```js
function add() {}
```

* Hoisted entirely
* Can be used before its definition

**Function Expression:**

```js
const add = function() {};
```

* Not hoisted
* Cannot be used before initialization
* Supports anonymous functions

---

### **6. What is IIFE (Immediately Invoked Function Expression)?**

“A function that runs immediately after it is created.”

```js
(function(){
  console.log("Runs instantly");
})();
```

Used for:

* avoiding polluting global scope
* creating private scope
* old JS module patterns

---

### **7. What is prototype chain in JS?**

“Every object has an internal link to another object called its prototype.
If a property is not found on the object, JavaScript looks up the prototype chain until it reaches `null`.

This is the basis of inheritance in JavaScript.”

---

### **8. What is `this` keyword and how does it behave?**

**Depends on how the function is called:**

* Method → `this` = object
* Standalone function → `this` = `undefined` in strict mode, otherwise `window`
* Arrow function → inherits `this` from lexical scope
* Event listener → element that triggered event
* Constructor function → new instance

Interview trick:
“Arrow functions do NOT have their own `this`.”

---

## **B. Operators**

---

### **1. What is optional chaining `?.` ?**

“It safely accesses deep properties without throwing errors.”

```js
user?.address?.street
```

If any part is undefined, expression returns `undefined` instead of error.

---

### **2. What is nullish coalescing `??`?**

“It returns the right-hand value only when the left-hand value is `null` or `undefined`.
Better than `||` when `0` or `""` are valid values.”

```js
const value = input ?? "Default";
```

---

### **3. Difference between `in` vs `hasOwnProperty()`?**

* `in` → checks key in object **and its prototype chain**
* `hasOwnProperty` → checks only object’s own keys

---

## **C. Arrays**

---

### **1. What is `Array.from()`?**

Converts array-like or iterable objects into arrays:

```js
Array.from("hello") // → ["h","e","l","l","o"]
```

Useful for NodeLists, arguments, strings.

---

### **2. Difference `splice` vs `slice`?**

| slice                   | splice                      |
| ----------------------- | --------------------------- |
| Doesn’t modify original | Modifies original           |
| Returns a copy          | Returns removed items       |
| Used for copying        | Used for inserting/removing |

---

### **3. What is array destructuring default values?**

```js
const [a = 10, b = 20] = [5];
console.log(a, b); // 5 20
```

---

### **4. How to flatten nested arrays?**

```js
arr.flat(Infinity)
```

---

### **5. What is `Array.isArray()`?**

Safest way to check if value is array:

```js
Array.isArray([1]) // true
```

---

## **D. Strings**

---

### **1. What is template literal tagging?**

A special function intercepts template literal creation:

```js
function tag(strings, ...values) { }
tag`Hello ${name}`;
```

Used for:

* sanitizing inputs
* i18n
* styling libraries (styled-components)

---

### **2. `replace` vs `replaceAll`**

* `replace` → only first occurrence
* `replaceAll` → all occurrences

---

## **E. Advanced Functions**

---

### **1. What are higher-order functions?**

“A function that accepts another function or returns a function.”

Examples:
map, filter, reduce.

---

### **2. What are pure vs impure functions?**

**Pure:**

* same input → same output
* no side effects

**Impure:**

* depends on external data
* modifies external state

Pure functions improve testability and predictability.

---

### **3. What is debouncing?**

“A technique to delay execution until user stops performing an action.”

Used for:

* searching
* resizing
* input validation

---

### **4. What is throttling?**

“Ensures a function runs at most once in a given timeframe.”

Used in:

* scroll events
* mouse move events

---

### **5. What is memoization?**

“Caching function results to improve performance.”

---

## **F. Async Programming**

---

### **1. Microtasks vs Macrotasks?**

**Microtasks (higher priority):**

* Promises
* queueMicrotask()

**Macrotasks:**

* setTimeout
* setInterval
* DOM events

Microtasks always run before macrotasks.

---

### **2. What is event loop starvation?**

When microtasks keep adding more microtasks, preventing macrotasks from executing.

The page freezes or becomes unresponsive.

---

### **3. What are Web Workers?**

Allow JavaScript to run in background threads.

Used for:

* heavy calculations
* image processing
* large data operations

They prevent UI from blocking.

---

### **4. Difference between promise.all, promise.race, promise.allSettled, promise.any?**

| Method               | Behavior                                          |
| -------------------- | ------------------------------------------------- |
| `Promise.all`        | Resolves when all succeed, fails if any fail      |
| `Promise.race`       | Resolves/rejects with the first completed promise |
| `Promise.allSettled` | Resolves after all complete regardless of success |
| `Promise.any`        | Resolves with first successful promise            |

---

## **G. API / Network**

---

### **1. What are request headers vs response headers?**

Request headers → sent by client
Response headers → sent by server

Examples:

* Authorization
* Content-Type
* Cache-Control

---

### **2. What is CORS?**

“A security feature that blocks cross-origin requests unless the server explicitly allows them.”

Server must set:

```
Access-Control-Allow-Origin: *
```

---

### **3. What is a preflight request?**

A browser sends an **OPTIONS** request before the actual request to check CORS permissions.

---

### **4. REST vs GraphQL?**

| REST                  | GraphQL                           |
| --------------------- | --------------------------------- |
| Multiple endpoints    | Single endpoint                   |
| Over-fetching happens | Client asks exactly what it needs |
| Simple                | More flexible                     |

---

## **H. Objects**

---

### **1. What is immutability?**

Values cannot be directly changed.

Useful for:

* React state
* predictable code

---

### **2. What is prototype inheritance?**

Objects inherit properties from other objects via the prototype chain.

---

### **3. Difference between spread vs Object.assign()?**

Both create shallow copies.

**Spread:**

```js
{...obj}
```

**Object.assign:**

```js
Object.assign({}, obj)
```

Spread is more readable.

---

## **I. Logic Functions**

---

### **1. Implement debounce**

```js
function debounce(fn, delay){
  let timer;
  return function(...args){
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this,args), delay);
  };
}
```

---

### **2. Implement throttle**

```js
function throttle(fn, delay){
  let last = 0;
  return function(...args){
    let now = Date.now();
    if(now - last >= delay){
      fn.apply(this,args);
      last = now;
    }
  };
}
```

---

### **3. Custom map**

```js
Array.prototype.myMap = function(callback){
  let result = [];
  for(let i=0; i<this.length; i++){
    result.push(callback(this[i], i, this));
  }
  return result;
};
```

---

### **4. Custom filter**

```js
Array.prototype.myFilter = function(callback){
  let result = [];
  for(let i=0; i<this.length; i++){
    if(callback(this[i], i, this)) result.push(this[i]);
  }
  return result;
};
```

---

## **J. Browser Working**

---

### **1. What is call stack?**

It stores the execution context of functions.
Works on LIFO — last in, first out.

---

### **2. What is heap memory?**

Where objects and reference types are stored dynamically.

---

### **3. What is reflow and repaint?**

* **Reflow**: recalculating the layout (expensive)
* **Repaint**: updating the visuals (less expensive)

Reflow ALWAYS triggers repaint.

---

### **4. What causes layout thrashing?**

Repeated reading of layout information (like `offsetHeight`) followed by writes (like `style.height`) in a loop.

---

### **5. DOMContentLoaded vs load event**

* `DOMContentLoaded`: HTML parsed, DOM ready
* `load`: All images, CSS, assets loaded
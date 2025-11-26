# ⭐ **3. JavaScript — Deep Interview Answers (Advanced)**

---

## **B. JS Operators**

### **1. `==` vs `===` (Deep Explanation)**

`==` performs **type coercion** before comparison.
`===` compares **type + value**.

Examples:

```js
"5" == 5   // true (string → number)
"5" === 5  // false
null == undefined // true
null === undefined // false
```

🧠 **Interview line:**

> Using `===` avoids unexpected type conversions, so it’s preferred in modern JS.

---

### **2. && and || (Deep — Short-Circuiting)**

* `&&` returns first **falsy** value
* `||` returns first **truthy** value

**Practical Use:**

```js
user && user.name     // check before accessing
name || "Guest"        // default value
```

---

### **3. Type Conversion**

JS implicitly converts:

* Number + String → String
* Boolean in numeric context → 1/0
* `null` → 0 in numeric context
* `undefined` → NaN

---

### **4. Output: `console.log(30 + "30")`**

Output: `"3030"`
Reason: Number converts to string.

---

### **5. null vs undefined (Deep)**

* `undefined` = variable declared but not assigned
* `null` = developer sets it intentionally

---

## **C. Arrays — Deep Interview Answers**

### **1. Ways to define array with specific length**

```js
new Array(10)
Array(10)
```

---

### **2. map vs forEach (Deep)**

| Feature    | forEach             | map             |
| ---------- | ------------------- | --------------- |
| Returns    | nothing (undefined) | new array       |
| Used for   | side effects        | transformations |
| Chainable? | No                  | Yes             |

Example:

```js
arr.map(x => x * 2)   // [2,4,6]
arr.forEach(x => x*2) // undefined
```

---

### **3. Reduce, Map, Filter**

* **map** → transform
* **filter** → select
* **reduce** → accumulate into single value

---

### **4. Accumulator & Index**

In reduce:

```js
array.reduce((acc, curr, index) => ...)
```

* *acc* holds old value
* *curr* is current element

---

### **5. Output: `[1,2,3,4].map(item => item > 2)`**

`[false, false, true, true]`.

---

### **6. Length of `[,,,]`**

Length = **3**
Empty slots, not undefined values.

---

### **7. Compare two arrays**

```js
JSON.stringify(a) === JSON.stringify(b)
```

---

### **8. Merge two strings alternatively**

Example: “abc” + “xyz” → “axbycz”

---

### **9. Slice**

Does NOT modify original array.

---

### **10. Separate numbers & characters**

```js
numArr = arr.filter(x => typeof x === "number");
charArr = arr.filter(x => typeof x === "string");
```

---

## **D. Strings — Deep**

### **1. Why Split & Join?**

To convert:

* string → array → manipulate → back to string

---

### **2. Reverse a string**

```js
str.split("").reverse().join("");
```

---

### **3. Palindrome**

Check:

```js
str === str.split("").reverse().join("")
```

---

## **E. Advanced Functions**

### **1. Currying (Deep Explanation)**

Currying transforms:

```
sum(a,b)
```

into

```
sum(a)(b)
```

Example:

```js
function sum(a){
  return function(b){
    return a + b;
  }
}
```

Uses:

* reusability
* partial application
* functional programming

---

### **2. Infinite Currying**

```js
function add(a){
  return function(b){
    if(b) return add(a+b);
    return a;
  }
}
add(1)(2)(3)(4)() // 10
```

---

### **3. call, apply, bind**

* `call` → invoke with parameters
* `apply` → invoke with array
* `bind` → return new function with bound context

Usage:

```js
fn.call(obj, a, b)
fn.apply(obj, [a,b])
fn.bind(obj)
```

---

### **4. Why use arrow functions?**

* Lexical `this` (inherits from parent)
* Shorter
* No binding issues

---

## **F. Async Programming**

### **1. Promises — deep**

States:

* pending
* fulfilled
* rejected

Example:

```js
new Promise((resolve,reject)=>{ ... })
```

---

### **2. Promise chaining**

```js
doTask()
 .then(res => ...)
 .then(res2 => ...)
 .catch(err => ...)
```

---

### **3. Why Promises?**

Avoid callback hell.

---

### **4. async/await**

Cleaner syntax built on promises.

---

### **5. fetch response & error handling**

```js
try {
  const res = await fetch(url);
  if(!res.ok) throw new Error("Error");
  const data = await res.json();
} catch(err) {
  console.log(err);
}
```

---

### **6. setTimeout vs setInterval**

* setTimeout → runs once
* setInterval → repeats

---

### **7. Output of var & let loop**

```js
for (var i=0; i<15; i++) {
 setTimeout(()=>console.log(i), 1000);
}
```

Output: prints **15** fifteen times → var is function-scoped.

```js
for (let i=0; i<15; i++) {
 setTimeout(()=>console.log(i), 1000);
}
```

Output: **0 to 14** → let is block-scoped.

---

## **G. API / Network**

### **1. API Methods**

* GET: retrieve
* POST: create
* PUT: update/replace
* PATCH: partial update
* DELETE: delete

---

### **2. PUT vs POST**

* POST = create (non-idempotent)
* PUT = update/replace (idempotent)

---

### **3. Status Codes**

* 200 OK
* 201 Created
* 400 Bad Request
* 401 Unauthorized
* 403 Forbidden
* 404 Not Found
* 500 Server Error

---

### **4. Axios vs Fetch**

Axios:

* auto JSON
* interceptors
* better error handling

Fetch:

* built-in
* needs manual `.json()`

---

## **H. Shallow vs Deep Copy (Deep) — Very Important**

### **Shallow Copy**

Copies only first level.

```js
const newObj = {...obj}
```

Nested objects still share reference.

---

### **Deep Copy**

Copies entire structure.

Methods:

```js
structuredClone(obj)
JSON.parse(JSON.stringify(obj))
lodash.cloneDeep(obj)
```

---

## **I. Combined JS Logic**

### **sum(a,b) and sum(a)(b)**

```js
function sum(a,b){
  if(b !== undefined) return a+b;
  return function(c){ return a+c }
}
```

---

## **J. How JS Works in Browser**

* JS engine has call stack
* Browser provides Web APIs
* Event loop moves callbacks to stack

---

# ⭐ **4. ReactJS — Deep Interview Answers**

---

## **A. React Basics**

### **1. What is React?**

React is a **JavaScript library** for building UI using:

* components
* virtual DOM
* one-way data flow

---

### **2. Why is React popular?**

* Fast via Virtual DOM
* Component-based
* Strong ecosystem
* Easy integration
* Backed by Meta

---

### **3. What is JSX?**

JSX = JavaScript XML.

Lets you write HTML-like syntax inside JS.

---

### **4. JSX vs JS**

JSX → requires Babel compilation.
Browser cannot read JSX directly.

---

### **5. Virtual DOM vs Real DOM**

Virtual DOM:

* Lightweight copy of real DOM
* Diffing algorithm
* Fast updates

Real DOM:

* Expensive operations
* Reflow / repaint costs

---

### **6. SPA**

Single Page Application loads one HTML and updates content dynamically.

---

### **7. Functional vs Class Components**

**Functional:**

* cleaner
* hooks
* faster rendering

**Class:**

* older
* lifecycle methods

---

## **B. Props & State**

### **1. What are props?**

Read-only data passed from parent → child.

---

### **2. What is state?**

Internal data of component that changes UI.

---

### **3. Props vs State**

| Props              | State                |
| ------------------ | -------------------- |
| external           | internal             |
| immutable          | mutable              |
| passed from parent | managed in component |

---

### **4. Props drilling**

Passing props across multiple layers unnecessarily.

---

### **5. Context API**

Provides global state without drilling.

---

## **C. Hooks**

### **1. useState**

Used for state management.

---

### **2. useEffect (Deep)**

useEffect has dependency array:

* `[]` → run once (mount)
* `[state]` → run on state change
* `no deps` → run on every render
* cleanup → runs on unmount

---

### **3. useRef**

Stores mutable values or DOM references.

---

### **4. useMemo**

Memoizes expensive calculations.

---

### **5. useCallback**

Memoizes function instances.

---

### **6. Memoization**

Caching results to avoid recomputation.

---

### **7. useLayoutEffect vs useEffect**

* useLayoutEffect runs **before** painting
* useEffect runs **after** painting

---

## **D. Optimization & Rendering**

### **1. React Fragments**

Avoid extra wrapper divs.

---

### **2. Key in lists**

Helps React track which items changed.

---

### **3. Reconciliation**

React compares new VDOM with old VDOM and updates only changed nodes.

---

### **4. Controlled vs Uncontrolled**

Controlled → value controlled by React state
Uncontrolled → DOM manages value (useRef)

---

### **5. HOCs**

A function that takes a component and returns enhanced component.

Used for:

* Logging
* Permissions
* Reuse of logic

---

### **6. Portals**

Render child elements outside parent component DOM.

---

### **7. Strict Mode**

Highlights potential issues in dev environment.

---

## **E. Lifecycle**

### **Class Component Lifecycle (Deep)**

**Mounting:**
`constructor → render → componentDidMount`

**Updating:**
`render → componentDidUpdate`

**Unmounting:**
`componentWillUnmount`

---

### **Functional Components Lifecycle**

Handled in useEffect.

---

## **F. Routing**

### **What is React Router?**

Client-side routing system for SPA.

---

### **How Navigation Works?**

URL changes without full page reload; React shows different components.

---

## **G. Redux — Deep Interview Level**

### **What is Redux?**

A predictable state container.

---

### **Why Redux?**

For:

* large applications
* predictable state transitions
* debugging with DevTools
* centralized store

---

### **Redux Principles**

1. Single source of truth
2. State is read-only
3. Changes via pure reducers

---

### **Redux Flow**

`Dispatch → Reducer → Store Updates → UI Re-renders`

---

### **Redux Middlewares**

Middleware sits between dispatch and reducer.

Examples:

* Redux Thunk
* Redux Saga
* Logger

---

### **Redux vs Context API**

* Context → good for small state
* Redux → for large, complex applications

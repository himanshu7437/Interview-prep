# ✅ **ADVANCED FRONTEND — FULL SENIOR-LEVEL ANSWERS**

# ⭐ PART 1 — **Advanced JavaScript Concepts (Senior-Level)**

---

## **1. JavaScript Execution Context (Deep Answer)**

“When JavaScript runs, it creates an Execution Context.
Each context has 2 phases:

### **1. Creation Phase**

* Memory (variable environment) is created
* Variables get **undefined**
* Functions get their entire function body
* `this` is calculated
* Scope chain is set

### **2. Execution Phase**

* JS runs line by line
* Assigns values
* Executes logic

Global context → stays till page closes
Function context → created per function call
Eval context → rarely used, unsafe

This is the foundation of hoisting, closures, and scope.”

---

## **2. Call Stack + Memory Heap**

“JavaScript engine has two main components:

### **Call Stack**

* Manages execution of functions
* LIFO structure
* Overflow → stack overflow

### **Memory Heap**

* Stores objects, arrays, closures
* Unstructured memory
* Used for dynamic allocation

Understanding this helps optimize memory and prevent leaks.”

---

## **3. Microtasks vs Macrotasks (Extremely Important)**

“JavaScript event loop handles two separate queues:

### **Macrotasks**

* setTimeout
* setInterval
* DOM events

### **Microtasks**

* Promises
* queueMicrotask
* MutationObserver

**Microtasks run BEFORE macrotasks**, even if timeout is 0.
This is why:

```js
setTimeout(() => console.log("timeout"))
Promise.resolve().then(() => console.log("promise"))
```

Output:

```
promise
timeout
```

Because microtasks have higher priority.”

---

## **4. Prototypal Inheritance (Deep Answer)**

“In JavaScript, objects inherit from other objects through the prototype chain.
Every object has an internal `[[Prototype]]` pointer, accessed as `__proto__`.
Functions have a `.prototype` used when creating instances with `new`.

If a property is not found on the object, JS looks up the prototype chain until it reaches `Object.prototype`.”

---

## **5. this binding (Senior-Level Breakdown)**

| Type             | Explanation                                  |
| ---------------- | -------------------------------------------- |
| Default Binding  | `this` = global object                       |
| Implicit Binding | `obj.method()` → `this = obj`                |
| Explicit Binding | `call`, `apply`, `bind`                      |
| new Binding      | `this` = instance created by constructor     |
| Arrow Function   | `this` = lexical (parent scope), no own this |

---

## **6. Memory Leaks in JS**

Caused by:

* Unremoved event listeners
* Global variables
* Closures holding references unintentionally
* Timers not cleared

“Always clean up listeners, intervals, and heavy closures.”

---

## **7. Debouncing vs Throttling**

### **Debounce**

Runs ONLY when user stops typing/clicking for X ms.
Used for:

* Search
* Auto-complete
* Resize

### **Throttle**

Runs at fixed intervals.
Used for:

* Scroll events
* Drag events

---

# ⭐ PART 2 — **Advanced React (Senior-Level)**

---

## **1. How React Fiber Works (Senior Candidate Must Know)**

“React Fiber is the internal engine of React that enables:

* Interruptible rendering
* Prioritization of tasks
* Concurrent rendering
* Smooth user experience

Fiber breaks rendering work into small units so React can pause and resume rendering.
This prevents UI blocking.”

---

## **2. Concurrent Rendering (React 18)**

“Concurrent rendering allows React to prepare UI in the background without blocking the main thread.
React can pause, resume, or throw away work.
This results in smoother updates, especially for large apps.”

---

## **3. useTransition**

“useTransition allows marking some state updates as non-urgent.
React can keep the UI responsive while it updates the background state.”

Example:

```js
const [isPending, startTransition] = useTransition();
startTransition(() => setFilter(query))
```

---

## **4. Suspense + Lazy Loading**

“Suspense lets React wait for something (data, components) while showing a fallback.”

Example:

```js
const LazyComp = React.lazy(() => import('./A'))
<Suspense fallback={<Spinner/>}>
  <LazyComp />
</Suspense>
```

---

## **5. Error Boundaries**

“Error Boundaries catch runtime errors in React UI and prevent full UI crashes.
Implemented using class components.”

---

## **6. Server Components (React 18 feature)**

“Server Components allow React to render components on the server before they reach the client.
They improve performance by reducing bundle size and avoiding unnecessary JS.”

---

## **7. Redux Toolkit + RTK Query (Modern Redux)**

* Removes boilerplate
* Built-in immer for immutable updates
* createSlice and createAsyncThunk
* RTK Query handles caching, automatic refetching, invalidation

“Every senior React dev must know Redux Toolkit.”

---

# ⭐ PART 3 — **Frontend System Design (Mandatory for Senior)**

---

## **1. CSR vs SSR vs SSG vs ISR**

| Rendering | Description                  | Use Case   |
| --------- | ---------------------------- | ---------- |
| CSR       | Render in browser            | SPAs       |
| SSR       | Render on server per request | SEO-heavy  |
| SSG       | Pre-built HTML               | Blogs      |
| ISR       | Rebuild pages in intervals   | E-commerce |

---

## **2. Designing a Scalable SPA (Senior-Level)**

Key design principles:

* Code splitting
* Route-based lazy loading
* Virtualization for large lists
* Caching strategies
* API layer abstraction
* Modular folder structure
* State management separation

---

## **3. Micro Frontends**

“Breaking the frontend into independent deployable apps (micro apps).
Each team works on separate micro-apps.”

Frameworks: Module Federation, Single-SPA.

---

## **4. WebSockets**

Real-time communication for:

* Chat apps
* Multiplayer games
* Live dashboards

Alternate: Server-Sent Events (SSE).

---

## **5. CDN (Senior-Level)**

“CDN delivers assets (JS, CSS, images) from nearest servers.
Improves:

* Latency
* Bandwidth
* Load times
* Reliability”

---

## **6. Caching Strategies**

* Cache-Control headers
* LocalStorage
* IndexedDB
* Service Worker cache
* CDN caching

Patterns:

* Cache-first
* Network-first
* Stale-while-revalidate

---

# ⭐ PART 4 — **Browser + Web API Internals**

---

## **1. Critical Rendering Path**

“The steps the browser takes to render a page:

1. Parse HTML → DOM
2. Parse CSS → CSSOM
3. Combine → Render Tree
4. Layout (positions)
5. Paint (pixels)
6. Composite (layers)

Optimizing these steps improves performance.”

---

## **2. Service Workers**

“They run in background, intercept network requests, enable offline mode, push notifications, caching.”

Used in PWA.

---

## **3. Event Loop in Browser (Deep)**

Event loop prioritizes:

1. Microtasks
2. Rendering
3. Macrotasks

Browsers may render between microtask batches.

---

# ⭐ PART 5 — **Security (Senior-Level)**

---

## **1. XSS**

Injecting JS into the website.
Prevent using:

* Sanitization
* Escaping
* CSP
* Avoid `dangerouslySetInnerHTML`

---

## **2. CSRF**

Forcing user to perform unintended actions.
Prevent using:

* SameSite cookies
* CSRF tokens
* Double-submit cookies

---

## **3. CORS**

“Browser security that restricts cross-domain API calls.”
Fix by configuring server headers.

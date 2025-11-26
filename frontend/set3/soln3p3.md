# ✅ **PART 3 — REACT (Deep Interview Answers)**

---

# ⭐ **4. ReactJS (New Questions — Deep Answers)**

---

## **A. Basics**

---

### **1. What is reconciliation in React?**

“In React, reconciliation is the process of determining what parts of the UI need to be updated when state or props change.
React compares the previous virtual DOM tree with the new one using a diffing algorithm.
Only the nodes that actually changed are updated in the real DOM, making updates very efficient.”

---

### **2. What is the diffing algorithm?**

“The diffing algorithm is React’s optimized way of comparing two virtual DOM trees.

React follows two assumptions:
1️⃣ Two elements of different types produce different trees.
2️⃣ Keys help identify elements across renders.

React performs:

* O(n) comparison
* Skips unchanged subtrees
* Uses keys to match list items

This avoids expensive deep comparisons.”

---

### **3. How does React update the DOM efficiently?**

React uses a 3-step process:

1. Build a new Virtual DOM
2. Diff it with the previous tree
3. Batch minimal DOM updates

The real DOM is touched **only when necessary**, which is why React apps feel fast.

---

### **4. What is declarative UI?**

“It means instead of manually describing each step of how the UI should change (imperative),
we declare what the UI should look like based on the current state.

React handles the DOM changes automatically.”

Example:

```js
isOpen ? <Modal /> : null
```

---

## **B. Props & State**

---

### **1. Why is state immutable in React?**

“If we mutate state directly, React cannot detect changes, so the component will NOT re-render.

React needs a new reference to know something changed.

That’s why we always use:

* `setState` in class components
* `useState` in functional components

These create a new state object, triggering re-render.”

---

### **2. How does state batching work in React?**

“React batches multiple state updates inside events into a single re-render for performance.

Example:

```js
setCount(count + 1)
setCount(count + 1)
```

Runs only **one render**, not two.”

From React 18+, batching also applies to promises, async operations, and timeouts.

---

### **3. What is derived state and why is it discouraged?**

Derived state means copying props into state.

Example:

```js
const [value, setValue] = useState(props.value)
```

Why it’s discouraged:

* Can easily become out of sync
* Causes unnecessary renders
* Can be computed directly during render instead

---

## **C. Hooks**

---

### **1. What are the rules of hooks?**

Two main rules:

1. Only call hooks at top level
2. Only call hooks inside React functions (components or custom hooks)

These ensure consistent hook order, which is crucial for React to track state correctly.

---

### **2. What happens if you break rules of hooks?**

Hooks will execute in the wrong order, causing:

* React to throw errors
* state mismatch
* unpredictable behavior

React’s ESLint plugin catches these mistakes.

---

### **3. What is `useReducer`?**

“A hook that manages complex state using a reducer function instead of multiple useState calls.”

Helpful when:

* multiple state transitions depend on each other
* state logic is complicated
* you want Redux-like patterns without Redux

---

### **4. When to use `useReducer` instead of `useState`?**

Use `useReducer` when:

* State updates are complex
* Multiple actions update the same state
* State transitions follow a predictable pattern

Use `useState` when:

* State is simple
* You want quick, straightforward updates

---

### **5. What is a custom hook & why create it?**

“A custom hook is a reusable function that encapsulates logic that uses other hooks.”

We use them to:

* Share logic across components
* Reduce duplicate code
* Improve readability

Example: useFetch, useLocalStorage.

---

### **6. Why is `useCallback` useless without a dependency array?**

Without dependencies:

```js
useCallback(fn)
```

This regenerates the function on every render.
So it behaves like a normal function—no memoization.

With dependencies:

```js
useCallback(fn, [count])
```

It memoizes the function until dependencies change.

---

## **D. Rendering & Optimization**

---

### **1. What is re-rendering and what triggers it?**

A component re-renders when:

* State changes
* Props change
* Context value changes
* Parent re-renders
* ForceUpdate() is called

Understanding this helps avoid unwanted renders.

---

### **2. What is shallow comparison in React?**

React only compares:

* Primitive values: by value
* Objects/arrays/functions: by reference

React does NOT check deep equality.

---

### **3. What causes infinite re-renders?**

Common reasons:

* Updating state inside render
* Missing dependency array in useEffect
* Creating new objects/functions inside render without memoization

---

### **4. What is `React.memo()`?**

A HOC that prevents unnecessary re-renders.

```js
export default React.memo(MyComponent)
```

It re-renders only when props change (shallow comparison).

---

### **5. How does React handle child components when parent re-renders?**

By default, **all children re-render** when parent re-renders.

To prevent it:

* Use React.memo
* Use useCallback / useMemo
* Lift state appropriately

---

## **E. Lifecycle**

---

### **1. How to mimic componentDidMount in hooks?**

```js
useEffect(() => {
  // code runs once
}, []);
```

---

### **2. How to mimic componentDidUpdate?**

```js
useEffect(() => {
  // runs after updates
});
```

Or using dependencies:

```js
useEffect(() => {
  // runs when count changes
}, [count]);
```

---

### **3. How to mimic componentWillUnmount?**

Return a cleanup function:

```js
useEffect(() => {
  return () => {
    console.log("Component unmounted");
  };
}, []);
```

---

## **F. Routing**

---

### **1. Difference between BrowserRouter and HashRouter?**

| BrowserRouter          | HashRouter       |
| ---------------------- | ---------------- |
| Uses history API       | Uses URL hash    |
| Clean URLs             | Adds `#`         |
| Requires server config | No server config |

---

### **2. What is useNavigate and how does it work?**

A hook for programmatic navigation.

```js
const navigate = useNavigate();
navigate("/home");
```

Uses React Router’s internal history stack.

---

### **3. What are route parameters & how to read them?**

URL:

```
/user/25
```

Route:

```jsx
<Route path="/user/:id" />
```

Read:

```js
const { id } = useParams();
```

---

## **G. Redux**

---

### **1. What is reducer purity and why important?**

Reducers must be:

* pure
* predictable
* return new state
* no side effects

Because Redux relies on immutability and predictability for time-travel debugging and performance.

---

### **2. What is Redux Toolkit and how does it improve Redux?**

Redux Toolkit (RTK) solves all the boilerplate problems:

* Automatic immutable updates using Immer
* createSlice for reducers + actions
* createAsyncThunk for async logic
* avoids huge switch statements

It’s now the official recommended way to use Redux.

---

### **3. What is Immer and why does Redux use it?**

Immer allows “mutating” code while actually producing immutable state behind the scenes.

Example:

```js
state.value++
```

Looks like mutation, but is actually immutable.

---

### **4. Difference between thunk vs saga?**

| Thunk               | Saga                     |
| ------------------- | ------------------------ |
| Simple              | Complex                  |
| Good for small apps | Good for large apps      |
| Uses async/await    | Uses generator functions |
| Part of RTK         | Separate library         |

---

### **5. What is an action creator?**

A function that returns an action object.

---

### **6. What is a selector?**

A function to extract or compute derived data from Redux state.
Used to avoid recalculations and improve performance.

---

## **H. Environment**

---

### **1. What is `.env` file in React?**

Used to store environment variables like:

```
REACT_APP_API_URL=...
```

React only loads variables starting with `REACT_APP_`.

---

### **2. Difference between production and development builds?**

| Development             | Production          |
| ----------------------- | ------------------- |
| Detailed error messages | Minified, optimized |
| Slower                  | Faster              |
| Includes warnings       | No warnings         |

Production build is created using:

```
npm run build
```

---

### **3. What is tree shaking?**

“Tree shaking removes unused code during bundling.
React uses ES modules, so bundlers like Webpack can eliminate dead code automatically.”

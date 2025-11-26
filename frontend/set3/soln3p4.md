# ✅ **PART 4 — ADVANCED FRONTEND (Performance, Security, Architecture, System Design)**

---

# ⭐ **A. Performance Optimization**

---

### **1. What is code splitting in React? Why is it useful?**

“Code splitting means breaking your JavaScript bundle into smaller chunks, so the browser loads only what it needs.
This reduces initial load time and improves performance significantly.”

React uses:

* Dynamic imports
* React.lazy
* Suspense

Example:

```js
const LazyComponent = React.lazy(() => import('./Component'));
```

---

### **2. What is lazy loading?**

“Lazy loading is a performance technique where components or assets are loaded **only when needed**, not upfront.”

Used for:

* Images
* Routes
* Large components

Improves:

* First contentful paint (FCP)
* Time to interactive (TTI)

---

### **3. What is memoization and how does React use it?**

“Memoization stores the result of expensive calculations and reuses it when inputs don’t change.”

React uses memoization through:

* `useMemo` for values
* `useCallback` for functions
* `React.memo` for components

This prevents unnecessary re-renders.

---

### **4. How to reduce unnecessary re-renders in React?**

Possible solutions:

* `React.memo()`
* `useCallback` for stable functions
* `useMemo` for stable values
* Avoid inline objects/functions
* Correct dependency arrays
* Avoid putting everything in state
* Lift state smartly
* Use context carefully (context re-renders children)

---

### **5. What is windowing or virtualization?**

“A technique for rendering only the visible portion of a long list.”

Libraries:

* react-window
* react-virtualized

Useful for:

* Large tables
* Chat applications
* Infinite scrolling

---

### **6. What is the difference between throttling and debouncing?**

**Debounce**
Only run the function after user stops typing/clicking for some time.
Used for:

* Search input
* Autocomplete
* Resize events

**Throttle**
Run the function at a fixed rate, ignoring extra calls.
Used for:

* Scroll events
* Mouse drag
* Window resize

---

### **7. What is the purpose of Web Workers in frontend?**

“Web workers allow running heavy JavaScript in separate background threads so UI remains responsive.”

Used for:

* Encryption
* Large array computations
* Image processing
* Data parsing

---

---

# ⭐ **B. Security (Frontend)**

---

### **1. What is XSS and how to prevent it?**

XSS = Cross-site scripting
Occurs when attackers inject JS into your website.

Prevention in frontend:

* `dangerouslySetInnerHTML` → avoid or sanitize input
* Escape user input
* Use libraries like DOMPurify
* Use proper Content Security Policy (CSP)

---

### **2. What is CSRF?**

Cross-Site Request Forgery = forcing users to perform actions without consent.

Prevent using:

* SameSite cookies
* CSRF tokens
* Double submit cookies

---

### **3. What is HTTPS and why important?**

HTTPS encrypts communication between client and server.
Prevents:

* Man-in-the-middle attacks
* Data tampering
* Credential theft

---

### **4. What is CORS?**

“CORS is a browser security mechanism that controls which domains can access your API.”

Fix by:

* Server adding proper headers
* Using proxy
* Using same domain/subdomain

---

### **5. Why shouldn’t we store tokens in localStorage?**

Because:

* Vulnerable to XSS attacks
* Tokens can be stolen

Better options:

* HttpOnly secure cookies
* Token rotation

---

---

# ⭐ **C. Architecture / Patterns**

---

### **1. What is component composition in React?**

“A pattern where small, reusable components are combined to build complex UIs.”

Better than inheritance.

Example:

```jsx
<Layout header={<Header />} footer={<Footer />} />
```

---

### **2. What is Presentational vs Container Components?**

| Presentational | Container       |
| -------------- | --------------- |
| UI only        | Logic only      |
| Functional     | Often use hooks |
| Stateless      | Stateful        |
| Reusable       | App-specific    |

Modern React replaces this pattern with custom hooks.

---

### **3. What is controlled vs uncontrolled state at the architecture level?**

Controlled:

* State fully managed by React
* UI → always depends on state

Uncontrolled:

* DOM maintains the state
* Accessed via refs

Controlled is preferred because:

* predictable updates
* easier debugging
* easier validation

---

### **4. What is lifting state up?**

“Moving shared state to the nearest common parent so components can share data.”

Prevents duplicated state across siblings.

---

### **5. What is prop drilling and how to avoid it?**

Prop Drilling = Passing data through multiple levels unnecessarily.

Solutions:

* Context API
* Redux
* Zustand/MobX/RTK Query
* Custom hooks

---

### **6. What is Separation of Concerns in React?**

Separate:

* UI
* Logic
* Data fetching
* State management

Tools:

* Custom hooks for logic
* Redux/RTK for global state
* Components for UI

---

---

# ⭐ **D. System Design for Frontend**

---

### **1. What is CSR, SSR, SSG, and ISR?**

| Method  | Description                         | Examples              |
| ------- | ----------------------------------- | --------------------- |
| **CSR** | Renders in browser                  | React SPA             |
| **SSR** | Server renders HTML                 | Next.js               |
| **SSG** | Static HTML generated at build-time | Next.js static export |
| **ISR** | Regeneration after X seconds        | Next.js ISR           |

---

### **2. When to use SSR?**

Use SSR when you need:

* SEO
* Dynamic content
* Faster first paint
* Personalized data

---

### **3. What is hydration?**

“Hydration is the process where React takes server-rendered HTML and attaches event listeners to make it interactive.”

Used in SSR/SSG apps.

---

### **4. What is a CDN and why used in frontend?**

CDN = Content Delivery Network

Benefits:

* Faster load time
* Caching
* Reduced server bandwidth
* Improved reliability

Used for:

* Images
* JS bundles
* Fonts
* Videos

---

### **5. What is caching and its types?**

Types:

* Browser cache
* Service worker cache
* CDN cache
* Memory cache
* IndexedDB cache

Benefits:

* Faster load
* Fewer API calls
* Offline support

---

### **6. What is a Service Worker?**

“A script that runs separately from the main thread and enables offline support, caching, background sync, and push notifications.”

Used in PWA.

---

### **7. What is a PWA (Progressive Web App)?**

PWA behaves like a mobile app but installed via browser.

Features:

* Offline mode
* Background sync
* Push notifications
* Home-screen install
* Faster performance

---

### **8. Explain how the browser renders a page.**

Steps:

1. HTML → DOM
2. CSS → CSSOM
3. DOM + CSSOM → Render Tree
4. Layout → positions
5. Paint → draw pixels
6. Composite → final display

Optimizing these steps improves performance.

---

### **9. What is preloading and prefetching?**

**Preload** → load now (high priority)
Used for critical assets like fonts.

**Prefetch** → load in background (low priority)
Used for future navigation.

---

### **10. What is bundle size and how to reduce it?**

Methods:

* Tree shaking
* Code splitting
* Lazy loading
* Minification
* Gzip/Brotli compression
* Removing unused polyfills
* Using CDN
* Avoiding large libraries


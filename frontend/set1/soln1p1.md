# ⭐ **1. HTML — Deep Interview Answers**

## **A. HTML Basics**

### **1. Inline vs Block Elements (Deep Explanation)**

In HTML, every element is either **block-level** or **inline**.

### 🔹 **Block Elements**

* Take full width available.
* Always start on a new line.
* You can set width/height.

**Examples:** `div`, `section`, `p`, `h1–h6`, `ul`, `li`.

### 🔹 **Inline Elements**

* Only take space needed.
* Do NOT start a new line.
* Height/width cannot be set usually.

**Examples:** `span`, `a`, `strong`, `em`, `img`.

### 💬 Interview Add-On

> "Block elements define structure/layout, whereas inline elements are for styling small portions of text."

---

### **2. div vs span (Deep)**

| Property | `<div>`                   | `<span>`             |
| -------- | ------------------------- | -------------------- |
| Type     | Block                     | Inline               |
| Use      | Layout, grouping sections | Styling part of text |
| Width    | Full width                | Only content width   |

**Example:**

* Use `div` for card wrapper
* Use `span` to highlight a word inside a sentence

---

### **3. What are HTML tags?**

They are predefined markup instructions wrapped in `<>` that tell the browser how to render content.

**Example:**
`<h1>Hello</h1>`

Tags include:

* Opening tag
* Closing tag
* Attributes

---

### **4. Empty elements**

Elements that **cannot** contain content and **don’t need** a closing tag.

Examples:
`<br>`, `<hr>`, `<img>`, `<meta>`, `<input>`

---

### **5. Self-closing tags**

XHTML-style empty elements like:
`<img />`, `<input />`

Modern HTML does NOT require `/`.

---

### **6. What is `<meta>`? (Deep)**

`<meta>` provides metadata — information **about** the webpage, not shown visually.

Common uses:

* SEO
* Character set
* Viewport control
* Keywords
* Description for Google search

**Example:**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

---

### **7. What is `<progress>` tag?**

HTML5 tag to show progress of a task like uploads, downloads.

```html
<progress value="30" max="100"></progress>
```

---

### **8. What is `<marquee>` tag?** (Deep)

Deprecated tag used for scrolling text.

---

### **9. scrollDelay attribute**

Controls speed:
Lower value = faster scrolling.

---

## **B. HTML Semantics**

### **1. em vs i**

* `<em>` conveys emphasis (semantic).
  Screen readers stress it.
* `<i>` just italicizes text visually.

---

### **2. strong vs b**

* `<strong>` conveys strong importance (semantic).
* `<b>` simply bolds text.

---

## **C. Lists**

### **Types**

* Ordered list: `<ol>`
* Unordered list: `<ul>`
* Definition list: `<dl>` with `<dt>` and `<dd>`

---

# ⭐ **2. CSS — Deep Interview Answers**

## **A. Basics**

### **1. CSS Box Model (Very Deep)**

Every element is structured like this:

```
+-------------------------+
|        margin           |
|  +-------------------+  |
|  |      border       |  |
|  | +--------------+  |  |
|  | |   padding    |  |  |
|  | | +----------+ |  |  |
|  | | | content  | |  |  |
|  | | +----------+ |  |  |
|  | +--------------+  |  |
|  +-------------------+  |
+-------------------------+
```

### 🎯 Why important in interviews?

Because layout issues usually come from wrong use of margin vs padding.

---

### **2. Padding vs Margin (Deep)**

| Property           | Padding       | Margin                         |
| ------------------ | ------------- | ------------------------------ |
| Location           | Inside border | Outside border                 |
| Affects Background | Yes           | No                             |
| Collapses?         | No            | Yes (vertical margin collapse) |

---

### **3. Border vs Outline**

* Border affects layout & takes space.
* Outline is drawn outside border & doesn’t affect box size.

**Useful for debugging**: `outline: 1px solid red;`

---

### **4. z-index (Deep)**

Controls stacking of positioned elements.

Only works when:

* position is not static (i.e., relative, absolute, fixed)

Higher z-index = element appears on top.

---

### **5. Positioning (Deep Breakdown)**

| Type     | Meaning                                        |
| -------- | ---------------------------------------------- |
| static   | default, no positioning                        |
| relative | moves relative to itself                       |
| absolute | relative to nearest ancestor with position set |
| fixed    | relative to viewport                           |
| sticky   | behaves like relative → fixed                  |

**Sticky example:**
Sticky headers/sidebars.

---

### **6. Universal Selector `*`**

Selects all elements.
Commonly used for reset styles:

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

---

## **B. Visual Effects**

### **1. Shadows**

**Box Shadow:**

```css
box-shadow: 3px 3px 10px rgba(0,0,0,0.3);
```

**Text Shadow:**

```css
text-shadow: 2px 2px 3px black;
```

---

### **2. Image Reflection**

```css
-webkit-box-reflect: below 10px;
```

---

### **3. Overlapping Elements**

Use `position: absolute` or create stacking context with `z-index`.

---

## **C. CSS Animation**

### **Keyframes (Deep)**

Define steps of animation:

```css
@keyframes slide {
  0% { transform: translateX(0); }
  100% { transform: translateX(100px); }
}

.box {
  animation: slide 1s ease-in-out infinite;
}
```

---

# ⭐ **3. JavaScript — Deep Interview Answers (Part 1)**

*(Basic concepts; advanced in Part 2)*

## **A. JS Fundamentals**

### **1. Hoisting (Deep Explanation)**

Hoisting = JavaScript moves **declarations** to the top of their scope during memory creation phase.

Examples:

```js
console.log(a); // undefined
var a = 10;
```

But:

```js
console.log(b); // ReferenceError
let b = 20;
```

### Why difference?

* `var` gets hoisted with default value **undefined**
* `let` and `const` are hoisted but placed in **Temporal Dead Zone**, so accessing them early throws error.

---

### **2. Scope (Deep)**

JS has 3 types of scopes:

* Global
* Function
* Block (for let/const)

**Practical:** Avoid polluting global scope → leads to bugs.

---

### **3. Closures (Very Deep — Important)**

A closure is formed when a function remembers variables from its outer scope even after outer function is finished.

```js
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  }
}

const inc = outer();
inc(); // 1
inc(); // 2
```

**Where used?**

* Private variables
* Debouncing
* Currying
* Memoization
* Event handlers

---

### **4. Event Loop (Deep Explanation)**

JS runs single-threaded, but async tasks run via Web APIs.

Execution model:

1. Call Stack
2. Web APIs
3. Callback Queue
4. Event Loop checks if stack is empty and pushes callback

**This explains why setTimeout runs last.**

---

### **5. JS Single-threaded vs Asynchronous**

JS has **one main thread**, but async tasks are handled by browser APIs (timers, fetch, DOM events).

---

### **6. NaN**

* NaN = Not a Number
* Type = number
* NaN !== NaN

---

### **7. Type of undefined**

`undefined` → type "undefined"

---

### **8. Primitive vs Non-Primitive**

Primitive = immutable values
Non-primitive = objects with dynamic properties

---

### **9. object.freeze()**

Freezes object so values cannot change.

---

### **10. Event delegation**

Instead of adding event listeners to many children, add one to parent.
Uses event bubbling.

---

### **11. Template literals**

Multiline strings + interpolation.

---

### **12. Destructuring**

Extract values from objects/arrays.
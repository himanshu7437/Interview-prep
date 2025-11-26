# ✅ **PART 1 — HTML (Deep Interview Answers)**

---

# ⭐ **1. HTML (New Questions — Answers)**

## **A. Basics**

### **1. What is DOM?**

In an interview:
“The DOM, or Document Object Model, is a tree-like representation of the HTML structure that the browser creates.
JavaScript doesn’t interact with raw HTML—it interacts with this DOM tree.
DOM allows us to:

* Access elements
* Modify attributes
* Change styles
* Add or remove nodes
  It’s basically the bridge between HTML and JavaScript.”

---

### **2. What is HTML5 and what new features it introduced?**

HTML5 is the latest major version of HTML. It introduced:

* Semantic tags: `<header>`, `<footer>`, `<section>`, `<article>`
* Audio & video tags without plugins
* Canvas API for drawing graphics
* Local storage & session storage
* Geolocation API
* Improved form controls (date, color, number etc.)
* Web workers

HTML5 made the web more interactive and powerful without relying on external plugins.

---

### **3. Difference between `<script>` in `<head>` vs end of `<body>`?**

**In `<head>`:**

* Blocks page rendering until script loads.
* Slower perceived performance.

**At end of `<body>`:**

* HTML loads first, script loads last.
* Page becomes interactive faster.
* This is why we usually place scripts at the bottom or use `defer`.

---

### **4. What is the purpose of `<link>` tag?**

Used mainly to load external resources like:

* CSS files
* Icons (favicon)
* Preload or prefetch assets

It does not embed content, it just references it.

---

### **5. What is `contenteditable` attribute?**

It makes an HTML element editable by the user directly in the browser.
Example:

```html
<div contenteditable="true">Edit me</div>
```

Used in text editors, CMS dashboards, note apps etc.

---

## **B. Semantic**

### **1. What is the purpose of semantic HTML?**

Semantic tags describe the *meaning* of content to:

* Browsers
* Screen readers
* SEO engines

Example: `<nav>` clearly represents navigation, `<article>` represents independent content, etc.

Improves accessibility and SEO.

---

### **2. Why should we avoid using too many `<div>` tags?**

Because:

* `<div>` has no semantic meaning
* Makes the structure harder to understand
* Reduces SEO ranking
* Makes accessibility weaker

Always prefer semantic tags when there is a meaningful alternative.

---

### **3. Difference between `<section>` and `<article>`?**

**`<section>`:**

* Groups related content
* Part of a page
* Not standalone

**`<article>`:**

* Self-contained, standalone content
* Can be shared independently

---

### **4. What is `<figure>` and `<figcaption>`?**

Used to group media with its caption:

```html
<figure>
  <img src="image.png">
  <figcaption>This is a caption.</figcaption>
</figure>
```

Improves semantic structure for images, diagrams, charts.

---

## **C. Forms**

### **1. Difference between GET vs POST in forms?**

| GET                    | POST                            |
| ---------------------- | ------------------------------- |
| Data is visible in URL | Data is hidden                  |
| Limited size           | No size limit                   |
| Not secure             | More secure                     |
| Used for fetching data | Used for sending sensitive data |

---

### **2. Use of `required`, `pattern`, `maxlength`?**

* `required` → forces input
* `pattern` → regex validation
* `maxlength` → restricts input length

They help client-side validation without JavaScript.

---

### **3. Difference between `<input type="button">` vs `<button>`?**

**`<button>`:**

* Can contain HTML (icons, spans)
* More flexible
* Default type = "submit"

**`<input type="button">`:**

* No inner HTML
* Used only for triggering JS

---

# ⭐ **2. CSS (Deep Interview Answers)**

---

## **A. Basics**

### **1. What is specificity in CSS?**

Specificity determines which CSS rule wins.

Specificity Hierarchy:

1. Inline styles (1000)
2. IDs (100)
3. Classes, attributes, pseudo-classes (10)
4. Elements (1)
5. Universal selector `*` (0)

Higher specificity overrides lower ones.

---

### **2. What is the cascade?**

CSS stands for Cascading Style Sheets.
The cascade defines how CSS rules are applied based on:

* Importance (`!important`)
* Specificity
* Source order

When two rules conflict, the cascade decides which rule applies.

---

### **3. Difference between class selectors and ID selectors?**

| Class             | ID                 |
| ----------------- | ------------------ |
| Reusable          | Must be unique     |
| Starts with `.`   | Starts with `#`    |
| Lower specificity | Higher specificity |

IDs should be minimized in large apps because they override too much.

---

### **4. What is `box-sizing: border-box`?**

Normally width = content only.
With `border-box`:

```
total width = content + padding + border
```

This avoids unexpected layout shifts.

---

## **B. Layout**

### **1. What is Flexbox?**

A layout system designed for 1-dimensional alignment (row OR column).
It makes alignment, spacing, centering super simple.

---

### **2. Difference between `flex` and `inline-flex`?**

* `flex` → element behaves as block
* `inline-flex` → element behaves as inline but children are flex items

---

### **3. What is CSS Grid?**

2-dimensional layout system.
Used when you need rows + columns both controlled.

---

### **4. Difference between Flexbox and Grid?**

| Flexbox           | Grid                        |
| ----------------- | --------------------------- |
| 1D layout         | 2D layout                   |
| Content-based     | Layout-based                |
| Great for navbars | Great for full-page layouts |

---

### **5. Difference between `display: none` vs `visibility: hidden`?**

| display: none                 | visibility: hidden        |
| ----------------------------- | ------------------------- |
| Removes element from DOM flow | Takes space but invisible |
| No reflow needed              | Causes layout shift       |

---

## **C. Advanced Visual**

### **1. How to create gradients?**

CSS:

```css
background: linear-gradient(to right, red, blue);
background: radial-gradient(circle, red, yellow);
```

---

### **2. Pseudo-classes vs Pseudo-elements?**

| Pseudo-class (`:hover`) | Pseudo-element (`::before`)       |
| ----------------------- | --------------------------------- |
| Represents state        | Represents actual part of element |
| `:hover`, `:focus`      | `::before`, `::after`             |

---

### **3. Difference between `:before` and `::before`?**

`::before` is the correct modern syntax.
`:before` works for backward compatibility.

---

### **4. How to create responsive layouts?**

Using media queries:

```css
@media (max-width: 600px) {
  .box { width: 100%; }
}
```

---

### **5. What is `transform`?**

Used for moving, scaling, rotating:

```css
transform: translateX(50px);
transform: rotate(45deg);
transform: scale(1.5);
```

It doesn’t trigger reflow → better performance.

---

## **D. Animation**

### **1. Difference between transition and animation?**

| Transition       | Animation             |
| ---------------- | --------------------- |
| Requires trigger | Can run automatically |
| Only from → to   | Multiple keyframes    |
| Simpler          | More powerful         |

---

### **2. What is animation-timing-function?**

Controls speed curve. Examples:

* `ease`
* `linear`
* `ease-in`
* `cubic-bezier()`

---

### **3. How to pause animation?**

```css
animation-play-state: paused;
```
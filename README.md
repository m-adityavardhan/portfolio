
---
# ✨ CSS Explanation

This stylesheet defines a responsive, theme-aware UI using CSS variables, custom properties, and modern layout techniques. It’s designed to support both light and dark modes, provide a structured layout, and enhance accessibility and user experience.

---

## 📁 Table of Contents

1. [CSS Variables & Theming](#-css-variables--theming)
2. [Global Styles](#-global-styles)
3. [Light/Dark Mode Switch](#-lightdark-mode-switch)
4. [Typography & Layout](#-typography--layout)
5. [Responsive Design](#-responsive-design)
6. [Components Explained](#-components-explained)

   * Wrapper
   * Main Article
   * Footer
   * Projects
   * Switch Toggle

---

## 🎨 CSS Variables & Theming

All global design tokens are defined in `:root`, making it easy to maintain consistency and apply theming.

```css
:root {
  --base-font-size: 1rem;
  --corners: 24px 0;
  --ld-bkgd: light-dark(var(--platinum), var(--charcoal));
  ...
}
```

✅ Use Case: Enables **light/dark theme**, **typography scaling**, and **uniform colors**.

🧠 Key Concepts:

* `light-dark(lightValue, darkValue)` lets the browser choose value based on the color scheme.
* Variables like `--ld-text` or `--ld-blue` adapt based on the current theme.

📍Used in:

```css
body {
  background-color: var(--ld-bkgd);
  color: var(--ld-text);
}
```

---

## 🌍 Global Styles

Reset and box model inheritance:

```css
*, *::before, *::after {
  box-sizing: inherit;
}
html {
  box-sizing: border-box;
  color-scheme: light dark;
}
```

✅ Ensures consistent layout behavior and color scheme across all browsers.

---

## 🌓 Light/Dark Mode Switch

CSS-only theme switcher using the `:has()` selector.

```css
html:has(#mode-switcher #light:checked) {
  color-scheme: light;
}
html:has(#mode-switcher #dark:checked) {
  color-scheme: dark;
}
```

✅ Automatically applies theme based on radio button selection.

📍Refer to `@layer switch` block and `.radio-switch` styles for custom UI switch implementation.

---

## 📝 Typography & Layout

```css
h1 {
  font-size: calc(var(--base-font-size) * 2.3);
}
h2 {
  text-transform: uppercase;
  letter-spacing: 0.15em;
}
p {
  line-height: 1.5em;
}
```

✅ Uses relative sizing (`rem`, `calc`) for better accessibility and responsiveness.

---

## 📱 Responsive Design

Responsive font and layout updates using media queries:

```css
@media(min-width: 750px) {
  :root {
    --base-font-size: 1.125rem;
  }
}
```

✅ Ensures readability and layout flexibility across screen sizes.

📍Also used in `.main-article`, `.project`, and `.footer-text`.

---

## 🧩 Components Explained

### 1. `.wrapper`

```css
.wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem;
}
```

✅ Centers and constrains content width for readability.

---

### 2. `.main-article`

Grid-based layout for a profile or "About Me" section:

```css
.main-article {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
  text-align: center;
}
```

📍Becomes a 2-column layout on wider screens:

```css
@media(min-width: 750px) {
  .main-article {
    grid-template-columns: 0.7fr 0.3fr;
  }
}
```

---

### 3. `.radio-switch`

Custom toggle switch UI for theme control using pseudo-elements:

```css
.radio-switch label:first-of-type::before {
  background: var(--white);
  border-radius: 100%;
  transition: transform 0.2s ease-in-out;
}
```

✅ Uses `::before` and `::after` to create a sliding switch effect.

---

### 4. `.projects` & `.project`

Layouts for listing multiple project entries:

```css
.projects {
  display: flex;
  flex-flow: column nowrap;
}
.project {
  display: grid;
  grid-template-columns: 1fr;
  gap: 3rem;
  background-color: var(--ld-projects);
  border-radius: var(--corners);
}
```

📍At 850px+, `.project` becomes 2-column:

```css
@media(min-width: 850px) {
  .project {
    grid-template-columns: 1fr 1fr;
  }
}
```

---

### 5. `.icons` & `.social`

Flexible layout for SVG icons (e.g., social links):

```css
.icons {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
  justify-content: center;
}
.social {
  fill: var(--ld-blue);
}
.social:hover {
  fill: var(--marina);
}
```

✅ Interactive icon color transitions with hover effects.

---

## 🧠 Bonus: Utility & Accessibility Considerations

* Uses `font-size` and layout in `rem` for accessibility.
* `object-fit` and `object-position` used in `.main-article img` for responsive cropping:

```css
object-fit: cover;
object-position: 10% 30%;
```

* `text-transform`, `letter-spacing` in headings improves visual hierarchy.

---

## ✅ Summary

This stylesheet leverages:

* CSS Variables for maintainable theming
* Grid & Flexbox for layout
* Media Queries for responsiveness
* CSS-only toggle switch with modern selectors

---

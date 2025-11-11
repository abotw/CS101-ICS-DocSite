---
title: Introduction to SCSS (Sassy CSS)
author: Matt Li
date: 2025-11-10
tags: [scss, css, web, frontend, cs101]
---

# Introduction to SCSS (Sassy CSS)

**SCSS** — short for **Sassy CSS** — is a **CSS preprocessor syntax** that extends the capabilities of regular CSS.  
It allows developers to write **cleaner, more maintainable, and more powerful stylesheets** by introducing programming-like features such as **variables, nesting, mixins, functions,** and **imports**.

SCSS is part of the **Sass (Syntactically Awesome Style Sheets)** family — a project created by Hampton Catlin and developed by Natalie Weizenbaum.  
Today, it’s a standard tool in modern front-end development workflows, widely supported across frameworks like **React**, **Vue**, and **Jekyll**.

---

## 1. What Is SCSS?

**SCSS** is a superset of **CSS3**, meaning every valid CSS file is also a valid SCSS file.  
It compiles down to standard CSS through a **Sass compiler**, allowing browsers to read it normally.

```scss
// Example SCSS
$primary-color: #3498db;

body {
  background: $primary-color;
  color: white;

  h1 {
    font-size: 2rem;
  }
}
````

When compiled, it becomes:

```css
body {
  background: #3498db;
  color: white;
}
body h1 {
  font-size: 2rem;
}
```

---

## 2. SCSS vs Sass vs CSS

|Feature|**CSS**|**Sass (.sass)**|**SCSS (.scss)**|
|---|---|---|---|
|Syntax|Braces `{}` and semicolons `;`|Indentation-based (no braces)|CSS-like (braces + semicolons)|
|Learning Curve|Easy|Moderate|Easy|
|Compatibility|Native to browsers|Requires compiler|Requires compiler|
|Example|`color: red;`|`color: red`|`color: red;`|

> 💡 In practice, **SCSS** is preferred because it feels familiar to CSS developers while offering advanced features.

---

## 3. Why Use SCSS?

SCSS helps you **manage large, complex stylesheets** efficiently.  
It improves **readability, reusability, and consistency**.

### Key Benefits

- **Variables** for consistent color and font usage
    
- **Nesting** to mirror the structure of HTML
    
- **Mixins** to reuse blocks of styles
    
- **Functions** for calculations and logic
    
- **Imports & Partials** for modular organization
    
- **Inheritance** for shared properties among selectors
    

---

## 4. SCSS Variables

Variables in SCSS start with a `$` symbol and store reusable values.

```scss
$font-stack: Helvetica, sans-serif;
$primary-color: #2ecc71;

body {
  font-family: $font-stack;
  color: $primary-color;
}
```

You can easily change the entire site’s color scheme by editing just one variable.

---

## 5. Nesting

SCSS allows **nested selectors**, reflecting the structure of HTML and avoiding repetitive code.

```scss
nav {
  ul {
    list-style: none;
  }
  li {
    display: inline-block;
  }
  a {
    text-decoration: none;
    color: black;
  }
}
```

Compiles to:

```css
nav ul {
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  text-decoration: none;
  color: black;
}
```

> ⚠️ Avoid nesting more than 3 levels deep to prevent overly specific selectors.

---

## 6. Mixins

**Mixins** allow you to define reusable chunks of CSS code.  
You can also pass arguments, similar to functions.

```scss
@mixin button($color) {
  background-color: $color;
  border: none;
  border-radius: 4px;
  color: white;
  padding: 10px 15px;
}

button {
  @include button(#e74c3c);
}
```

This helps you maintain a consistent design system.

---

## 7. Functions and Operators

SCSS provides **functions** for dynamic calculations.

```scss
$base: 16px;

p {
  font-size: $base * 1.25;
}
```

You can also use **built-in functions**, like `lighten()`, `darken()`, `mix()`, etc.:

```scss
$color: #3498db;

button {
  background: lighten($color, 10%);
  border: 1px solid darken($color, 10%);
}
```

---

## 8. Partials and Imports

You can split styles into multiple files for better organization.  
Partial files start with an underscore (`_`), and they won’t compile directly.

Example structure:

```
scss/
  _variables.scss
  _header.scss
  _footer.scss
  main.scss
```

Inside `main.scss`:

```scss
@use 'variables';
@use 'header';
@use 'footer';
```

The compiler combines them into one final CSS file.

> 🔁 In older SCSS syntax, `@import` was used, but modern Sass recommends `@use` for better performance and namespace management.

---

## 9. Inheritance (`@extend`)

The `@extend` directive allows one selector to inherit styles from another.

```scss
.message {
  border: 1px solid #ccc;
  padding: 10px;
}

.success {
  @extend .message;
  background: #2ecc71;
}

.error {
  @extend .message;
  background: #e74c3c;
}
```

This reduces duplication and improves maintainability.

---

## 10. Control Directives

SCSS supports logic with **`@if`**, **`@for`**, **`@each`**, and **`@while`** directives.

```scss
$theme: dark;

body {
  @if $theme == dark {
    background: #222;
    color: white;
  } @else {
    background: white;
    color: black;
  }
}
```

Loops example:

```scss
@for $i from 1 through 3 {
  .item-#{$i} {
    width: 100px * $i;
  }
}
```

Compiles to:

```css
.item-1 { width: 100px; }
.item-2 { width: 200px; }
.item-3 { width: 300px; }
```

---

## 11. Compilation

SCSS needs to be **compiled** into CSS before browsers can read it.  
There are several ways to compile:

### Command Line

```bash
npm install -g sass
sass input.scss output.css
```

### Watch Mode

```bash
sass --watch scss:css
```

### Integration

- **Webpack / Vite**: via `sass-loader`
    
- **Jekyll**: automatic SCSS processing under `_sass/`
    
- **VS Code extensions**: live compilation and preview
    

---

## 12. Example Project Structure

```
project/
├── scss/
│   ├── _variables.scss
│   ├── _mixins.scss
│   ├── _header.scss
│   └── main.scss
├── css/
│   └── main.css
├── index.html
└── package.json
```

You can configure a build script in `package.json`:

```json
"scripts": {
  "build-css": "sass scss/main.scss css/main.css --style=compressed",
  "watch-css": "sass --watch scss:css"
}
```

Then run:

```bash
npm run watch-css
```

---

## 13. Integration with Jekyll

If you’re building a **Jekyll site**, SCSS works seamlessly:

- Put `.scss` files in the `_sass/` directory.
    
- Reference them in your main stylesheet:
    

```scss
@import "variables";
@import "layout";
```

- Add this to your site’s front matter:
    

```scss
---
---
@import "main";
```

Jekyll will automatically compile your SCSS into CSS when you build the site.

---

## 14. SCSS Best Practices

✅ **Use variables** for consistent colors and spacing  
✅ **Limit nesting** to 3 levels  
✅ **Organize with partials** and modular files  
✅ **Use `@use` instead of `@import`**  
✅ **Keep mixins reusable** and not too large  
✅ **Leverage functions** for dynamic calculations

---

## 15. Example: Complete SCSS Snippet

```scss
// _variables.scss
$primary: #007bff;
$radius: 5px;

// _button.scss
@mixin button($bg) {
  background: $bg;
  color: white;
  border-radius: $radius;
  padding: 10px 15px;
  border: none;
}

// main.scss
@use 'variables';
@use 'button';

.btn {
  @include button($primary);
  &:hover {
    background: lighten($primary, 10%);
  }
}
```

Compiled CSS:

```css
.btn {
  background: #007bff;
  color: white;
  border-radius: 5px;
  padding: 10px 15px;
  border: none;
}
.btn:hover {
  background: #339dff;
}
```

---

## 16. Conclusion

**SCSS** revolutionizes how developers write and maintain CSS.  
By bringing programming concepts into styling, it makes code more modular, powerful, and maintainable — especially for large projects.

For students in **CS101-ICS** or anyone learning modern front-end development, mastering SCSS provides a deeper understanding of **modular design**, **style reusability**, and **build automation** — essential concepts in professional web engineering.

---

_Further Reading:_

- [Official Sass Documentation](https://sass-lang.com/documentation)
    
- [Sass Guidelines](https://sass-guidelin.es/)
    
- [Using Sass with Jekyll](https://jekyllrb.com/docs/assets/#sassscss)
    
- [MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS)
    

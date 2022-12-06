# Best-Practices-In-HTML & CSS

## 1. HTML

The main reference for HTML good patterns is [W3C](https://www.w3.org/TR/html/) and [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element), behind these docs we could learn a lot with semantic and another good practices.

- 4.1 [Component Scope](#41-component-scope)
- 4.2 [Language](#42-language)
- 4.3 [Performance](#43-performance)

### 4.1 Component Scope

  

We don't guest the scope of HTML components inside page, so when we start a new component, we should use a semantic tag, like `section` or `article` for example, to be able to starting to use the heading tags by context.


**❌ Bad:**

  

```html

<div  class="component">

<h4  class="title">Title</h4>

<p>Paragraph</p>

</div>

```


**✅ Good:**

  

```html

<section  class="component">

<h1  class="title">Title</h1>

<p>Paragraph</p>

</section>

```

![deexit-kumar-sharma](data/semantic.png)


### 4.2 Language


While defining the language and character encoding is optional, it's recommended to always declare

both at document level, even if they're specified in your HTTP headers. Favor UTF-8 over any other

character encoding.

  

**❌ Bad:**

```html

<!-- bad -->

<!doctype  html>

<title>Hello, world.</title>

```


**✅ Good:**

```html
<!-- good -->

<!doctype  html>

<html  lang="en">

<meta  charset="utf-8">

<title>Hello, world.</title>

</html>

```


  

### 4.3 Performance

  

Unless there's a valid reason for loading your scripts before your content, don't block the

rendering of your page. If your style sheet is heavy, isolate the styles that are absolutely

required initially and defer the loading of the secondary declarations into a separate style sheet.

Two HTTP requests is significantly slower than one, but the perception of speed is the most

important factor.

  
**❌ Bad:**

```html

<!-- bad -->

<!doctype  html>

<meta  charset="utf-8">

<script  src="analytics.js"></script>

<title>Hello, world.</title>

<p>...</p>

```

**✅ Good:**

```html

<!-- good -->

<!doctype  html>

<meta  charset="utf-8">

<title>Hello, world.</title>

<p>...</p>

<script  src="analytics.js"></script>

```


  

## 2. CSS

  

The tips above could be used in any CSS framework or preprocessor, like SCSS, Styled Components and etc

  

- 2.1 [CSS Syntax](#21-css-syntax)

- 2.2 [CSS Declaration Order](#22-css-declaration-order)

- 2.3 [CSS Class Names](#23-css-class-names)

- 2.4 [CSS Good Practices](#24-css-good-practices)

  

### 2.1 CSS Syntax

Keep one declaration per line.
  

**❌ Bad:**

  

```css

.selector-1, .selector-2, .selector-3 {

...

}

```

**✅ Good:**

  

```css

.selector-1,

.selector-2,

.selector-3 {

...

}

```
  

Separate each ruleset by a blank line.

  


  

**❌ Bad:**

  

```css

.selector-1 {

...

}

.selector-2 {

...

}

```

**✅ Good:**

  

```css

.selector-1 {

...

}

  

.selector-2 {

...

}

```
### 2.2 CSS Declaration Order

  

The declarations should be added in alphabetical order.

  


  

**❌ Bad:**

  

```css

.selector {

padding: 5px;

height: 200px;

background: #fff;

margin: 5px;

width: 200px;

color: #333;

border: #333  solid  1px;

display: flex;

}

```

**✅ Good:**

  

```css

.selector {

background: #fff;

border: #333  solid  1px;

color: #333;

display: flex;

height: 200px;

margin: 5px;

padding: 5px;

width: 200px;

}

```
  

### 2.3 CSS Class Names

  

Keep class lowercase and use dashes to separate the classname.

  


  

**❌ Bad:**

  

```css

.pageHeader { ... }

.page_header { ... }

```

**✅ Good:**

  

```css

.page-header { ... }

```
  

The good naming follows a [BEM naming convention](http://getbem.com/introduction/) (Blocks, Elements and Modifiers) to avoid conflicts with other components. If you are using CSS-in-JS like a Styled-Component, you can use BEM if you need to nesting elements inside parent.

  

The main pattern is use single dash to element name, double underline to element block and double dash to style modification.

  

  

**❌ Bad:**

  

```css

.page-header-title { ... }

.page-header-active { ... }

  

.active { ... }

.primary { ... }

```

**✅ Good:**

  

```css

/* Good */

.page-header__title { ... }

.page-header--active { ... }

  

.button--active { ... }

```


Dashes and underline serve as natural breaks in related class. Prefix class based on the closest parent or base class.

  


  

**❌ Bad:**

  

```css

.item-nav { ... }

.link-nav { ... }

```

  
**✅ Good:**

  

```css

.nav { ... }

.nav__item { ... }

.nav__link { ... }

```

Avoid giving too short names for class and always choose meaningful names that provide the class function.

  


  

**❌ Bad:**

  

```css

.s { ... }

.btn { ... }

.ph { ... }

.block { ... }

```

**✅ Good:**

  

```css

.button { ... }

.page-header { ... }

.progress-bar { ... }

```
  

### 2.4 CSS Good Practices

  

Avoid use values like colors, spacing and etc directly in the elements, use variables instead, and it can be CSS variables or some preprocessor variables, always check the context.

  


  

**❌ Bad:**

  

```css

.button {

color: #333;

padding: 16px;

}

```

**✅ Good:**

  

```css

.button {

color: var(--color-primary);

padding: var(--space-sm);

}

```
  

Never use IDs to style elements, always use classes instead.

  


  

**❌ Bad:**

  

```css

#header { ... }

#section { ... }

```

**✅ Good:**

  

```css

.header { ... }

.section { ... }

```
  

Do not style directly the elements, it will create a lot of conflicts, always use classes instead.

  


  

**❌ Bad:**

  

```css

input[type="text"] { ... }

header

section

```

**✅ Good:**

  

```css

.form-control { ... }

.header { ... }

.section { ... }

```
  

Avoid nesting elements, because it decrease performance and increase the specificity of the CSS, always use classes instead.

  


  

**❌ Bad:**


```css

.navbar  ul { ... }

.navbar  ul  li { ... }

.navbar  ul  li  a { ... }

```
  
**✅ Good:**

  

```css

.navbar { ... }

.nav { ... }

.nav__item { ... }

.nav__link { ... }

```

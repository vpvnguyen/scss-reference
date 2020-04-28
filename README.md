SCSS Reference

- Create standard html and css layout
- css to be converted to sass later
- Node / NPM is required to use SASS; converts SASS to CSS
- src: https://blog.bitsrc.io/the-complete-beginners-guide-to-sass-ee8d5278f4c

### What is SASS?

Sass is a CSS preprocessor, a superset of CSS that adds features that aren’t available in regular CSS.
A CSS preprocessor is a language that extends CSS, adds features to CSS and gets compiled into regular CSS. A CSS preprocessor helps developers to write cleaner and easier to understand CSS code.

## Setup

- Create style.css and add css properties
- `npm install --save-dev node-sass` to install node-sass into devDependencies in `package.json`
- Create a script in `package.json` as

```javascript
"scripts" : {
    "sass": "node-sass sass/main.scss css/style.css"
}
```

> Script will compile the `main.scss` into the a css file as `style.css` when ran

- Now, in `main.scss`, you can use SASS to create variables to set certain styles.

```scss
$color-primary: crimson;
.layout {
  background: $color-primary;
}
```

- To enable node-sass to auto compile, add `-w` flag at the end of the script.

```javascript
"scripts" :{
    "sass": "node-sass sass/main.scss css/style.css -w"
}
```

## Variables

> \$variable-name: variable-value

```scss
$color-primary: #55c57a;
$color-secondary: #7ed56f;

.heading-primary {
  color: $color-primary;
  text-align: center;
  margin-top: 10px;
}
.heading-secondary {
  color: $color-secondary;
  text-align: center;
  margin-top: 15px;
}
```

## Nesting

```html
<nav class="navigation">
  <ul>
    <li>Home</li>
    <li>About</li>
    <li>Contact</li>
  </ul>
</nav>
```

```scss
.navigation {
  background-color: yellow;
  padding: 20px;
  ul {
    list-style: none;
  }
  li {
    text-align: center;
    margin-top: 20px;
  }
}
```

## Mixins

```html
<div class="box">
  <div></div>
</div>
```

```scss
@mixin absCenterPosition() {
  /* code */
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

@mixin absCenterPosition() {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

## Functions

```scss
@function divide($a, $b) {
  @return $a / $b;
}
div {
  margin: divide(60, 2) * 1px;
  height: 200px;
  width: 200px;
}
```

## Partials and Import

```scss
// main.scss
@import "header";
```

## Inheritance/Extend

```css
.small-panel,
.big-panel {
  background-color: blue;
  border: 2px solid red;
}
.small-panel {
  width: 70px;
  height: 70px;
}
.big-panel {
  width: 200px;
  height: 200px;
}
```

```scss
%panel {
  background-color: blue;
  border: 2px solid red;
}
.small-panel {
  @extend %panel;
  width: 70px;
  height: 70px;
}
.big-panel {
  @extend %panel;
  width: 200px;
  height: 200px;
}
```

## Ampersand (&)

```html
<button class="btn btn--green">Hello World</button>
```

```css
.btn {
  display: inline-block;
  padding: 5px 8px;
}
.btn--green {
  background-color: green;
}
.btn:hover {
  background-color: transparent;
}
```

```scss
.btn {
  display: inline-block;
  padding: 5px 8px;
  &--green {
    background-color: green;
  }
  &:hover {
    background-color: transparent;
  }
}
```

## Directives

- `@if and @else`

```scss
@mixin text-color($val) {
  @if $val == error {
    color: red;
  } @else if $val == warning {
    color: yellow;
  } @else if $val == success {
    color: green;
  } @else {
    color: black;
  }
}
.heading {
  @include text-color(error);
}
```

- `@for and @while`

```scss
@for $i from 1 through 4 {
  .col-#{$i} {
    width: 100% / $i;
  }
}
```

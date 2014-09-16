# User-agent Style Sheet

Browsers implement some default css rules for different elements. For example, an `h1` tag may have some margin by default. However, different browsers might implement different defaults. It is highly recommended to clear out these defaults for all the elements you use in order to have the same output across all browsers. For example,

```css
  html, body, h1, h2, div, p, ul, li, img {
    margin: 0;
    padding: 0;
    border: 0;
    font: inherit;
  }
```
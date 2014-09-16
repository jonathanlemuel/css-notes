# Pseudo-content

We can inject content into an element with CSS with the :before and :after
pseudo content selectors. This will inject a ☺ into every h1 tag, after any
content that is already inside of it.

```css
h1:after {
  content: "☺";
  display: block;
  color: red;
}
```
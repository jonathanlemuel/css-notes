# Basic CSS Syntax

CSS is how we style the HTML markup we write. CSS works by specifying **attributes** on **selectors**. Here is a simple example:

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- In the HTML -->
    <style>
      selector {
        property: value;
        another-property: anothervalue;
      }
    </style>
    <!-- External stylesheet -->
    <link rel="stylesheet" type="text/css" href="/path/to/css/file.css">
  </head>
  <body>
  </body>
</html>
```

### Example:

```css
header {
  color: blue;
}
```

The `header` selector matches any `header` tag it finds in the DOM; the attribute `color: blue` makes any text wrapped in `header` tags blue. Note that this will match text wrapped in other tags _within_ the header tags as well. For instance:

```html
<header>
  <h1> A blue title! </h1>
</header>
```
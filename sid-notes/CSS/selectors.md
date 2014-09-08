# CSS & You

CSS is how we style the HTML markup we write. CSS works by specifying **attributes** on **selectors**. Here is a simple example:

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

# Be More Specific

Say we want the text inside the `h1` tag above to be pink. CSS is built to allow us to be as specific as we want. For example:

```html
/* CSS */

header {
  color: blue;
}

header h1 {
  color: pink;
}

/* HTML */
<header>
  This text will be blue!

  <h1> This text will be pink! </h1>
</header>
```

Note that the CSS above will match `h1` tags within `header` tags no matter how deep they're nested:

```html
<header>
  This text will be BLUE!

  <section>
    <h1> This text will still be PINK! </h1>
  </section>
</header>
```

There are a whole host of ways to match selectors. For instance, say we only wanted to match top level `h1` tags within the `header` tag (i.e. `h1` children of the `header` tag, but not `h1` grandchildren) We could accomplish this via the `>` immediate child selector:

```html
/* CSS */

header {
  color: blue;
}

header > h1 {
  color: pink;
}

/* HTML */
<header>
  This text will be BLUE!

  <h1> This text will be PINK! </h1>

  <section>
    <h1> This text will be BLUE! </h1>
  </section>
</header>
```

There are a lot of ways to match tags. The table under [Selectors][css3-selectors] gives a comprehensive list of the ways to do so.

# Precedence
Say we have the following CSS:

```html
h1 {
  color: blue;
}

header > h1 {
  color: orange;
}

header h1 {
  color: pink;
}

h1.some-class {
  color: red;
}
```


If we style both the `h1` tag, and the `header h1` combination, how do we know which `h1` tag will get which styling? This problem is resolved via CSS precedence, which is a surprisingly complicated issue: read about it [here][css-precedence].

[css-precedence]: http://www.vanseodesign.com/css/css-specificity-inheritance-cascaade/

# Classes & IDs

## Classes

Classes are ways to group together tags that should be styled similarly. To define a class on a tag, we simply set its `class` property:

```html
<article class="featured">
  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
</article>
```

To match any tag with the `featured` class, we write:
```css
.featured {
  font-weight: bold;
}
```

To match only `article` tags with a `featured` class, we may write:
```css
article.featured {
  font-weight: bold;
}
```

## IDs

IDs, unlike classes, should be used to match a **unique** tag in the DOM. We define IDs just like we define classes:

```html
<article id="important_content">
  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
</article>
```

To match the `important_content` id, we may write:
```css
#important_content {
  font-weight: bold;
}
```

[css3-selectors]: http://www.w3.org/TR/css3-selectors/#selectors

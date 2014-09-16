# Selectors

There are many different ways to select elements. You can use element IDs, classes, pseudo classes, and tag names.

Examples:

|          | HTML                            | CSS selector |
|:-------- |:------------------------------- |:------------:|
| ID       | `<div id="something"></div>`    | `#something` |
| class    | `<div class="something"></div>` | `.something` |
| tag name | `<div></div>`                   | `div`        |


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


# Pseudo-classes

```css
input[type="submit"] { }
/* an input that has attribute of type that equals 'submit' */

a:link { }

a:hover { }
/* selects an a that is currently being hovered over (with mouse) */

a:visited { }

li:first-child { }
/* will select the first li. NOT its children */

li:nth-child(5) { }
/* Selects the 5th li. Counting starts at 1, not 0. */

li:nth-child(even) { }
/* even-index lis. Remember counting starts at 1, so it'll select the second, fourth, etc. */
```
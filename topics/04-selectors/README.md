# Selectors

There are many different ways to select elements. You can use element IDs, classes, pseudo classes, attributes, and tag names.

Examples:

|              | HTML                            | CSS selector              |
|:------------ |:------------------------------- |:-------------------------:|
| ID           | `<div id="something"></div>`    | `#something`              |
| class        | `<div class="something"></div>` | `.something`              |
| tag name     | `<div></div>`                   | `div`                     |
| attribute    | `<input checked>`               | `input[checked]`          |
| attribute=   | `<a href="appacademy.io"></a>`  | `a[href="appacademy.io"]` |
| pseudo-class | `<li></li>`                     | `li:first-child`          |
| pseudo-class | `<li></li>`                     | `li:not(.special)`        |

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

**Do not use id selectors too aggressively**. If you make a mistake
and label multiple items with the same id, you can get unexpected
results. For instance, using `$("#xyz")` will typically return just a
single one of the items with the id `xyz` Only assign an id if the
item really will be unique. Nine times out of ten, a CSS class is a
better way to go.

# Other Useful Selectors

## Attribute Selector

Sometimes it is useful to select elements in CSS based on a particular attribute. CSS provides this capability via the attribute selector, which
follows the following format:

```css
tag[attribute]
```

So if we wanted to style any checked checkboxes
(`<input type="checkbox" checked>`)

```css
input[checked] {
  color: red;
}
```

Attributes may also have values. For example, if we wanted to select links, there wouldn't be much of a point in selecting the ones with an `href` attribute. We can also specify that an attribute should be equal to a certain value, like so:

```css
a[href="http://appacademy.io"] {
  color: red;
}

This would apply the style to any links like the following:

```html
<a href="http://appacademy.io">App Academy</a>
```

This format only matches exact values for an attribute, but there are other
variations than can match only part of an attribute value. For instance,
the following would match links with href values that *start with* http:

```css
a[href^="http"]
```

# Pseudo-classes

Lastly, we have a a special group of selectors called [pseudo-classes][pseudo_class].
[pseudo_class]: https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes

```css
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

## `:not` Selector

Another useful pseudo-class selector is `:not`. It takes as an argument
another selector and will match all elements to which the passed selector
*does not* apply. For example, consider the following HTML:

```html
<div class="regular"></div>
<div class="regular"></div>
<div class="special"></div>
<div class="regular"></div>
```

We could select the third `<div>` by passing a selector that matches the others,
but not the third one, to `:not`:

```css
div:not(.regular) {
  color: blue;
}
```

## Helpful Guide

[The 30 CSS Selectors You Must Memorize][30_selectors]
[30_selectors]: (http://code.tutsplus.com/tutorials/--net-16048)

[css3-selectors]: http://www.w3.org/TR/css3-selectors/#selectors
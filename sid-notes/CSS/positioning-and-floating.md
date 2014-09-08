# Positioning

Another important property one can apply via CSS is the `position` property. `position` has the following options available: `static`, `relative`, `absolute` and `fixed`.

The interesting part of the `position` property is that it does **NOT** cascade! This is unusual. Most properties we set on selectors do cascade down to the tags children, grandchildren, &c. This isn't true of the `position` property.

## Static Positioning
This is the default position type of every element.

## Absolute Positioning

Absolute positioning gives you complete control over where an element is positioned. The downside is that the element will not take up space on the page. Observe:

```html
/* CSS */
section {
  position: absolute;
  background: yellow;
  top: 30px;
  left: 50px;
  width: 100px;
  height: 100px;
}

/* HTML */
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
<section>
  Absolutely positioned!
</section>
```

This produces:

![Absolute](./images/absolute-nospace.png?raw=true)

As you can see, there is text under the absolutely positioned element. It acts as if positioned "above" the page.

An important note: the `top`, `bottom`, `left` and `right` properties of an absolutey positioned element are positioned relative to their first non-statically positioned parent container. For example:

```html
/* CSS */
section {
  margin: 0px auto;
  width: 500px;
  background: yellow;
  position: relative;
}

article {
  background: blue;
  position: absolute;
  top: 10px;
  left: 100px;
}

h1 {
  background: red;
}

/* HTML */
<h1>Outside</h1>
<section>
  <h2>Section</h2>
  <article>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
  </article>
</section>
```

This produces:

![Relative Absolute](./images/relative-absolute.png?raw=true)

The absolutely positioned `article` tag is 10px down and 100px right of the relatively positioned parent `section` tag.

## Relative Positioning
This is probably the most confusing of the position types. This is because `relative` actually means _relative to myself_. For instance, if you give `position: relative` then `top: 10px`, the tag will be moved down 10px from _where it would normally appear_. Moreover, the space it would initially have taken up will **still** be taken up. Many people think `relative` means "relative to my parent container", which is untrue. Observe:

```html
/* CSS */
strong {
  position: relative;
  background: yellow;
  top: 20px;
}

/* HTML */
Lorem ipsum dolor sit <strong>amet, consectetur</strong> adipisicing elit, sed do eiusmod tempor incididunt...
```

This produces:

![Relative top](./images/position-relative.png?raw=true)

Note that if you don't give any `top`, `bottom`, `left`, or `right` properties, `position: relative` does nothing to the element.

# Floating
Floating is a CSS positioning property that is used separately from the `position` attribute discussed above. You should never have both `float` and `position` attributes specified on the same element.

You can think of `float` like images in magazines that have text flowing around them. For example:

```html
/* CSS */
section {
  float: left;
  width: 100px;
  height: 100px;
  background: yellow;
}

/* HTML */
<section></section>
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
```

Produces:

![Basic float](./images/basic-float.png?raw=true)

Floating elements is extremely useful for positioning, because it allows us to align elements horizontally. For example, we may float several elements next to one another:

```html
/* CSS */
nav {
  float: left;
  background: yellow;
  height: 200px;
  width: 75px;
  margin: 20px;
}

section {
  float: left;
  background: pink;
  width: 400px;
  height: 100px;
  margin: 20px;
}

/* HTML */
<nav>Sidebar</nav>
<section>Content Box</section>
```
Produces:

![Float to position](./images/float-position.png?raw=true)

## The Float Gotcha

If an element (parent) contains only floated elements (children), it has zero height! In the next example, the `section` contains only a single `float`ed `nav` tag:

```html
/* CSS */
nav {
  float: right;
  background: orange;
}

section {
  background: blue;
}

/* HTML */
<section>
  <nav>
    Navigation here
  </nav>
</section>
```
Producing:

![The clear problem](./images/clear-problem.png?raw=true)

Sad! Our `section` tag's blue background doesn't come through. The way to fix this is via trick known as the clear fix. We'll use the `:after` pseudo-selector to insert an empty string inside the `section` tag. We'll give it the `clear: both` property. The `clear` property tells an element to fall below any floated elements it would share a line with. Modifying the above CSS with the following:

```html
/* Additional CSS */
section:after {
  content: ""; /* Empty content string */
  clear: both;
  display: table; /* Need this to work properly on IE */
}
```

We get:

![Clearfix](./images/clearfix.png?raw=true)

The empty string forces our `section` tag to have some height.

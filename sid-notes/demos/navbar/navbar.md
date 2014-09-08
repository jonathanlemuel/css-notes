# Prerequisites
Please read **all** of the articles under the CSS heading [here][css-curriculum] before reading this article.

[css-curriculum]: https://github.com/appacademy/css-curriculum

# Building a Basic Navigation Bar
In this demo, we'll walk through how to build a standard navigation bar. Our final product will look something like this:

![Final Result](./images/basically-done.png?raw=true)

The full page can be seen [here][top-nav-page].

[top-nav-page]: http://appacademy.github.io/css-curriculum/navbar

## Semantic HTML
The first thing we'll do is write out our navigation bar in semantic HTML. Let's take a crack:

```html
<header>
  <nav>
    <h1>App Academy Students</h1>

    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">Notifications</a></li>
      <li><a href="#">Messages</a></li>
      <li><a href="#">Settings</a></li>
    </ul>
  </nav>
</header>
```

Nice and semantic. Notice the lack of `div` and `span` tags. Those tags are generic and their use should be minimized. This is what it the above markup looks like:

![Raw HTML](./images/semantic-html.png?raw=true)

Let's do our standard CSS reset, stripping the default styling from all the tags we're using.

```css
html, body, header, nav, h1, ul, li {
  border: 0;
  margin: 0;
  padding: 0;
  font: inherit;
}

/* Removes the bullet points from unordered lists */
ul {
  list-style-type: none;
}
```

![After CSS Reset](./images/post-reset.png?raw=true)

We're almost ready to begin styling our page. The final thing we'll do before diving into CSS is add classes to some of our HTML tags. Styling tags without classes can be dangerous, because a single page will frequently re-use tags; i.e. we may have more than one `nav` tag on the page, but they may not need the same styling. We're choosing the `top` class to identify this header unit. We do not need to add classes to each individual element. We can scope them to their parent class. Thus:

```css
<header class="top">
  <nav class="top-nav">
    <h1>App Academy Students</h1>

    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">Notifications</a></li>
      <li><a href="#">Messages</a></li>
      <li><a href="#">Settings</a></li>
    </ul>
  </nav>
</header>
```

## CSS

Let's start styling our page. Our `header` needs to take up the full width of our page, have a red background, and a dark bottom border.

```css
.top {
  background: #f00;
  border-bottom: 3px solid #333;
}
```

We don't need to specify the `width` property, since `header` is by default a block element which takes up as much horizontal space as possible. Here's what it looks like:

![Header](./images/header-wrap.png?raw=true)

We want the navigation part of our header to be smaller than the full width of the page, as well as centered. We also want it to have left and right borders.

```css
.top-nav {
  width: 900px;
  margin: 0 auto;
  border-left: 3px solid #333;
  border-right: 3px solid #333;
}
```

![Header](./images/navbar-centered.png?raw=true)

Since we want to horizontally align our top-logo and list of links, we'll need to `float` them next to each other. Here's a few wrong ways to do it:

**First wrong way:** Float the top-logo left and give it a width, then float the list items left as well. **Bad because:** We actually want the list items aligned on the right, and forcing them to the right by adjusting the width of another element is hacky.

**Second wrong way:** Float the top-logo left, and the list items right. **Bad because:** The list will align on the right, but in the wrong order! This is because they'll float right _in the order they appear on the DOM_.

**Right way:** Float the top-logo left, float the `ul` right, and float the `li`s left within the `ul`. This gives us all the behaviors we want without being hacky!

```css
.top-nav > h1 {
  float: left;
}

.top-nav > ul {
  float: right;
}

.top-nav > ul > li {
  float: left;
}
```

![Without Clearfix](./images/oops-clearfix.png?raw=true)

AH! What happened? We floated elements inside a block element (our `nav`) without using a clearfix. So let's make our clearfix in a class called `group`, and add it to our `nav` tag:

```css
.group:after {
  clear: both;
  content: "";
  display: block;
}
```

![With Clearfix](./images/yay-clearfix.png?raw=true)

Closer! Let's give everything some room to breathe. I could add `padding` to our `li` elements, but we'd run into a small problem: only the `a` tag is clickable. The padding on the `li` would give us the visual effect we want, but we could only click on the text to navigate to the link. We want to be able to click anywhere near the text and still go to the correct page.

If we try to pad **just** the `a` tag, only horizontal padding will get rendered because our `a` elements are inline. The solution is to make the `a` tags into block elements with padding:

```css
.top-nav > ul > li > a {
  display: block;
  padding: 10px;
}
```

![Padded top-nav](./images/padded.png?raw=true)

Now let's take care of some fonts, colors, and borders:

```css
body {
  font-family: sans-serif;
}

.top {
  background: #f00;
  border-bottom: 3px solid #333;
}

.top-nav {
  color: #fff;
  border-left: 3px solid #333;
  border-right: 3px solid #333;
}

.top-nav > ul > li {
  border-left: 3px solid #333;
}

.top-nav > ul > li > a {
  padding: 10px;
  font-weight: bold;
  text-decoration: none;
  color: #fff;
}
```

![Padded top-nav](./images/basically-done.png?raw=true)

Yay!

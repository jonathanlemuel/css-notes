# Display Types

A special CSS attribute one can give to any selector is `display`. The options for `display` are `inline`, `block`, `inline-block` and `none`.

## Inline
Inline is the display type of most tags that are meant to be interspersed with text. Examples include `a`, `strong`, `span` and `time`.

Inline elements always keep their "line height". This causes properties like `margin` and `padding` to behave strangely. For example, if we write:

```html
/* CSS */
strong {
  background: yellow;
  padding: 10px;
}

/* HTML */
Lorem ipsum dolor sit <strong>amet, consectetur</strong> adipisicing elit, sed do eiusmod tempor incididunt...
```

This produces:

![Inline](./images/inline-padding.png?raw=true)

As you can see, these properties only push other elements away horizontally, not vertically. You cannot specify `height` and `width` properties on inline elements.

_NB_: See how the text in our `strong` tag is bold, even though we did not specify a `font-weight` property in our CSS? This is an example of a User Agent Stylesheet. Most browsers have default styling that is applied to many tags. It is fairly common to clear the UAS in your CSS.

## Block
Block elements differ from inline elements in that they do _not_ respect line height. By default, block elements take up as much horizontal space as possible. Additionally, they **do** respect `width` and `height` properties. Observe, if we use the above example, but change the `display` type of our `strong` tag.

```html
/* CSS */
strong {
  background: yellow;
  padding: 10px;
  display: block;
}

/* HTML */
Lorem ipsum dolor sit <strong>amet, consectetur</strong> adipisicing elit, sed do eiusmod tempor incididunt...
```

This produces:

![Block](./images/block-padding.png?raw=true)

## Inline block
Inline block elements are a combination of the block and inline elements (shocking!). They do remain inline, but they force elements around them to respect both horizontal and vertical space. You can set the `width` and `height` properties of an inline block element.

```html
/* CSS */
strong {
  background: yellow;
  width: 100px;
  height: 50px;
  display: inline-block;
}

/* HTML */
Lorem ipsum dolor sit <strong>amet, consectetur</strong> adipisicing elit, sed do eiusmod tempor incididunt...
```

This produces:

![Inline Block](./images/inline-block.png?raw=true)

## None

`display: none` totally removes the content from the (visual) page. Note that the element is still in the DOM, and viewable from the source of the page, it just isn't rendered.

This produces:

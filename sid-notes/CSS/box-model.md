# The Box Model

_Everything_ rendered on the DOM is a box. Every `header`, `article`, `div` and `article` (along with every other tag!) is a box. Every box has three major properties: `padding`, `border`, and `margin`.

![Box Model](./images/box-model.png?raw=true)

The overall width of a box is given by `border-left + border-right + padding-left + padding-right + content`, where `content` is the inner blue box in the picture. These properties can be specified with CSS, as usual:

```css
header {
  /* The order is ATTRIBUTE: top right bottom left */
  /* That's clockwise, for those you that like clocks */

  padding: 5px 10px 5px 10px;
  margin: 0px 0px 0px 0px;
  border: 1px solid black;
}
```

If you specify `width` in the selector, `border` and `padding` are **added** to the width you specify.

As a demo, open up your inspector in chrome, and navigate to the "Elements" tab. Right click the `head` tag, and click "Edit as HTML". Then, add the following lines:

```html
<style>
  * {
    border: 1px solid red;
  }
</style>
```

To see borders around every box on the page!

## Margin
Margin is the only property out of `margin`, `border`, and `padding` that does _not_ affect the size of the box itself. Instead, margin is the "private space" a box needs around it. For example, if you set `margin-left: 50px` on a tag, then the box that tag renders will have nothing in the 50px to the left of it. The box will 'move itself over' to ensure that this space is respected.

Margin is not additive. This means if two boxes next to each other request 50px of margin, there will be 50px between them, not 100px.

## Padding
Padding lives between the content of a box and the border of a box.

## Border
Border lives between the padding of a box and the margin of a box.

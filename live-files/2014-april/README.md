# CSS Demos

## Demos
- **[Form](./form.html)**: Basic styling of a form with text inputs and a button.
- **[Modal](./modal.html)**: A modal you can hide and show.
- **[Table](./table.html)**: How to style a semantic table. Use for tabular data.
- **[Toggle](./toggle.html)**: A demo of a button toggling visual state using classes rather than inline styles.
- **[Button](./button.html)**: Replacing text with image sprites for a button.
- **[Carrousel](./carrousel.html)**: Creating a carrousel with floats/positioning and jQuery.
- **[Center](./center.html)**: Center a collection of floats, using inline-block.
- **[Click](./click.html)**: Create a grid using floats, changing appearance interactively using jQuery and classes (rather than inline styles).
- **[Page](./page.html)**: A full styled page, with navigation bar using floats, a dropdown absolutely positioned, and a two colum floated layout. Note the semantic use of HTML tags and classes.
- **[Positioning](./positioning.html)**: Position boxes upon boxes with absolute and relative positioning, aditionally showing the power of :hover to allow JavaScript-less interactivity.
- **[Post](./post.html)**: A demo of a styled collection of posts. Uses floats and semantic HTML.
- **[Tag](./tag.html)**: Tag a collection of cats using positioning.
- **[Input](./input.html)**: How to style a hipster input.
- **[Triangle](./triangle.html)**: Make a CSS triangle by hacking border properties.

## Topics to know
- How to use the browser inspector for CSS/HTML
- Semantic HTML
- Classes/ids
- CSS selector precedence
- Default browser styles
- Box model (margin, border, padding, width/height)
- Display block and inline
- Document flow
- Floating and clearing
- Pseudo content (:after/:before)
- Clearfix (use .group)
- Positioning (static, relative, absolute, fixed)
- Pseudo classes (:hover/:active/:focus)
- Box sizing (change the way the box model is calculated)


## Brief notes

#### General
- Push all visual presentation into CSS
- Avoid inline styles

#### Display
- none
- block
- inline

##### Note:
- Block expands to full width of parent container
- Height stretches to fit content inside
- Block elements stack vertically, cannot be next to each other naturally
- Inline follows text flow
- Inline obeys text styling (line-height)

#### Box-model
- width/height
- padding
- border
- margin

##### Note:
- Width/height + padding + border add up total size
- Margin is like private space, collapses
- Margin is see-through, not part of element

#### Selector precedence
1. !important
2. inline styles (example: `<div style="color:green;"></div>`)
3. id
4. class or psuedo-class
5. element or pseudo-element

##### Note:
- The more specific selector wins
- If equally specific, the last declared one wins
- Styles cascade, if not overwritten

#### Floats
- Left or right
- Can be cleared
- Show up at expected space
- Do not stretch height of parent container, they stick out
- All content that follows wraps around, unless cleared
- Used to align block elements next to each other

#### Pseudo elements
- Use element:after { } syntax
- Either after or before
- Acts as inline elements inside element
- Can take any styling
- Needs a declared content property

#### Clearfix
- Clear floats using a pseudo element
- It's a trick! Memorize it, but be able to reason about it
- Prefer a semantic name as `.group` for the class

```css
.group:after {
  content: "";
  display: block;
  clear: both;
}
```

#### Toggle state using classes
- Don't have jQuery inject inline styles
- Put your HTML for various states on the page in advance
- Use classes

## Positioning

#### Document flow
- Top to bottom
- Order of html tag appearance matters

#### Position: static
- Default for each element
- Takes up its normal space in document flow
- No nudging
- No z-index

#### Position: relative
- Shows up like static by default
- Takes up normal space in document flow
- Can be nudged with left/right/top/bottom
- Nudging offset is "relative" to original position in document flow
- Creates a new coordinate system for children that are "absolute"
- Obeys to z-index property

#### Position: absolute
- By default shows up at the place where it should in document flow
- Does not take up space in normal document flow (lifted out)
- Offset coordinates are relative to the closest ancestor that is not positioned static. If none found, then the body element
- Creates a new coordinate system for children that are "absolute"
- Obeys to z-index property
- Margins work but do not collapse
- The box takes up minimal horizontal and vertical space

#### Position: fixed
- By default shows up at the place where it should in document flow
- Does not take up space in normal document flow (lifted out)
- Offset coordinates relative to the window viewport (not document!)
- Stays "fixed" in place
- Not all viewports are the same size, so the box may be off the page, never to be seen
- Use carefully! don't block the window!
- Obeys to z-index property
- Margins work but do not collapse
- The box takes up minimal horizontal and vertical space

#### Z-index
- Visual stacking order of elements
- Just a number (no units)
- Numbers get compared
- The bigger number, the more in front
- Anything with a number is higher than non declared, except for -1, which is behind everything
- Nesting matters (parent container dictates children)
- So, if parent element has a low z-index, and a child has a high value, child does not pop out, because parent still has a low value
- For elements that have no assigned z-index, the order matters, elements declared later in the document are in front visually

## Links
- [HTML (what)](http://simon.html5.org/html5-elements)
- [HTML (mdn)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5/HTML5_element_list)
- [CSS 2.1](http://www.w3.org/TR/CSS21/propidx.html)
- [CSS 3](https://developer.mozilla.org/en-US/docs/CSS/CSS_Reference)
- [CSS Selector Specificity Calculator](http://specificity.keegan.st/)
- [HTML Validator](http://validator.w3.org/)

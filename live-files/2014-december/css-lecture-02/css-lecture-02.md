### General
- HTML is concerned with structuring content
- CSS is responsible for how to present content
- Push all visual presentation into CSS
- Avoid inline style declarations on HTML elements

#### Syntax

```css
selector {
  property: value;
}
```

#### Selector precedence

1. **!important** -> `a { color: red !important }`
2. **inline style** -> `<div style="color:green;"></div>`
3. **id** -> `#cat`
4. **class** or pseudo-class -> `.cats`
5. **element** or pseudo-element -> `h1`

##### Note:

- The more specific selector wins
- If equally specific, the last declared one wins
- Styles cascade, if not overwritten
- Avoid !important, inline styles and id selectors. They do not lead to dry, maintainable code.
- You can apply your styles to multiple selectors at once by separating them by commas: `selector1, selector1 { property: value; }`

#### Inherit

- Setting a property to `inherit` will cause it to take its property value from its parent element
- We leverage inherit to greatly DRY up our styles
- Example: if we set the font property on all `<article>` tags to inherit, then we only need to define the font once on the `<body>` tag and now all articles will be set in the same font.
- Inherit makes sense on properties like `font`, `color`, `text-align`
- It does not make sense on properties like `margin`, `padding`, `border`, `background`. Can you explain why?

#### Rectangles

- All elements are represented as rectangular boxes on a page
- Everything is a rectangle!
- The area a rectangle takes up is determined by:
  - **width/height** of content
  - **padding**
  - **border**
  - **margin**

#### Box-model

- The default way to calculate an element's size is:
  - **width/height** + **padding** + **border**
- In other words, if you set width/height, it is *exclusive* of padding and border. You need to add them to the width/height to get the total size an element takes up on the page.
- This default way of calculating the box model size is called **content-box**

#### Margin

- Margin is like private space, it collapses
- Margin is see-through, not part of element
- Cannot be given background, not part of element
- Weird gotcha: margins push through top and bottom of any direct ancestor elements that do not have a border or padding, or their overflow set to visible

### The Display Property

- Specifies the type of rendering box used for an element
- The bread and butter values of display are:
  - **none**
  - **block**
  - **inline**
- There are several more exotic types such as table and flex

#### Display None

- Turns off the display for the element. The page is rendered as though the element did not exist.

#### Display Block

- Element expands to full width of parent container
- Height stretches to fit content inside
- You can manually override height and width properties
- Block elements stack vertically, cannot be next to each other
  naturally

#### Display Inline

- The default property for display
- Cannot contain block elements
- Inline follows text flow
- Think of inline elements as words that flow in a paragraph, they follow each other, are placed on a baseline, and wrap if they do not fit in the parent container
- Elements take up minimal width and height to accommodate content
- You cannot manually set height and width
- Padding and margin only work sensibly left and right, pushing other inline elements horizontally away
- Vertical padding and margin overflows and is often undesired


#### User Agent Styles
- Browsers (also known as User Agents) have an internal stylesheet
- You see them in action when you have a plain HTML page without any declared styles
- They are sensible defaults, but differ slightly per browser
- This stylesheet is loaded before any of your declared styles

#### Reset
- In order to be intentional about our own styles, we *reset* the properties the User Agent Stylesheet declares.
- This prevents surprises and unexpected conflicts with the styles you write yourself
- We put our reset styles at the top of our stylesheet
- Resets consist of zero-ing out box-model properties and setting color and font properties to inherit
- I prefer to be intentional and list the exact used tags to reset:

```css
html, body, section, article,
h1, h2, p, strong, em, a {
  margin: 0;
  border: 0;
  padding: 0;
  outline: 0;
  font: inherit;
  text-decoration: inherit;
  text-align: inherit;
  color: inherit;
  background: transparent;
}
```
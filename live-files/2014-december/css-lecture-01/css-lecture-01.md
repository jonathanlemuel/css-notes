### General
- HTML is concerned with structuring content
- CSS is responsible for how to present content
- Push all visual presentation into CSS
- Avoid inline style declarations on HTML elements

#### Syntax

```

  selector {
    property: value;
  }

```

#### Selector precedence

1. !important
2. inline styles (example: `<div style="color:green;"></div>`)
3. id
4. class or pseudo-class
5. element or pseudo-element

##### Note:

- The more specific selector wins
- If equally specific, the last declared one wins
- Styles cascade, if not overwritten
- Avoid !important, inline styles and id selectors. They do not lead to dry, maintainable code.

#### Rectangles

- All elements are represented as rectangular boxes
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
- You cannot override height and width
- Padding and margin only work sensibly left and right, pushing other inline elements horizontally away
- Vertical padding and margin overflows and is often undesired
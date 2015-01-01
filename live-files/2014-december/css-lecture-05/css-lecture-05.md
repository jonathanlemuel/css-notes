#### Z-index

- Visual stacking order of elements
- All other things being equal, the order in which elements are declared in a document dictate the visual stacking order. Elements declared later are in front visually.
- Z-index is a way to overwrite the default stacking order.
- Only applies to elements positioned `relative`, `absolute` and `fixed`
- Just a number, no units
- Numbers get compared
- The greater the number, the more in front
- A positive z-index is in front of anything that has no declared z-index, or has a negative z-index
- A negative z-index is behind anything that has no declared z-index
- Nesting matters, setting z-index on a parent container also dictates its children
- If a parent element has a low z-index, and its child has a high
  value, the child does not pop out, as the parent still has a low value

## Positioning

#### Static

- Default for each element
- Takes up its normal space in document flow
- No nudging
- No z-index
- Informally considered as "not positioned"

#### Relative

- Shows up like static by default
- Takes up normal space in document flow
- Can be nudged with left/right/top/bottom
- Nudging offset is "relative" to its original position in document flow
- Creates a new coordinate system for children that are `absolute`
- Cannot nudge conflicting properties `left` and `right` or `top` and `bottom` at the same time
- Allows z-index to be set
- Switching from `static` to `relative` can usually be done without any consequences in layout
- Most often used to contain absolute positioned elements or to set a z-index on an element

#### Absolute

- By default shows up at the position where it should in document flow
- Does not take up space on the page, it is lifted out
- Offset coordinates are relative to the nearest ancestor that is not
  positioned `static`. If none is found, then the window is used
- Creates a new coordinate system for children that are `absolute`
- Allows z-index to be set
- Margins work but do not collapse
- The box of the element will take up minimal horizontal and vertical space, unless overwritten by `width` and `height` properties
- You can set both `left` and `right`, and/or `top` and `bottom` properties at the same time, this will stretch the element and is surprisingly useful

#### Fixed
- Offset coordinates are relative to the window, not the document
- Stays fixed in place to the window, even as the document scrolls
- Not all windows are the same size, so the element may be off the page,
  never to be seen
- Use carefully! Don't block the window!
- Otherwise, behaves the same as `absolute` positioned elements:
  - By default shows up at the position where it should in document flow
  - Does not take up space on the page, it is lifted out
  - Creates a new coordinate system for children that are `absolute`
  - Allows z-index to be set
  - Margins work but do not collapse
  - The box of the element will take up minimal horizontal and vertical space, unless overwritten by `width` and `height` properties
  - You can set both `left` and `right`, and/or `top` and `bottom` properties at the same time, this will stretch the element and is surprisingly useful
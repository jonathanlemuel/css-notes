
#### Pseudo Content

- Used to inject content inside an element
- You can either inject *after* or *before* the present content inside an element
- Acts as inline elements inside element by default
- Can take any styling
- Needs a declared content property
- Content property can be a string or select an element's attribute
- Example of string content:
```css
h1:before {
  content: ":)";
}
```
- Example of attribute content:
```css
a:after {
  content: " (" attr(href) ")";
}
```

#### Floats

- The float property *floats* an element to the left or right side of its parent container
- Used to align block elements next to each other
- A floated element shows up at the expected position
- Takes up minimal vertical/horizontal space to accommodate content
- Does not stretch height of parent container, it sticks out
- All content that follows wraps/flows around, unless cleared
- To tell an element that it cannot wrap around a floated element, you define the `clear` property on it
- Setting `clear` on an element is like it saying: "I refuse to wrap around any floated element, thus I will show up below the floated element."

#### Clearfix
- To make a parent element extend to the full height of all floated elements inside it, we apply the clearfix
- It injects a pseudo element inside the parent container with the clear property
- In doing so this pseudo element will show up below the floated elements
- Since this pseudo element is just a regular element, it will stretch the height of the parent to accommodate it
- We don't want this pseudo element to show up visually, so we just set it to an empty string, effectively making it a 0 height element
- It's a trick! Memorize it, but be able to reason about it
- Prefer a semantic name as `.group` for the class you add to the parent container of the floats

```css
.group:after {
  content: "";
  display: block;
  clear: both;
}
```
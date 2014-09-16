# Selector precedence

Not all selectors are created equal. Some are more 'powerful' than others. Here's the order:

1. `!important`
  - `selector { property: value !important; }`
  - NB: This is not a selector. It only applies to a single style property applied through a rule.
2. Inline styles
  - `<div style="property: value;"></div>`
3. IDs
  - `<div id="some-id"></div>`, then in CSS: `#some-id { property: value; }`
4. Classes (or pseudo classes)
  - `<div class="some-class"></div>`
  - Then, in CSS: `.some-class { property: value; }`
  - Pseudo-class: `input[type="submit"]`
5. Tag name
  - `<div></div>`
  - Then, in CSS: `div { property: value; }`

The `!important` flag should be used very sparsely. For the most part it's only used to overwrite the styles applied by some sort of plugin or widget. For example, Google's reCAPTCHA generates elements on the fly with inline styles. The only way we can overwrite these styles is with the `!important` flag. It should be reserved for those kinds of situations.

One of the main reasons CSS was invented was to separate out the decorative/ornamental rendering logic from actual content, so that rules out inline-styles. It also makes your styles much less dynamic and flexible. ie: having different styles for mobile devices and computer screens would be impossible.

We prefer to use classes for the most part, sprinkling in some pseudo-class and tag-name rules, and just apply different classes to apply styles.


## Specificity

- Selector chaining: Selectors can be chained to create more specific selectors.
  - For example `div.content` would select divs with class `content`. This is more specific than just specifying `.content`.
- Descendants: You can specify that a selector must be a descendant of another element.
  - `section.posts article.post` selects all the `article`s with class `post` that are descendants of any `section` with class `posts`.
  - This is more specific than just specifying `article.post`.
- Direct descentants: Specify that an element must be a direct descentant of another element.
  - i.e.: `#posts > article` selects all the `article` elements that are immediately nested under an element with ID `posts`.
  - This is more specific than `#posts article`

For exact specificity level, you can use a [specificity calculator][spec_calc]
[spec_calc]: http://specificity.keegan.st/
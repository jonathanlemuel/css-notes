# Binary Display Toggle

This is pretty simple concept, but it's extremely powerful. The end goal is to
toggle between the display of two things. For example, friending buttons on a
facebook-like app.

We should have both the 'Add friend' and 'Remove friend' buttons on the page
and only display the approriate one. We'd probably to the friendind over ajax
and upon successful friending, hide the 'Add friend' button and display the
'Remove friend' button instead.

## Naive approach

Continuing with the friending buttons example, we could have a container that
wraps both buttons to which we would give the classes `can-friend` and
`can-unfriend` and we `display: block;` and `display: none;` the buttons
appropriately based on the presence of these classes.

```css
.button-container.can-friend .friend {
  display: block;
}

.button-container.can-friend .unfriend {
  display: none;
}

.button-container.can-unfriend .friend {
  display: none;
}

.button-container.can-unfriend .unfriend {
  display: block;
}
```

Then in the AJAX success callback after clicking on one of these buttons, we'd do:

```javascript
$('.friend').on('click', function (event) {
  ...

  $.ajax({
    ...
    success: function () {
      $('.button-container').removeClass('can-friend');
      $('.button-container').addClass('can-unfriend');
    }
  });

});
```

This isn't terrible, but it introduces a code smell. The problem is that for
the display logic to work properly, it depends too much on us remembering we
need to toggle these two different classes, which we might forget and toggle
individually. So, it's not impossible for us to mess up and add both classes,
which in this case would result in both buttons displaying. No bueno.

## Use the force, Luke!

We have two different states we're toggling between. So, the naive approach
represents these two different states with the *presence* of two different
classes (the only deciding factor of whether a button displays is the presence
of its respective class on the parent container).

However, we can also use the absence of a class as a information, so this
binary data we need (whether to display one button or the other), should be
inferable from the presence or absence of one single class on the container.

Let's try it. We'll start by just displaying or hiding the `.friend` button
based on the presence or absence of the `is-friend` class on the container:

```css
.button-container.is-friend .friend{
  display: none;
}

.button-container .friend {
  display: block;
}
```

There's a little more going on in this CSS than meets the eye. We're relying on the specificity of the two different rules. So, when the container **doesn't** have the `.is-friend` class, the `.friend` button will be `display: block;`. But, when the container **does** have the `.is-friend` class, the top rule applies, and because it is more specific than the other one, it will overwrite the `display` property for the button.

Let's also write the (opposite) rules for the `.unfriend` button:

```css
.button-container.is-friend .friend {
  display: block
}

.button-container .friend {
  display: none
}
```

Pretty awesome, huh?

## Combine them, you can

```css
.button-container.is-friend .friend, .button-container .friend {
  display: block
}

.button-container .friend, .button-container.is-friend .friend {
  display: none
}
```

May the force be with you.
# What are  Image Sprites?

An image sprite is a collection of images all "pasted together" on a single canvas, and served up as one file. [Here][sprite-ex] is an example.

Image sprites are a good idea, because the client only has to submit a single GET request for the image file, rather than a GET request per image, greatly decreasing the load on our servers.

[sprite-ex]: ./sprite_example.png

## Using Image Sprites

In this demo, we'll show you how to use image sprites effectively. We'll use [this sprite][cats-button-sprite] to make a button that changes when we hover over it, like this:

![no-hover](./no-hover.png?raw=true) ![hover](./hover.png?raw=true)

We'll start with the following basic HTML and CSS:

```html
<html>
<head>
</head>
<body>

  <button class="cats-button">CATS</button>

</body>
</html>
```

```css
html, body, button {
  margin: 0;
  padding: 0;
  border: 0;
  font: inherit;
  vertical-align: baseline;
}

body {
  font-family: sans-serif;
  background: #fff;
  color: #333;
  padding-top: 200px;
  text-align: center;
}
```

[cats-button-sprite]: ./cats-button-sprite.png

Rendering the following unstyled button:

![unstyled](./unstyled.png?raw=true)

Why do we have the "Cats" text at all if we're going to replace it with an image? For screen readers, of course! Let's add the background image to our button to see where we're at.

```css
.cats-button {
  width: 100px;
  background: url("cats-button.png") no-repeat 0 0;
}
```

![bg-button](./bg-button.png?raw=true)

Hmm. Not quite what we want. For one, I don't want the "CATS" text to appear over our image; and I also want the entire first half of the sprite displayed on the button. I can accomplish these simultaneously with the following CSS:

```css
.cats-button {
  /* ... old styling still here ... */
  height: 0px;
  padding-top: 50px;
}
```

![button-no-text](./button-no-text.png?raw=true)

By collapsing the `height: 0px` we make the text disappear; by adding `padding-top: 50px`, we let 50px of the background image to show through. A couple more things to give the user indication that they can click this image, and adding some fancy rounded corners:

```css
.cats-button {
  /* ... old styling still here ... */
  cursor: pointer;
  border-radius: 10px;
}
```

![button-pointer](./button-pointer.png?raw=true)

Finally, the coup de grace. By changing the [`background-position`][bg-pos] of our background image, we can change what part of the sprite gets displayed on hover. Observe:

[bg-pos]: https://developer.mozilla.org/en-US/docs/Web/CSS/background-position

```css
.cats-button:hover {
  background-position: 0 -50px;
}
```

![hover](./hover.png?raw=true)

Yay! Check out the final version [here][final].

[final]: http://appacademy.github.io/css-curriculum/button-sprite/

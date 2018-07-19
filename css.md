# CSS snippets and one-liners

## `box-sizing: border-box`

This instructs each HTML element on the page to work on the border box instead of the default context box, and makes it more intuitive to work with widths – especially widths expressed in percentages, which underpin responsive design – in conjunction with borders and paddings.

The complete, best-practicy version of the technique goes like this:

```css
html {
box-sizing: border-box;
-moz-box-sizing: border-box;
-webkit-box-sizing: border-box;
}

html * {
box-sizing: inherit;
-moz-box-sizing: inherit;
-webkit-box-sizing: inherit;
}
```

Two things happen in the expanded version:

* We use vendor prefixes to make it work in older browsers;
* Forcing the border box on each and every one of our HTML elements makes it hard to have portions that might use the content box model. If instead we use box-sizing: inherit we can then have a container that overrides border box with content box and not have all its children override it -- they will simply inherit from the container.

[Read more here](http://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

## Horizontal and vertical alignment

```css
{ 
  position: absolute; 
  top: 50%; 
  left: 50%; 
  transform: translate(-50%, -50%); 
}
```

## The `object-fit` property

TODO

## Further reading

* [Ten CSS One-Liners to Replace Native Apps](http://alistapart.com/blog/post/ten-css-one-liners-to-replace-native-apps)
* [30 seconds of CSS](https://github.com/atomiks/30-seconds-of-css)
* [Michael Scharnagl's tweet](https://twitter.com/justmarkup/status/974573989497593856?s=21)

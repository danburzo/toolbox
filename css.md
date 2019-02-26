# CSS Topics

## Snippets and one-liners

### `box-sizing: border-box`

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

### Horizontal and vertical alignment

```css
{ 
  position: absolute; 
  top: 50%; 
  left: 50%; 
  transform: translate(-50%, -50%); 
}
```

### The `object-fit` property

TODO

### Further reading

* [Ten CSS One-Liners to Replace Native Apps](http://alistapart.com/blog/post/ten-css-one-liners-to-replace-native-apps)
* [30 seconds of CSS](https://github.com/atomiks/30-seconds-of-css)
* [Michael Scharnagl's tweet](https://twitter.com/justmarkup/status/974573989497593856?s=21)

## Reading materials

### CSS Grid

* [CSS Grid for Designers](https://open.nytimes.com/css-grid-for-designers-f74a883b98f5)
* 🎥 [Making Future Interfaces: Algorithmic Layout](https://www.youtube.com/watch?time_continue=2&v=qOUtkN6M52M)
* 🎥 In [Layout Land](https://www.youtube.com/channel/UC7TizprGknbDalbHplROtag), Jen Simmons explains the basics of CSS Grids.
* [Using CSS Grid the Right Way](https://vgpena.github.io/using-css-grid-the-right-way/)
* [ A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/) over at CSS Tricks
* [Auto-Sizing Columns in CSS Grid: `auto-fill` vs `auto-fit`](https://css-tricks.com/auto-sizing-columns-css-grid-auto-fill-vs-auto-fit/)
* [CSS Grid Experiments](https://julesforrest.com/css-grid-experiments)
* [How I design with CSS Grid](https://www.chenhuijing.com/blog/how-i-design-with-css-grid)
* [Grid to Flex](https://www.gridtoflex.com/)
* [How to build complicated Grids using CSS Grid](https://danwebb.co/journal/how-to-build-complicated-grids-using-css-grid)
* [CSS Grid in IE: Debunking Common IE Grid Misconceptions](https://css-tricks.com/css-grid-in-ie-debunking-common-ie-grid-misconceptions/)
* [CSS Grid for UI Layouts](https://hacks.mozilla.org/2018/02/css-grid-for-ui-layouts/)
* [GRID](http://grid.malven.co/)

### CSS Flexbox

* [FLEX](http://flexbox.malven.co/)
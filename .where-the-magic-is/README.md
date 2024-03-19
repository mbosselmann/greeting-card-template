# ✨ Where the Magic is ✨

Inside of this folder you can find the magic that makes the greeting card template work. The folder contains stylings, JavaScript code and also some fonts that can be used. The stylings are essential for the layout of the card and make the flipcard effect possible that is solved via JavaScript.

As these greeting card template is used to teach fundamental web development skills with a focus on HTML and CSS, the JavaScript code is kept to a bare minimum.

## Explanation of the CSS code inside of `global.css`

The `global.css` file contains the stylings for the greeting card. For a good understanding of the following explanations you should first know more about how CSS works. You should know what a CSS rule is and how to use it. Also how to use selectors and how to use properties and values. For a good start we can recommend [MDN](https://developer.mozilla.org/en-US/) and [CSS Tricks](https://css-tricks.com/).

The file is structured as follows:

```css
/* allison-regular - latin */
@font-face {
  font-display: swap; /* Check https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display for other options. */
  font-family: "Allison";
  font-style: normal;
  font-weight: 400;
  src: url("./fonts/allison-v11-latin-regular.woff2") format("woff2"); /* Chrome 36+, Opera 23+, Firefox 39+, Safari 12+, iOS 10+ */
}

/* handlee-regular - latin */
@font-face {
  font-display: swap; /* Check https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display for other options. */
  font-family: "Handlee";
  font-style: normal;
  font-weight: 400;
  src: url("./fonts/handlee-v18-latin-regular.woff2") format("woff2"); /* Chrome 36+, Opera 23+, Firefox 39+, Safari 12+, iOS 10+ */
}
```

With the `@font-face` rule, we define custom fonts that we want to use for our greeting card:

- The `font-display` property defines how a font is displayed while it is loading.
- The `font-family` property defines the name of the font. When you use the name of the font in your CSS, the browser will use the font file that is defined in the `@font-face` rule.
- The `font-style` property defines the style of the font.
- The `font-weight` property defines the weight of the font.
- The `src` property defines the source of the font file and the format of the font file.
- There are also comments that explain which browsers support the font format.

If you want to learn more about the `@font-face` rule, you can check out the following resources:

- [MDN: @font-face](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face)
- [CSS Tricks: @font-face](https://css-tricks.com/snippets/css/using-font-face/)
- [Google Developers: Web Fonts](https://developers.google.com/fonts/docs/css2)

```css
* {
  box-sizing: border-box;
  margin: 0;
}
```

The universal selector `*` selects all elements on the page. By using the universal selector, we can set the `box-sizing` and `margin` properties for all elements on the page:

- The `box-sizing` property defines how the width and height of an element are calculated.
- The `border-box` value includes the padding and border in the element's total width and height.
- The `margin` property sets the margin of an element to `0`.

Resources to learn more about the `box-sizing` property and the `*` selector:

- [MDN: box-sizing](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing)
- [CSS-Tricks: box-sizing](https://css-tricks.com/box-sizing/)
- [MDN: Universal selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors)
- [CSS-Tricks: Universal selector](https://css-tricks.com/almanac/selectors/u/universal/)

```css
body {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

The `body` selector selects the `body` element on the page. By using the `body` selector, we define some basic stylings for the `body` element that are essential for the layout of the greeting card:

- The `height` property sets the height of the `body` element to `100vh` (100% of the viewport height).
- The `display` property defines the display type of the `body` element. The `flex` value makes the `body` element a flex container. To use `Flexbox` as layout method is a common method for multiple reasons. It is easy to use, it is responsive and it is supported by all major browsers.
- We want to achieve that our greeting card is always centered on the page. The `justify-content` property aligns the flex items (in this case the greeting card) on the main axis (in this case horizontally). The `align-items` property aligns the flex items on the cross axis (in this case vertically). **Amazing!** 🥳

If you want to learn more about **Flexbox**, you can check out the following resources:

- [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [MDN: Flexbox](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox)
- [Josh Comeau: An Interactive Guid to Flexbox](https://www.joshwcomeau.com/css/interactive-guide-to-flexbox/)
- [Game: Flexbox Froggy](https://flexboxfroggy.com/)

```css
.card {
  width: 100%;
  height: 100%;
  max-width: 500px;
  max-height: 790px;
  transform-style: preserve-3d;
  transition: all 0.5s linear;
  -webkit-transition: all 0.5s linear;
}
```

The `.card` selector selects the element with the class `card`. By using the `.card` selector, we define some basic stylings for the greeting card:

- The `width` property sets the width of the greeting card to `100%`.
- The `height` property sets the height of the greeting card to `100%`.
- The `max-width` property sets the maximum width of the greeting card to `500px`.
- The `max-height` property sets the maximum height of the greeting card to `790px`.
- The `transform-style` property defines how the children of the greeting card are rendered in 3D space. The `preserve-3d` value preserves the 3D rendering of the children. For our example is this property essential to make the flipcard effect possible. Otherwise the back side of the card would not be visible.
- The `transition` property defines the transition effect for the greeting card. The `all` value applies the transition effect to all properties that are changed. The `0.5s` value sets the duration of the transition to `0.5s`. The `linear` value sets the transition timing function to `linear`.
- The `webkit` prefix is used for better browser support as some older browsers require the `-webkit-` prefix.

```css
.card section {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  z-index: 0;
}
```

We also have a CSS rule that selects the `section` element inside of the `.card` element. By using the `card section` selector, we define some basic stylings for the `section` element:

- By combining `.card` and `section` we only select `section` elements that are inside of the `.card` element. This is a good example of how to use a **descendant combinator**.
- Each side of the greeting card is a `section` element that is positioned absolutely inside of the `.card` element.
- We need the `backface-visibility` property to hide the back side of the card when the card is flipped. The `-webkit-` prefix is again used for better browser support.
- The `z-index` property sets the z-index of the `section` element to `0`. The z-index property specifies the stack order of an element. An element with greater stack order is always in front of an element with a lower stack order.
- The **absolute positioning** leads to the sections placed on top of each other.
- We also need to set a `z-index` for other absolute positioned elements inside of our sections so that they are only visible on one side of the card. Otherwise they would be visible on both sides. 🤯

```css
@media (max-width: 500px) {
  .card {
    max-height: 100vh;
  }
}
```

Something we also added to our card is a media query. The `@media` rule includes a block of CSS properties only if a certain condition is true. In this case, we use the media query to set the maximum height of the `section` element to `100vh` (100% of the viewport height) when the viewport width is `500px` or less. This way we ensure that the card fills out the entire viewport on smaller devices. **Note:** A viewport is the user's visible area of a web page. The viewport varies with the device and will be smaller on a mobile phone than on a computer screen.

```css
.front {
  position: relative;
  background-color: #fff;
  box-shadow: 2px 11px 26px 2px rgba(17, 17, 26, 0.12);
}

.back {
  padding: 1em;
  background-color: #fff;
  box-shadow: 2px 11px 26px 2px rgba(17, 17, 26, 0.12);
  transform: rotateY(180deg);
  display: grid;
  place-content: center;
}
```

The `.front` and `.back` selectors select the elements with the classes `front` and `back`. By using the `.front` and `.back` selectors, we define some basic stylings for the front and back side of the greeting card. We also add a `trans

- We also add `position: relative` to the `.front` selector. This is necessary to position the `.headline` element inside of the `.front` element.
- The `background-color` property sets the background color of the front and back side of the greeting card to `#fff` (white).
- The `box-shadow` property adds a shadow effect to the front and back side of the greeting card. The `rgba(17, 17, 26, 0.12)` value sets the color of the shadow to a dark color with a low opacity. The `rgba` color model is used to define colors with an alpha channel (opacity).
- We also rotate the back side of the card by `180 deg`. Otherwise the back card would be visible on the front side of the card and the front side of the card would be visible on the back side of the card together with the back side. And for the worse the content would be displayed mirror-inverted. 🤯

```css
.headline {
  position: absolute;
  top: 70%;
  width: 100%;
  z-index: 2;
  text-align: center;
}
```

The headline is positioned absolutely inside of the `.front` element. The `top` property sets the top edge of the headline to `70%` of the height of the `.front` element. The `width` property sets the width of the headline to `100%`. The `z-index` property sets the z-index of the headline to `2`. The `text-align` property centers the text of the headline.

```css
p {
  margin: 0 0 10px 0;
}

.postcardimage {
  height: 100%;
  width: 100%;
  object-fit: cover;
}
```

The `p` selector selects all `p` elements on the page. By using the `p` selector, we define a margin for all `p` elements. The `margin` property sets the margin of the `p` elements to `0 0 10px 0` (top, right, bottom, left). This way we ensure that there is a margin below each paragraph.

Last but not least we have a class selector `.postcardimage` that selects the elements with the class `postcardimage`. By using the `.postcardimage` selector, we define the behaviour of the image that is placed inside of the `.front` element. The `height` and `width` properties set the height and width of the image to `100%`. The `object-fit` property sets how the content of the image is resized to fit the container. The `cover` value scales the image as large as possible while maintaining the aspect ratio and cropping the image to cover the container.

## Explanation of JavaScript Code inside of `script.js`

The `script.js` file contains the JavaScript code that adds interactivity to the greeting card. For a good understanding of the following explanations you should first know more about how JavaScript works. You should know what a variable is and how to use it. Also how to use functions and how to use event listeners. For a good start we can recommend [MDN](https://developer.mozilla.org/en-US/) and [JavaScript.info](https://javascript.info/).

```js
const card = document.querySelector(".card");
card.addEventListener("click", () => {
  card.classList.toggle("flipcard");
});
```

With this code we select the `.card` element and add an event listener to it. The event listener listens for a `click` event on the `.card` element. When the `.card` element is clicked, the event listener calls a function that toggles the `flipcard` class on the `.card` element. The `flipcard` class is used to rotate the card by `180 deg` and to show the back side of the card. If the user clicks on the card again, the `flipcard` class is removed and the card rotates back to the front side.

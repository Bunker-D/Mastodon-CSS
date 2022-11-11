<!-- TODO language shortcuts -->


<a href="#how-to-use-those-files">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 7410 3900" width="1.1em"><path fill="#b22234" d="M0 0h7410v3900H0z"/><path d="M0 450h7410m0 600H0m0 600h7410m0 600H0m0 600h7410m0 600H0" stroke="#fff" stroke-width="300"/><path fill="#3c3b6e" d="M0 0h2964v2100H0z"/><g fill="#fff"><g id="d"><g id="c"><g id="e"><g id="b"><path id="a" d="M247 90l70.534 217.082-184.66-134.164h228.253L176.466 307.082z"/><use xlink:href="#a" y="420"/><use xlink:href="#a" y="840"/><use xlink:href="#a" y="1260"/></g><use xlink:href="#a" y="1680"/></g><use xlink:href="#b" x="247" y="210"/></g><use xlink:href="#c" x="494"/></g><use xlink:href="#d" x="988"/><use xlink:href="#c" x="1976"/><use xlink:href="#e" x="2470"/></g></svg>
&nbsp;&nbsp;English</a><br>

<a href=#comment-utiliser-ces-fichiers>
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 3 2" width="1.1em"><path fill="#EC1920" d="M0 0h3v2H0z"/><path fill="#fff" d="M0 0h2v2H0z"/><path fill="#051440" d="M0 0h1v2H0z"/></svg>
&nbsp;&nbsp;Français
</a><br><br>

![Demonstration](doc/mastodon.png)

---

# How to use those files

## Presentation

This is a CSS overlay that can be applied to the advanced web interface of Mastodon websites.

It brings:
- The ability to control the width of the columns (by dragging their lower right corner),
- A more rounded feel,
- The columns are spread rather than stacked to the left,
- The decorative image (bottom left) can be better handled in some instances.

![Demonstration](doc/mastodon540.mp4)

## Installation

### Set up the browser to apply a style 

- If not already done, enable the avanced web interface for Mastodon, and the Dark theme\*:
  <br>On the right side of the default Mastodon view, click “Preferences”. Then, in “Appaarance”, check “Enable advanced web interface”, and select “Mastodon (Dark)” as the “Site them”.
  <br>\* Alternatively, if you do not want to use a dark theme, you can [remove the additional recoloring](#no-color) provided by this tool.
- Install the *Stylus* browser extension, or any other extension that allows to apply custom CSS to a web page. *Stylus* is available on [Firefox](https://addons.mozilla.org/en-US/firefox/addon/styl-us/) and [Chrome](https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne)).
- Add a style for your Mastodon web page. Typically, for *Stylus*:
  - Go to the your Mastodon web page,
  - Click the button of the extension, then click “write style for …” (stop at the first slash, thus including the name of your instance but not more than that).
- Select the right [CSS file](#choose-the-right-css-file), copy-paste the CSS code in the *Stylus* window.
- [Customize](#customization) if need be.

### Choose the right CSS file

The only difference between the proposed CSS files lies in how the decorative bottom left image is handled, and the optimal choice depends on what your Mastodon instance uses or what you want to use instead.

<!-- TODO choice diagram -->

- If you want to keep the **default image**:
  - If your instance uses something that is integrated to the design **with transparancy**, and that shall be kept to the lower left corner (which is the Mastodon default with a mastodon drawing, seen in most instances), use [`mastodon.css`](mastodon.css).
  - If your instance uses a custom picture with **no transparancy** that should be properly framed and centered, use [`instance.css`](instance.css).
- If you want to use **you own image**:
  - If it has transparancy and be kept to the lower left corner, use [`custom-transp.css`](custom-transp.css).
  - If it has no transparancy and shall be properly framed, used [`custom.css`](custom.css).<br>
    (While `instance.css` will center the image when the column is too wide for it, `custom.css` was created to use higher resolution images that would take the whole available width, and be cropped accordingly to fit a target height.)

### Customization

#### Specify a custom picture

If you are using `custom.css` or `custom-transp.css`, find these lines (toward the end) and put the url of the image you want to use in between the parentheses:
```css
.drawer__inner__mastodon {
  background: url(""); /* 👈 Put image url here. */
```

With `custom.css`, by default, when the image is cropped, its center is kept. It might not perfectly fit your picture, but you can change that by modifying the next line:
```css
  background-position: center center;
```
The first `center` can be replaced with `top` or `bottom`, and the second `center` with `left` or `right`, depending on the area of the picture you want to keep.

#### Custom modifications

You can modify the rest of the code to your liking. For those unfamiliar with CSS, here are a few things you might want to do and how…

<details id="no-color"><summary><strong>Not happy with the new colors?</strong></summary><p>

Just remove the whole *Recolor* section (from `/* Recolor */` to `/* Roundness */`).

If just don't like the gadient on the leftmost column, remove this:
```css
.drawer__inner {
  background: linear-gradient(0deg, $left-bottom 0%, $left-top 100%);
}
```
For keeping a slightly darker color with no gradient, you can also replace it with:
```css
.drawer__inner {
  background: #333746;
}
```

</p></details>

<details><summary><strong>The bottom left image is too small or grows too big?</strong></summary><p>

Find these lines and change the maximal height (by default, `200px`) as you see fit:
```css
.drawer__inner__mastodon {
  max-height: 200px; /* 💡 If the bottom-left picture grows to big, change that. */
```

</p></details>

<details><summary><strong>You don't want a bottom left image?</strong></summary><p>

Find this line:
```css
.drawer__inner__mastodon {
```

… and add `visibility: hidden;` right under it, like so:
```css
.drawer__inner__mastodon {
  visibility: hidden;
```

</p></details>

<br><br>

---

# Comment utiliser ces fichiers

# Aureum: Perfect formatting and readable text, at every screen size. Automatically.

**With only one 3kb CSS file, and absolutely zero CSS classes.**

Because Aureum algorithmically formats your HTML, you don't have to learn any new CSS classes, or clutter your HTML templates with `class="screen-small-12 screen-medium-6"` to try to make the styling look decent on mobile, tablet, and web devices. **It just scales.**

## Customizing / extending Aureum (building your own themes)

Themes should contain three additional `.css` files, included in the following order, after `aureum.css`:
- `theme/skin.css` decorating: *background colors, border colors, border styles etc., and font styles*
- `theme/format.css` layout: *border widths, margins, padding, widths*
- `theme/animate.css` animations: *hover and focus transformations, etc.*

**To see an example webpage, designed with a custom Aureum theme (without any CSS classes), please visit [aureum.io/example.html](https://aureum.io/example.html)**

### Skin.css

A skin design can be built with only a few lines of CSS added to the following groups of HTML tags.

For example, to invert all of the default colors on the site, use:

```css
*:focus {
  outline-color: #ffffff;
}

body {
  background-color: #000000;
}

h1, h2, h3, h4, h5, h6, p, small, a, a:link, a:visited, a:active, a:hover {
  color: #ffffff;
}

u {
  border-bottom-color: #ffffff;
}

input[type=text], input[type=number], input[type=password], input[type=date], input[type=file], input[type=email], input[type=search], textarea, select, button, label, pre {
  border-color: #ffffff;
  color: #ffffff;
}

:-ms-input-placeholder { color: #ffffff; }
:-moz-placeholder { color: #ffffff; }
::-moz-placeholder { color: #ffffff; }
::-webkit-input-placeholder { color: #ffffff; }

pre {
  background-color: #222222;
  border-color: #393939;
}

hr {
  background-color: #ffffff;
}
```

### Format.css

While formatting / building new elements, like a fixed top-bar navigation menu, or a list of articles, it's best to use one of the following values: `0.013, 0.021, 0.034, 0.056, 0.09, 0.146, 0.236, 0.382, 0.618, 1, 1.618, 2.618, 4.236, 6.854, 11.09, 17.944, 29.034, 46.979, 76.013`
- Font sizes, borders, and margins should be set in **rem**: `article { border: 0.146rem solid #fafafa; }`
- Padding should be set in **vw**: `article { padding: 1.618vw; }`
- Widths should be set in **percentages**: `article { width: 50%; }`
- Ratios, such as line height or transform/scale, should be set using `1 + [any of the numbers in the list above]`, like: `article:hover { transform: scale(1.056); }`

For instance, if you wanted to create a list of articles in a container:

```html
<section>
  <article>
    <p>Praesent <a href="#"><u>egestas ante eget</u></a> elit malesuada, a venenatis nulla tincidunt.</p>
  </article><article>
    <p>Nulla sem justo, lacinia nec nunc id, <a href="#"><u>feugiat</u></a> volutpat arcu.</p>
  </article>
</section>
```

and conditionally arrange those articles next to each other -- 2 per row on large screens, and 1 per row on smaller screens -- you would include the following single `@media (max-width: 1000px) {...}` query to the CSS:

**Please note the use of `article { display: inline-block; }` instead of `float: left;`, `article { vertical-align: top; }`, and no whitespace between new article elements (closing & opening tags) `</article><article>`.**

```css
section {
  border-width: 0.146rem;
  padding: 1.618vw;
}

article {
  display: inline-block;
  padding: 1vw;
  vertical-align: top;
  width: 50%;
}
@media (max-width: 1000px) {
  article { width: 100%; }
}

article > p {
  margin-bottom: 0;
  padding: 1.618vw;
}
```

### Animate.css

```css
button {
  transition: transform 160ms ease-in-out;
}

button:hover, button:focus {
  transform: scale(1.056);
}
```

**For more information, please visit [aureum.io](https://aureum.io)**

**To see an example webpage, designed with a custom Aureum theme (without any CSS classes), please visit [aureum.io/example.html](https://aureum.io/example.html)**
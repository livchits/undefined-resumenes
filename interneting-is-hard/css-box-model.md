# CSS Box Model - Cap. 5 of Interneting Is Hard

CSS treats each element in your HTML document as a “box” with a bunch of different properties that determine where it appears on the page. The core components of the CSS box model are padding, borders, margins, block boxes, and inline boxes.

## Block Elements and Inline Elements
 
 [CSS uses “boxes”](https://internetingishard.com/html-and-css/basic-web-pages/#emphasis-italic-elements) to define the layout of a web page. Each HTML element rendered on the screen is a box, and they come in two flavors: “block” boxes and “inline“ boxes.
 
All the HTML have a default type of box. For instance, `<h1>` and `<p>` are block-level elements, while `<em>` and `<strong>` are inline elements. (The `background-color` property only fills in the background of the selected box, so this will give us a clear view into the structure.)
-   **Block boxes** always appear **below** the previous block element. This is the “natural” or “static” flow of an HTML document when it gets rendered by a web browser.
    
-   The **width of block boxes** is set automatically based on the width of its parent container. 
    
-   The default **height of block boxes** is based on the content it contains. 
    
-   **Inline boxes** don’t affect **vertical spacing**. They’re not for determining layout—they’re for styling stuff _inside_ of a block.
    
-   The **width of inline boxes** is based on the content it contains, not the width of the parent element.
 
## Changing Box Behavior

We can override the default box type of HTML elements with the CSS `display` property. For example, we can make `<img>`elements blocks instead of inline elements:
```
img {
  display: block;
}
```
## Content, Padding, Border, and Margin

The “CSS box model” is a set of rules that determine the dimensions of every element in a web page. It gives each box (both inline and block) four properties:

-   **Content** – The text, image, or other media content in the element.
-   **Padding** – The space between the box’s content and its border.
-   **Border** – The line between the box’s padding and margin.
-   **Margin** – The space between the box and surrounding boxes.

This is everything a browser needs to render an element’s box. The content is what you author in an HTML document, and it’s the only one that has any semantic value.

## Padding

The `padding` property it…defines the padding for the selected element:
```
h1 {
  padding: 50px;
}
```
Sometimes you’ll only want to style one side of an element. For that, CSS provides the following properties:

```
p {
  padding-top: 20px;
  padding-bottom: 20px;
  padding-left: 10px;
  padding-right: 10px;
}
```
You can use any unit for the padding of an element, not just pixels.

### Shorthand Formats

CSS provides an alternative “shorthand” form of the `padding` property that lets you set the top/bottom and left/right padding with only one line of CSS. When you provide _two_ values to the `padding` property, it’s interpreted as the vertical and horizontal padding values, respectively.
```
p {
  padding: 20px 0 20px 10px;  /* Top  Right  Bottom  Left */
}
```
or
```
p {
  padding: 20px 10px;  /* Vertical  Horizontal */
}
```

## Borders
The border: a line drawn around the content and padding of an element. The `border` property requires a new syntax: first, we define the stroke width of the border, then its style, followed by its color.
```
h1 {
  padding: 50px;
  border: 1px solid #5D6063;
}
```
This tells the browser to draw a thin gray line around our heading. 

Like `padding`, there are `-top`, `-bottom`, `-left`, and `-right` variants for the `border` property:
```
border-bottom: 1px solid #5D6063;
```
Borders are invaluable for debugging. When you’re not sure how a box is being rendered, add a `border: 1px solid red;` declaration to it. This will clearly show the box’s padding, margin, and overall dimensions.

Please refer to the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/CSS/border-style) for more information about border styles.

## Margins

Margins define the space outside of an element’s border,  the space between a box and its surrounding boxes.

It also accepts the same shorthand formats as `padding` and the properties `margin-top`, `margin-bottom`, `margin-left` and `margin-right`.

### Margin or padding?

-   The padding of a box has a background, while margins are always transparent.
-   Padding is included in the click area of an element, while margins aren’t.
-   Margins collapse vertically, while padding doesn’t.

### Margins on Inline Elements

One of the starkest contrasts between block-level elements and inline ones is their handling of margins. Inline boxes _completely ignore_ the top and bottom margins of an element.

## Vertical Margin Collapse

When you have two boxes with vertical margins sitting right next to each other, they will collapse. Instead of adding the margins together like you might expect, only the biggest one is displayed.
![Diagram: comparison of an uncollapsed vertical margin with a collapsed vertical margin](https://internetingishard.com/html-and-css/css-box-model/vertical-margin-collapse-bba78e.png)Sometimes you do want to prevent the margins from collapsing. All you need to do is put another invisible element in between them.

## Generic Boxes

So far, every HTML element we’ve seen lends additional meaning to the content it contains. But there are many times when we need a generic box purely for the sake of styling a web page. This is what `<div>` and `<span>` are for.

Both `<div>` and `<span>` are “container” elements that don’t have any affect on the semantic structure of an HTML document. They do, however, provide a hook for adding CSS styles to arbitrary sections of a web page. The only real difference between a `<div>` and a `<span>` is that the former is for block-level content while the latter is meant for inline content.

## Explicit Dimensions

Sometimes our desired layout calls for an explicit dimension, like a sidebar that’s exactly 250 pixels wide. For this, CSS provides the `width` and `height` properties. These take precedence over the default size of a box’s content.

## Content Boxes and Border Boxes

The `width` and `height` properties only define the size of a box’s _content_. Its padding and border are both added _on top of_ whatever explicit dimensions you set. This can be a little counterintuitive when you’re trying to lay out a page. Fortunately, CSS lets you change how the width and height of a box is calculated via the `box-sizing` property. By default, it has a value of `content-box`, which leads to the behavior described above, but we can change it to `border-box`. This forces the actual width and height of the box to include padding and borders. Of course, this means that the content width and height are now determined automatically.

## Aligning Boxes

There are three methods for horizontally aligning block-level elements: “auto-margins” for center alignment, “floats” for left/right alignment, and “flexbox” for complete control over alignment. 

### Centering With Auto-Margins

When you set the left and right margin of a block-level element to `auto`, it will center the block in its parent element. For example:
```
div {
  color: #FFF;
  background-color: #4A90E2;
  width: 200px;
  box-sizing: border-box;
  margin: 20px auto; /* Vertical  Horizontal */
}

```
This only works on blocks that have an explicit width defined on them. Remove that `width: 200px` line, and div will be the full width of the browser, making “center alignment” meaningless.

## Resetting Styles

Different browsers have different default styles for all of their HTML elements, making it difficult to create consistent stylesheets. It’s usually a good idea to override default styles to a predictable value using the “universal” CSS selector (`*`). 
```
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```
This selector matches every HTML element, effectively resetting the `margin` and `padding` properties, also convert all our boxes to `border-box`.

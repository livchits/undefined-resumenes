# Floats - Cap. 7 of Interneting Is Hard

“Floats” let you put block-level elements side-by-side instead of on top of each other. It lets us build all sorts of layouts, including sidebars, multi-column pages, grids, and magazine-style articles with text flowing around an image.

Float-based layouts have mostly been replaced with [Flexbox](https://internetingishard.com/html-and-css/flexbox/) in modern websites. But you’ll definitely encounter them at some point in your career.

## Default HTML Layout Behavior

Floats alter the default layout of a web page. Each block-level element fills 100% of its parent elements’s width and they appear vertically one after another. We’re essentially limited to a single-column layout.

## Floating an Element

The CSS `float` property gives us control over the _horizontal_ position of an element. By “floating” an element to the left, we’re telling the browser to align it to the left side of the page. It also tells surrounding elements that they can flow _around_ the element instead of beginning underneath it.

You can also float elements right. Or, if you’re overriding a float declaration, you can cancel it with the `none` value.

Floated boxes always align to the left or right of their parent element.

## Multiple Floats

When you float multiple elements in the same direction, they’ll stack horizontally.

## After a Float

### Clearing Floats

“Clearing” a float is when we tell a block to ignore any floats that appear before it. Instead of flowing around the floated box, a cleared element always appears after any floats. It’s like forcing a box back into the default vertical flow of the page.
```
.footer {
  clear: both;            /* Add this */
  height: 200px;
  background-color: #D6E9FE;
}
```
Usually, you want to clear both left and right floats, but you can choose to clear only one or the other with the `left` or `right` values. 

### Hiding Overflow

Clearing floats only fixes the height issue when there’s an element _inside_ the container element that we can add a `clear` property to. 

By adding an `overflow: hidden` declaration to a container div, we’re telling it to recognize the height of any floated elements it contains. This is how we can add a background color, for example. Without it, we wouldn’t be able to see the container’s background because it would have zero height.

To summarize, when you have an extra unfloated HTML element at the bottom of a container div, use the `clear` solution. Otherwise, add an `overflow: hidden` declaration to the container element. The underlying idea for both options is that you need a way to tell the browser to incorporate floats into the height of their container element in order for their backgrounds to show up.

## Floats for Equal-Width Columns

Floats can also be used to create multi-column layouts. We can add three equal-width columns to a footer:
```
<div class='footer'>
  <div class='column'></div>
  <div class='column'></div>
  <div class='column'></div>
</div>
```
```
.column {
  float: left;
  width: 31%;
  margin: 20px 1.15%;
  height: 160px;
  background-color: #B2D6FF;    /* Medium blue */
}
```
Percentages in CSS are relative to the width of the parent element. The result is three columns that automatically resize to one-third of the browser window. Resize the browser window, and you’ll see our columns grow and shrink accordingly. 

## Floats for Grids

Want a grid in the footer instead of 3 columns? No problem! When there isn’t enough room to stack a floated element horizontally, it pops down to the next line. All we need to do is add some more `.column` elements:
```
<div class='footer'>
  <div class='column'></div>
  <div class='column'></div>
  <div class='column'></div>
  <div class='column'></div>
  <div class='column'></div>
  <div class='column'></div>
</div>
```
Our footer background is too short. Let’s replace the footer’s explicit height with another `overflow: hidden` so it can accommodate any number of grid items:
```
.footer {
  overflow: hidden;
  background-color: #D6E9FE;
}
```
## Floats for Content

Another aspect of layouts is styling the individual HTML components (your actual content) that go inside this overarching page structure.
Let’s add some dummy content to our `.content` element so we have something to play with:

```
<div class='container'>
  <div class='page'>
    <div class='sidebar'></div>
    <div class='content'>
      
      <img src='?' class='article-image'/>

      <p>Ad netus sagittis velit orci est non ut urna taciti metus donec magnis
      hendrerit adipiscing mauris sit a proin ultrices nibh.</p>

      <p>Enim suspendisse ac scelerisque nascetur vestibulum parturient sed mi a
      dolor eu non adipiscing non neque scelerisque netus ullamcorper sed
      parturient integer.Eros dui risus non sodales ullamcorper libero a dis
      cubilia a orci iaculis cursus.</p>

      <p>Egestas at aliquam a egestas accumsan cum elementum consectetur conubia
      tristique eu et vitae condimentum in ante consectetur suscipit a a duis
      vestibulum gravida morbi sagittis.Parturient scelerisque facilisis
      ullamcorper a a pretium a nisl parturient semper senectus accumsan ipsum
      mus scelerisque eget ridiculus.Accumsan dolor a.</p>

      <p>Ligula taciti vel primis sit a tincidunt habitant parturient parturient
      in parturient ante nulla consectetur sem.Facilisis parturient litora.</p>

    </div>
  </div>
</div>
```

Let’s create a magazine-style layout by floating the image and letting the text flow around it.

```
.content {
  padding: 20px;
}

.article-image {
  float: left;
  width: 300px;
  height: 200px;
  margin-right: 20px;
  margin-bottom: 20px;
}

p {
  margin-bottom: 20px;
}
```

### Hiding Overflow (For Content)

Let’s try this in our footer: in your favorite `.column` element, add the following:
```
<div class='column'>
  <div class='avatar'></div>
  <h3 class='username'>Bob Smith</h3>
  <p class='comment'>Aptent vel egestas vestibulum aliquam ullamcorper volutpat
  ullamcorper pharetra hac posuere a rhoncus purus molestie torquent. Scelerisque
  purus cursus dictum ornare a phasellus. A augue venenatis adipiscing.</p>
</div>
```
And the corresponding CSS rules:

```
.avatar {
  float: left;
  width: 60px;
  height: 60px;
  margin: 25px;
  border-radius: 40px;
  background-color: #D6E9FE;
}

.username {
  margin-top: 30px;
}

.comment {
  margin: 10px;
  overflow: hidden;  /* This is important */
}
```
This highlights another use case for our `overflow: hidden` trick. Sticking it on our `.comment` box made sure that the text “horizontally cleared” the floated image. Without it, the last line of the `.comment` text would hang underneath the image.
![Web pages showing with hidden overflow (text left-aligned) and without hidden overflow (text flowing around icon)](https://internetingishard.com/html-and-css/floats/no-overflow-hidden-for-content-1cb097.png)

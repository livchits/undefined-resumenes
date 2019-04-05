# CSS Selectors - Cap. 6 of Interneting Is Hard

“CSS selectors” let us map a single CSS rule to a specific HTML element. This makes it possible to _selectively_ style individual elements while ignoring others.

The “type selector” targets all the matching elements on a page. Now we’ll explore more granular ways to style a web page with class selectors, descendant selectors, pseudo-classes, and ID selectors.

## Class Selectors

“Class selectors” let you apply CSS styles to a specific HTML element. They let you differentiate between HTML elements of the same type, like when we had two `<div>` elements, but only wanted to style one of them. Class selectors require two things:
-   A `class` attribute on the HTML element in question.
-   A matching CSS class selector in your stylesheet.
```
<p class='synopsis'>CSS selectors let you <em>select</em> individual HTML
   elements in an HTML document. This is <strong>super</strong> useful.</p>
```
```
.synopsis {
  color: #7E8184;        /* Light gray */
  font-style: italic;
}
```
This rule is _only_ applied to elements with the corresponding `class` attribute. The dot (`.`) prefixing the class name distinguishes class selectors from the type selectors.

### Class Naming Conventions

The value of the HTML `class` attribute can be (almost) anything you want. The standard naming convention is to use all lowercase and hyphens for spaces. It’s usually a good idea to avoid naming classes based on their appearance. Using something semantic like `.synopsis` gives us more freedom for our CSS to customize how that synopsis is displayed.

## Container Divs

`<div>` doesn’t alter the semantic structure of a page, which makes it a great tool for defining the _presentational_ structure of a web page. By wrapping other HTML elements in `<div>` tags, we can organize our site into larger layout-oriented chunks without messing up how search engines view our content.

## Reusing Class Styles

The same class can be applied to multiple elements in a single HTML document. This means that we can now reuse arbitrary CSS declarations wherever we want.

## Modifying Class Styles

We can apply multiple classes to the _same_ HTML element, too. The styles from each class will be applied to the element, giving us the opportunity to reuse styles and override some of them with a new class.

### Order Matters

Overriding occurs in our stylesheet. When there’s two conflicting properties in a CSS file, the last one is always the one that gets applied. This means that the order of the `class` attribute in our HTML element has no effect on override behavior. 

## Descendant Selectors

“Descendant selectors” let you target only those elements that are _inside_ of another element. For example, we can pull out that `<em>` in the `.synopsis` paragraph with the following:
```
.synopsis em {
  font-style: normal;
}
```
Descendant selectors aren’t limited to class selectors—you can combine any other group of selectors this way. For instance:
```
h1 em {
  /* Some other styles */
}
```
Check out the related “child selector” [over at MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_selectors).

## Pseudo-Classes for Links

In a rendered web page there’s “stateful” information about what the user is doing (opposed to the content we’ve authored). The classic example is a link. You create an `<a href>` element and the user can interact with that link. They can hover over it, click it, and visit the URL.
CSS “pseudo-classes” provide a mechanism for hooking into this kind of temporary user information and style each one of them individually. Think of them as class selectors that you don’t have to write on your own because they’re built into the browser.

### Basic Link Styles

Pseudo-classes begin with a colon followed by the name of the desired class. The most common link pseudo-classes are as follows:

-   `:link` – A link the user has never visited.
-   `:visited` – A link the user has visited before.
-   `:hover` – A link with the user’s mouse over it.
-   `:active` – A link that’s being pressed down by a mouse (or finger).
```
a:link {
  color: blue;
  text-decoration: none;
}
a:visited {
  color: purple;
}
a:hover {
  color: aqua;
  text-decoration: underline;
}
a:active {
  color: red;
}
```
### Visited Hover State

In the above snippet our `a:hover` style is applied to both visited and unvisited links. We can refine our links even more:
```
a:visited:hover {
  color: orange;
}
```
This breaks our `a:active`, so...

### Visited Active State

We can fix that with `a:visited:active`. 
```
a:visited:active {
  color: red;
}
```
## Pseudo-Classes for Buttons

Pseudo-classes can be applied to any kind of selector. For example, to a class for [make a button.](https://internetingishard.com/html-and-css/css-selectors/#pseudo-classes-for-buttons)

## Pseudo-Classes For Structure

There’s also a [bunch of other pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) that provide extra information about an element’s surroundings. For example, the `:last-of-type` pseudo-class selects the final element of a particular type in its parent element.
```
p:last-of-type {
  margin-bottom: 50px;
}
```
The `:first-of-type` and `:last-of-type` selectors only operate inside their parent element. That is to say, `p:first-of-type` selects the first `<p>` in _every_ container element.

## ID Selectors

“ID selectors” are a more stringent alternative to class selectors. They work pretty much the same way, except you can only have _one_ element with the same ID per page, which means you can’t reuse styles at all. Instead of a `class` attribute, they require an `id` attribute on whatever HTML element you’re trying to select. 
```
<a id='button-2' class='button' href='nowhere.html'>Button Two</a>
```
```
#button-2 {
  color: #5D6063;  /* Dark gray */
}
```
### URL Fragments

`id` attributes need to be unique because they serve as the target for “URL fragments”. Fragments are how you point the user to a specific part of a web page.
```
<!-- From the same page -->
<a href='#button-2'>Go to Button Two</a>

<!-- From a different page -->
<a href='selectors.html#button-2'>Go to Button Two</a>
```

## CSS Specificity

“CSS specificity” is the weight given to different categories of selectors. This means that certain selectors will _always_ override other ones, regardless of where they appear in the stylesheet.

The specificity of selectors are show below, from greatest to least:
-   `#button-2`
-   `.button:link`
-   `a:link` and `.synopsis em` (they’re equal)
-   `.button`
-   `a`

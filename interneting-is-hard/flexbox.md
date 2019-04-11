# Flexbox- Cap. 8 of Interneting Is Hard

Flexbox gives us _complete_ control over the alignment, direction, order, and size of our boxes.

Use flexbox to lay out your web pages as much as possible, reserving floats for when you need text to flow _around_ a box (i.e., a magazine-style layout) or when you need to support legacy web browsers.

## Flexbox Overview

Flexbox uses two types of boxes that we’ve never seen before: “flex containers” and “flex items”. The job of a flex container is to group a bunch of flex items together and define how they’re positioned.

Every HTML element that’s a direct child of a flex container is an “item”. Flex items can be manipulated individually, but for the most part, it’s up to the container to determine their layout. The main purpose of flex items are to let their container know how many things it needs to position. Defining complex web pages with flexbox is all about nesting boxes.

## Flex Containers

The first step in using flexbox is to turn one of our HTML elements into a flex container. We do this with the `display` property, by giving it a value of `flex`, we’re telling the browser that everything in the box should be rendered with flexbox instead of the default box model.
```
.menu-container {
  /* ... */
  display: flex;
}
```

## Aligning a Flex Item

To define the horizontal alignment of the items in a flexcontainer we have the `justify-content` property.
```
.menu-container {
  /* ... */
  display: flex;
  justify-content: center;   
}
```
This has the same effect as adding a `margin: 0 auto` declaration to the `.menu` element, which is into the `menu-container` element. Manipulating items through their containers like this is a common theme in flexbox.

Other values for `justify-content` are:
-   `center`
-   `flex-start`
-   `flex-end`
-   `space-around`
-   `space-between`

## Distributing Multiple Flex Items

The `justify-content` property also lets you distribute items equally inside a container:`space-around` value spreads its items out across its entire width. The flex container automatically distributes extra horizontal space to either side of each item. The `space-between` value is similar, but it only adds that extra space _between_ items.

## Grouping Flex Items

Flex containers only know how to position elements that are one level deep (i.e., their child elements). Wrapping a bunch of items in an extra `<div>` results in a totally different web page.
![Diagram: wrapping two flex items in a <div> to eliminate one of the flex items](https://internetingishard.com/html-and-css/flexbox/grouping-flex-items-1bb642.png)
## Cross-Axis (Vertical) Alignment

Flex containers can also define the vertical alignment (cross-axis) of their items if the container has an explicit heigth. Vertical alignment is defined by adding an `align-items` property to a flex container. The available options are:
-   `center`
-   `flex-start` (top)
-   `flex-end` (bottom)
-   `stretch`
-   `baseline`

The `stretch` lets you display the background of each element. The box for each item extends the full height of the flex container, regardless of how much content it contains. A common use case for this behavior is creating equal-height columns with a variable amount of content in each one.

##Wrapping Flex Items

Flexbox is a powerful alternative to float-based grids. It can render items as a grid, it can change their alignment, direction, order, and size. To create a grid, we need the flex-wrap property.

`flex-wrap` property forces items that don’t fit to get bumped down to the next row.

##Flex Container Direction

“Direction” refers to whether a container renders its items horizontally or vertically. Horizontal is the default direction: items are drawn one after another in the same row before popping down to the next column when they run out of space.

Flexbox can transform rows into columns using only a single line of CSS. 
```
flex-direction: column;
```

###Alignment Considerations

When you rotate the direction of a container, you also rotate the direction of the justify-content property. It now refers to the container’s vertical alignment—not its horizontal alignment.

![Diagram: axes flipped when flex-direction is equal to column](https://internetingishard.com/html-and-css/flexbox/flex-direction-axes-b30e85.png)
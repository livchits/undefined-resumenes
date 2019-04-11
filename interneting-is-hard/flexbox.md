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

## Wrapping Flex Items

Flexbox is a powerful alternative to float-based grids. It can render items as a grid, it can change their alignment, direction, order, and size. To create a grid, we need the flex-wrap property.

`flex-wrap` property forces items that don’t fit to get bumped down to the next row.

## Flex Container Direction

“Direction” refers to whether a container renders its items horizontally or vertically. Horizontal is the default direction: items are drawn one after another in the same row before popping down to the next column when they run out of space.

Flexbox can transform rows into columns using only a single line of CSS. 
```
flex-direction: column;
```

### Alignment Considerations

When you rotate the direction of a container, you also rotate the direction of the justify-content property. It now refers to the container’s vertical alignment—not its horizontal alignment.

![Diagram: axes flipped when flex-direction is equal to column](https://internetingishard.com/html-and-css/flexbox/flex-direction-axes-b30e85.png)

## Flex Container Order

The `flex-direction` property also offers you control over the order in which items appear via the `row-reverse` and `column-reverse` properties. 
![Diagram: row (left to right), row-reverse (right to left), column (top to bottom), column-reverse (bottom to top)](https://internetingishard.com/html-and-css/flexbox/flex-direction-reverse-532d8f.png)
Notice that this only swaps the order on a per-row basis.

## Flex Item Order

Adding an `order` property to a flex item defines its order in the container without affecting surrounding items. Its default value is `0`, and increasing or decreasing it from there moves the item to the right or left, respectively. Unlike setting `row-reverse` and `column-reverse` on a flex container, `order` works across row/column boundaries.

## Flex Item Alignment

We align items individually with the `align-self` propert. Adding this to a flex item overrides the `align-items` value from its container.

You can align elements using the same values as the `align-items` property:
-   `center`
-   `flex-start` (top)
-   `flex-end` (bottom)
-   `stretch`
-   `baseline`

## Flexible Items

Flex items are _flexible_: they can shrink and stretch to match the width of their containers. The `flex` property allows them to have flexible widths. It works as a weight that tells the flex container how to distribute extra space to each item. For example, an item with a `flex` value of `2` will grow twice as fast as items with the default value of `1`.
![Diagram: no flex (3 square boxes), equal flex (3 rectangle boxes), unequal flex (2 smaller boxes, one stretched out box)](https://internetingishard.com/html-and-css/flexbox/flexible-items-cfe7a3.png)
### Static Item Widths

We can even mix-and-match flexible boxes with fixed-width ones. `flex: initial` falls back to the item’s explicit `width` property. This lets us combine static and flexible boxes in complex ways.
![Diagram: fixed-width box (flex: initial), flexible box (flex: 1)](https://internetingishard.com/html-and-css/flexbox/combining-flexible-and-static-items-52aacb.png)
## Flex Items and Auto-Margins

Auto-margins in flexbox can be used as an alternative to an extra `<div>` when trying to align a group of items to the left/right of a container. Think of auto-margins as a “divider” for flex items in the same container.

Auto-margins eat up _all_ the extra space in a flex container, so instead of distributing items equally, this moves the item with `margin-left: auto;` and any following items to the right side of the container.

## Summary

Flexbox gave us a ton of amazing new tools for laying out a web page. 
-   Use `display: flex;` to create a flex container.
-   Use `justify-content` to define the horizontal alignment of items.
-   Use `align-items` to define the vertical alignment of items.
-   Use `flex-direction` if you need columns instead of rows.
-   Use the `row-reverse` or `column-reverse` values to flip item order.
-   Use `order` to customize the order of individual elements.
-   Use `align-self` to vertically align individual items.
-   Use `flex` to create flexible boxes that can stretch and shrink.

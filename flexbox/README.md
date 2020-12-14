# Flexbox

Flexbox uses two types of boxes: “flex containers” and “flex items”. The job of a flex container is to group a bunch of flex items together and define how they’re positioned.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-container-and-flex-items-6234bb.png" width="400px">

Every HTML element that’s a direct child of a flex container is an “item”. Flex items can be manipulated individually, but for the most part, it’s up to the container to determine their layout. The main purpose of flex items are to let their container know how many things it needs to position.

### Flex Containers

By setting `display: flex` we’re telling the browser that everything in the box should be rendered with flexbox instead of the default box model. This enables the flexbox layout mode—without it, the browser would ignore all the flexbox properties.
<br/>
The next job is to define the horizontal alignment of the items, this is done with the `justify-content` property. By setting `justify-content: center` This has the same effect as adding a margin: 0 auto declaration to the .menu element. But we did this by adding a property to the parent element (the flex container) instead of directly to the element we wanted to center (the flex item).
<br/>
`justify-content` values are:

- center
- flex-start
- flex-end
- space-around
- space-between

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-justify-content-alignment-ea129c.png" width="400px">
<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-justify-content-distribution-b0ee9c.png" width="400px">

### Grouping elements

Flex containers only know how to position elements that are one level deep (i.e., their child elements). They don’t care one bit about what’s inside their flex items. Wrapping a bunch of items in an extra &lt;div&gt; results in a totally different web page.

<img src="https://www.internetingishard.com/html-and-css/flexbox/grouping-flex-items-1bb642.png" width="400px">

### Cross-Axis (Vertical) Alignment

Flex containers can also define the vertical alignment of their items. Since `.header` has an explicit height, items can be positioned vertically inside of it. The official specification calls this “cross-axis” alignment but it might as well be called “vertical” alignment. Vertical alignment is defined by adding an `align-items` property to a flex container. Adding `align-items: center` moves the content into the middle of our 300px height element
<br/>
`align-items` values are:

- center
- flex-start (top)
- flex-end (bottom)
- stretch
- baseline

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-align-items-26abfd.png" width="400px">

stretch is interesting as The box for each item extends the full height of the flex container, regardless of how much content it contains. A common use case for this behavior is creating equal-height columns with a variable amount of content in each one—something very difficult to do with floats.

### Wrapping items

Flexbox is a more powerful alternative to float-based grids. Not only can it render items as a grid—it can change their alignment, direction, order, and size, using the `flex-wrap property`.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-wrap-b960c1.png" width="400px">

By adding `flex-wrap: wrap` property, any items that don't fit horizontally get bumped down to the next row. Now, our flex items behave much like floated boxes, except flexbox gives us more control over how “extra” items are aligned in the final row via the `justify-content` property.

### Flex Container Direction

“Direction” refers to whether a container renders its items horizontally or vertically. So far, all the containers we’ve seen use the default horizontal direction, `flex-direction` can change this from row (horizontal) to column (vertical).
<br/>
When you rotate the direction of a container, you also rotate the direction of the justify-content property (clock-wise). It now refers to the container’s vertical alignment—not its horizontal alignment.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-direction-axes-b30e85.png" width="400px">

The flex-direction property also offers you control over the order in which items appear via the `row-reverse` and `column-reverse` properties.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-direction-reverse-532d8f.png" width="400px">

### Flex Item Order

Adding an `order` property to a flex item defines its order in the container without affecting surrounding items. Its default value is 0, and increasing or decreasing it from there moves the item to the right or left, respectively.
<br/>
By setting the first-item property `order: 1` and the last-item property `order: -1` we can swap them without effecting the other images stored on the page.

### Flex Item Alignment

We can also align items individually using the `align-self` property. Adding this to a flex item overrides the `align-items` value from its container. By adding `align-self: flex-end` to `.social, .subscribe` sends them to the bottom of the `.header` element. Note margins and padding work as expected. You can used the same values outlined in [align-items](#cross-axis-vertical-alignment)

### Item Flex

Flex items are flexible: they can shrink and stretch to match the width of their containers. The `Flex` property defines the width of individual items in a flex container. Or, more accurately, it allows them to have flexible widths. It works as a weight that tells the flex container how to distribute extra space to each item. For example, an item with a flex value of 2 will grow twice as fast as items with the default value of 1.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flexible-items-cfe7a3.png" width="400px">

Compare this to the `justify-content` property, which distributes extra space between items. This is similar, but now we’re distributing that space into the items themselves. The result is full control over how flex items fit into their containers.
<br/>
We can even mix-and-match flexible boxes with fixed-width ones. `flex: initial` falls back to the item’s explicit width property. This lets us combine static and flexible boxes in complex ways.

<img src="https://www.internetingishard.com/html-and-css/flexbox/combining-flexible-and-static-items-52aacb.png" width="400px">

Because of the `flex: initial` in `.footer-one, .footer-three` the `flex: 1` property is ignored so we can set a sttic width for both elements. because of this when re sizing the page, the dark blue boxes will never change size, whilst the light blue box will.

<img src="https://www.internetingishard.com/html-and-css/flexbox/footer-flexible-items-static-widths-af0a32.png" width="400px">

### Flex and Auto Margins

Auto-margins in flexbox are special. They can be used as an alternative to an extra &lt;div&gt; when trying to align a group of items to the left/right of a container. Think of auto-margins as a “divider” for flex items in the same container.
<br/>
By removing the div containing the `.signup` and `.login` elements, everything is evenly spaced across the flex container. by setting `margin-left: auto` on the `.signup` element the auto-margins eat up all the extra space in a flex container, so instead of distributing items equally, this moves the .`signup` and any following items (`.login`) to the right side of the container.

### Summary

- Use `display: flex;` to create a flex container.
- Use `justify-content` to define the horizontal alignment of items.
- Use `align-items` to define the vertical alignment of items.
- Use `flex-direction` if you need columns instead of rows.
- Use the `row-reverse` or `column-reverse` values to flip item order.
- Use `order` to customize the order of individual elements.
- Use `align-self` to vertically align individual items.
- Use `flex` to create flexible boxes that can stretch and shrink.

### Extra - align-content vs align-items

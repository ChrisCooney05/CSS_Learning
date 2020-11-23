# Flexbox

Flexbox uses two types of boxes: “flex containers” and “flex items”. The job of a flex container is to group a bunch of flex items together and define how they’re positioned.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-container-and-flex-items-6234bb.png" width="400px">

Every HTML element that’s a direct child of a flex container is an “item”. Flex items can be manipulated individually, but for the most part, it’s up to the container to determine their layout. The main purpose of flex items are to let their container know how many things it needs to position.

### Flex Containers 

By setting ```display: flex``` we’re telling the browser that everything in the box should be rendered with flexbox instead of the default box model. This enables the flexbox layout mode—without it, the browser would ignore all the flexbox properties.
<br/>
The next job is to define the horizontal alignment of the items, this is done with the ```justify-content``` property. By setting ```justify-content: center``` This has the same effect as adding a margin: 0 auto declaration to the .menu element. But we did this by adding a property to the parent element (the flex container) instead of directly to the element we wanted to center (the flex item).
<br/>
```justify-content``` values are:
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

Flex containers can also define the vertical alignment of their items. Since ```.header``` has an explicit height, items can be positioned vertically inside of it. The official specification calls this “cross-axis” alignment but it might as well be called “vertical” alignment. Vertical alignment is defined by adding an ```align-items``` property to a flex container. Adding ```align-items: center``` moves the content into the middle of our 300px height element
<br/>
```align-items``` values are:
  - center
  - flex-start (top)
  - flex-end (bottom)
  - stretch
  - baseline

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-align-items-26abfd.png" width="400px">

stretch is interesting as The box for each item extends the full height of the flex container, regardless of how much content it contains. A common use case for this behavior is creating equal-height columns with a variable amount of content in each one—something very difficult to do with floats.

### Wrapping items

Flexbox is a more powerful alternative to float-based grids. Not only can it render items as a grid—it can change their alignment, direction, order, and size, using the ```flex-wrap property```.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-wrap-b960c1.png" width="400px">


By adding ```flex-wrap: wrap``` property, any items that don't fit horizontally get bumped down to the next row. Now, our flex items behave much like floated boxes, except flexbox gives us more control over how “extra” items are aligned in the final row via the ```justify-content``` property.

### Flex Container Direction

“Direction” refers to whether a container renders its items horizontally or vertically. So far, all the containers we’ve seen use the default horizontal direction, ```flex-direction``` can change this from row (horizontal) to column (vertical).
<br/>
When you rotate the direction of a container, you also rotate the direction of the justify-content property (clock-wise). It now refers to the container’s vertical alignment—not its horizontal alignment.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-direction-axes-b30e85.png" width="400px">

The flex-direction property also offers you control over the order in which items appear via the ```row-reverse``` and ```column-reverse``` properties.

<img src="https://www.internetingishard.com/html-and-css/flexbox/flex-direction-reverse-532d8f.png" width="400px">

### Flex Item Order

Adding an ```order``` property to a flex item defines its order in the container without affecting surrounding items. Its default value is 0, and increasing or decreasing it from there moves the item to the right or left, respectively.
<br/>
By setting the first-item property ```order: 1``` and the last-item property ```order: -1``` we can swap them without effecting the other images stored on the page.

### Flex Item Alignment

We can also align items individually using the ```align-self``` property. Adding this to a flex item overrides the ```align-items``` value from its container. By adding ```align-self: flex-end``` to ```.social, .subscribe``` sends them to the bottom of the ```.header``` element. Note margins and padding work as expected. You can used the same values outlined in [align-items](#cross-axis-vertical-alignment)
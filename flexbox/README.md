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


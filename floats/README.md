# Floats

Floats” let you put block-level elements side-by-side instead of on top of each other. This is a big deal. It lets us build all sorts of layouts, including sidebars, multi-column pages, grids, and magazine-style articles with text flowing around an image. This is where we finally start creating real web pages. Float-based layouts have mostly been replaced with Flexbox in modern websites. Perhaps more importantly, the limited nature of floats makes them a gentler introduction to CSS layouts than Flexbox.

### Floating Elements

The CSS float property gives us control over the horizontal position of an element. By “floating” an element to the left, we’re telling the browser to align it to the left side of the page. However, this doesn’t just align the sidebar—it also tells surrounding elements that they can flow around the sidebar instead of beginning underneath it.
<br/>
We now have all the tools necessary to align block-level elements: floats for left/right alignment and auto-margins for center alignment. This only applies to block boxes. Inline boxes are aligned with the text-align property.
<br/>
Floated boxes always align to the left or right of their parent element. In our example, the sidebar’s parent is &lt;div class='page'&gt; by setting the .page width to a fixed size and margin to 0 top/bottom and auto for width, we can take the floated sidebar element off the edge of the browser window. Positioning nested container divs like this is how you build up sophisticated website layouts.
<img src="https://www.internetingishard.com/html-and-css/floats/floating-in-fixed-width-page-a9c965.png" width="400px">

### Multiple Floats

When you float multiple elements in the same direction, they’ll stack horizontally, much like the default vertical layout algorithm, except rotated 90 degrees. By setting the float of .content to left, both elements stack side by side, instead of the sidebar resting within content.

<img src="https://www.internetingishard.com/html-and-css/floats/two-floats-next-to-each-other-37f154.png" width="400px">

### After a Float

As both the sidebar and content have been floated, they are removed from the normal flow of the page, so the footer is now pressed up against the menu div or the last element that was not floated. <br/>
Clearing a float is when we tell a block to ignore any floats that appear before it. It’s like forcing a box back into the default vertical flow of the page. Done by setting ```clear: both``` to the .footer element.

<img src="https://www.internetingishard.com/html-and-css/floats/clearing-a-float-44a4d5.png" width="400px">

Clearing floats only fixes the height issue when there’s an element inside the container element that we can add a clear property to. With the footer now outside of the .page container the .page container has a 0 height issue. <br/>
By adding ```overflow: hidden``` we’re telling it to recognize the height of any floated elements it contains. this is how the grey background shows up instead of just white.
<br/>
when you have an extra unfloated HTML element at the bottom of a container div, use the ```clear``` solution. Otherwise, add an ```overflow: hidden``` declaration to the container element.
<br/>

### Floats for Columns

Percentages in CSS are relative to the width of the parent element. The result is three columns that automatically resize to one-third of the browser window.

<img src="https://www.internetingishard.com/html-and-css/floats/floats-for-columns-8a52b0.png" width="400px">

When there isn’t enough room to stack a floated element horizontally, it pops down to the next line. By removing the implicit height of the footer and adding ```overflow: hidden``` it will scale to accommodate as many .column elements as we want.

### Overflow with content

When adding content to an element that contains a float, everything will wrap around it, in a magazine style. If we want to avoid this, we need to use ```overflow: hidden``` just like in the .comment div. This will “horizontally cleared” the floated image. Without it, the last line of the .comment text would hang underneath the image.

<img src="https://www.internetingishard.com/html-and-css/floats/no-overflow-hidden-for-content-1cb097.png" width="400px">

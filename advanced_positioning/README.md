# Advanced Positioning 
The other three types of positioning are “relative”, “absolute”, and “fixed”. Each of them let you manually position elements using specific coordinates, opposed to the more semantic options in flexbox and floats. Instead of saying “Stick this box in the center of its container,” advanced positioning lets you say things like “Put that box 20 pixels above and 50 pixels to the right of its parent’s origin.”
<br/>
The vast majority of elements on a web page should be laid out according to the static flow of the page. These other positioning schemes come into play when you want to do more advanced things like tweak the position of a particular element or animate a UI component without messing up the surrounding elements.

<img src="https://www.internetingishard.com/html-and-css/advanced-positioning/css-positioning-schemes-790d5b.png" width="400px">

The CSS ```position``` property lets you alter the positioning scheme of a particular element. Its default value, as you might imagine, is ```static```. When an element’s position property doesn’t have a value of ```static```, it’s called a “positioned element”.

### Relative Positioning

“Relative positioning” moves elements around relative to where they would normally appear in the static flow of the page. This is useful for nudging boxes around when the default flow is just a little bit off. The ```position: relative;``` line makes it a positioned element, and the ```bottom``` and ```right``` properties let you define how far it’s offset from its static position. This is sort of like setting an (x, y) coordinate for the element.
<br/>
The ```bottom``` and ```right``` properties measure from the original box’s top and left edges, respectively. We can offset relative to the other edges with the ```top``` and ```left``` properties.

<img src="https://www.internetingishard.com/html-and-css/advanced-positioning/relative-positioning-offsets-494268.png" width="400px">

Note that these properties accept negative values, which means there’s two ways to specify the same offset. We could just as easily used ```top: -30px;``` in place of ```bottom: 30px;```.

### Absolute Positioning 

“Absolute positioning” is just like relative positioning, but the offset is relative to the entire browser window instead of the original position of the element. Since there’s no longer any relationship with the static flow of the page, consider this the most manual way to lay out an element.

<img src="https://www.internetingishard.com/html-and-css/advanced-positioning/absolute-positioning-screenshot-641ad7.png" width="400px">

The other interesting effect of ```absolute``` is that it completely removes an element from the normal flow of the page. In our relative positioning example (the first row), there’s still a space where the positioned element used to be, but with absolute positioning, that space has vanished. It’s as if ```.item-absolute``` doesn’t even exist to its parent and surrounding elements.
<br/>
Absolute positioning becomes much more practical when it’s relative to some other element that is in the static flow of the page. Coordinates for absolute elements are always relative to the closest container that is a positioned element. It only falls back to being relative to the browser when none of its ancestors are positioned. So, if we change ```.item-absolute```’s parent element to be relatively positioned, it should appear in the top-left corner of that element instead of the browser window.
<br/>
We’re using relative positioning of ```.absolute``` for the sole purpose of letting our absolute element hook back into the normal flow of the page. This is how we safely combine absolute positioning with static positioning.

<img src="https://www.internetingishard.com/html-and-css/advanced-positioning/relatively-absolute-positioning-screenshot-98bcce.png" width="400px">

### Fixed Positioning

“Fixed positioning” has a lot in common with absolute positioning: it’s very manual, the element is removed from the normal flow of the page, and the coordinate system is relative to the entire browser window. The key difference is that fixed elements don’t scroll with the rest of the page.

### Positioned Elements for Animation 

Animation is one of the primary use cases for relative and absolute positioning. These advanced positioning schemes allow JavaScript to move elements around while avoiding any kind of interaction with surrounding elements. The JavaScript code creates a simple animation that continually updates the ```left``` property of the ```.item-relative```. 

<img src="https://www.internetingishard.com/html-and-css/advanced-positioning/animated-relative-positioning-193400.png" width="400px">

If you were to try to achieve the same effect by manipulating the ```margin``` or ```padding``` properties, you would inadvertently move the statically positioned boxes and/or the containing ```.example``` element, too.
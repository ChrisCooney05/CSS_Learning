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
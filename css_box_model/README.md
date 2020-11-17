# Content, Padding, Border and Margin

The “CSS box model” is a set of rules that determine the dimensions of every element in a web page. It gives each box (both inline and block) four properties:

- **Content** - The text, image, or other media content in the element
- **Padding** - The space between the box's content and its border
- **Border** - The line between the box's padding and margin
- **Margin** - The space between the box and the surrounding boxes.

![box_model](https://www.internetingishard.com/html-and-css/css-box-model/css-box-model-73a525.png)

# Content Boxes and Border Boxes

The width and height properties only define the size of a box’s content. Its padding and border are both added on top of whatever explicit dimensions you set. Fortunately, CSS lets you change how the width of a box is calculated via the box-sizing property.

![content_box](https://www.internetingishard.com/html-and-css/css-box-model/box-sizing-content-box-09f48a.png)
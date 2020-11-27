# Responsive Images

This section will be building off what was produced in [responsive-design](https://github.com/ChrisCooney05/CSS_Learning/tree/master/responsive-design). We’ll be adding two images to the page that will change depending on the user’s device. 

### Retina Screens

Retina screens have twice as many pixels per inch than standard-resolution screens. That is to say, each retina pixel is the equivalent of 4 standard pixels. This has a big impact on how images are displayed in a web browser. To render correctly on a retina device, an image needs to be twice as big as its final display dimensions. For example, if you want to add a 500×250 pixel image to the page, the corresponding image file needs to be 1000×500 pixels.

<img src="https://www.internetingishard.com/html-and-css/responsive-images/retina-2x-image-dimensions-5a4673.png" width="400px">

This is actually a bit of a simplification—not all retina screens are created equal. For instance, the iPhone 6 Plus has three times as many pixels per inch as a standard screen, but the same techniques apply to 3x retina screens as well.
<br/>
What’s more, standard displays and smaller devices don’t need all those extra pixels in high-resolution images, and sending that much unnecessary data usually results in a bad user experience.
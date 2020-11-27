# Responsive Images

This section will be building off what was produced in [responsive-design](https://github.com/ChrisCooney05/CSS_Learning/tree/master/responsive-design). We’ll be adding two images to the page that will change depending on the user’s device. 

### Retina Screens

Retina screens have twice as many pixels per inch than standard-resolution screens. That is to say, each retina pixel is the equivalent of 4 standard pixels. This has a big impact on how images are displayed in a web browser. To render correctly on a retina device, an image needs to be twice as big as its final display dimensions. For example, if you want to add a 500×250 pixel image to the page, the corresponding image file needs to be 1000×500 pixels.

<img src="https://www.internetingishard.com/html-and-css/responsive-images/retina-2x-image-dimensions-5a4673.png" width="400px">

This is actually a bit of a simplification—not all retina screens are created equal. For instance, the iPhone 6 Plus has three times as many pixels per inch as a standard screen, but the same techniques apply to 3x retina screens as well.
<br/>
What’s more, standard displays and smaller devices don’t need all those extra pixels in high-resolution images, and sending that much unnecessary data usually results in a bad user experience.

### Responsive SVG

The easiest way to solve all these problems is with SVG images. They “just work.” Since they’re vector-based, SVGs avoid screen resolution problems. Browsers automatically scale up SVGs for retina devices, so this 500×250 pixel SVG image will render crisply on both standard and retina devices.
<br/>
SVGs let us forget about screen resolution issues, but we do need to shrink the illustration to fit neatly into our fluid tablet and mobile layouts. Firefox will do this automatically, but if you open this page with Chrome and make your browser very narrow, you’ll find that the image stays the same size.
<br/>
When we specify 100% width on an image, it’ll assume we want to maintain its aspect ratio and calculate its height automatically. This fixes the mobile layout, but now the desktop version is huge:

<img src="https://www.internetingishard.com/html-and-css/responsive-images/responsive-svg-image-bfa291.png" width="400px">

We can cap the size of the image at ```500px``` with an inline style. This is one of the rare times an inline style is acceptable, due to the fact that it’s describing an innate property of the image. An image’s physical dimensions are more content than presentation, so it makes sense for this to appear in the HTML rather than the stylesheet.

### Responsive PNG, GIF, and JPG

Sometimes you need to include a photo. PNG, GIF, and JPG images are “raster images”, meaning that they are defined pixel-by-pixel instead of with vectors. As a result, they are much more sensitive to screen resolution than SVGs. If you’re not worried about optimization, responsive raster images really aren’t that much harder than using SVG images. By using the image with ```-big``` suffix, we are using the high-resolution version of the PNG, which has dimensions of 1000×500. Retina devices need this “2x” size to display the image crisply. If we were to use the low-resolution version of this image (500×250 pixels), it would look fine on standard screens, but fuzzy on retina devices.

<img src="https://www.internetingishard.com/html-and-css/responsive-images/retina-responsive-images-9f367b.png" width="400px">

This the lazy way to create responsive PNG, GIF, or JPG images, as it assumes everybody needs a high-resolution image, even if they don’t. That is to say, a 1000×500 pixel image is overkill for non-retina devices.
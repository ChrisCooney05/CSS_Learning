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

### Responsive Image Optimization

Different devices have different image requirements. Fortunately, HTML provides a way to choose the best image for the user’s device. We’ll take a look at three scenarios for optimizing responsive images:

  - A standard-resolution screen that doesn’t need a retina-quality image.
  - A retina mobile device that can use a standard-quality image because it’s been scaled down so much.
  - A desktop layout that uses a wide image, and an associated mobile layout that uses a taller image.

The first method is the easiest, and it’s great for images smaller than 600 pixels wide because they aren’t big enough to benefit from the second scenario. The second method is a very important optimization for larger images, especially full-bleed photos. The third is for when you’re feelin’ fancy.

### Retina Optimization Using srcset

High-resolution images are big. Our ```illustration-big.png``` file takes up more than twice as much disk space as its low-resolution counterpart. It doesn’t make sense to serve all that extra data when the user doesn’t actually need it. Adding a ```srcset``` attribute to our &lt;img/&gt; element lets us present our high-resolution image only to retina devices, falling back to the low-resolution version for standard screens.
<br/>
The ```srcset``` attribute points to a list of alternative image files, along with properties defining when the browser should use each of them. The 1x tells the browser to display ```illustration-small.png``` on standard-resolution screens. The 2x means that ```illustration-big.png``` is for retina screens. Older browsers that don’t understand ```srcset``` fall back to the ```src``` attribute.

<img src="https://www.internetingishard.com/html-and-css/responsive-images/retina-responsive-images-with-srcset-707397.png" width="400px">

Typically, the low-res and high-res versions of an image would be the exact same (except for their dimensions), but we made illustration-small.png yellow so you can easily differentiate it from the retina version, which is blue.
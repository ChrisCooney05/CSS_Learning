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

### Screen Width Optimization Using srcset

The above srcset technique misses an important use case for larger images: if the user has a retina smartphone, it’ll download the high-resolution image even when the standard version would suffice.
<br/>
Imagine that we wanted to display a big photo in our .header element. The header is 960 pixels wide in our desktop layout, so our photo needs to be at least 1920 pixels wide to display well on retina screens. Now, consider a smartphone with a retina screen. Smartphones are typically less than 400 pixels wide in portrait mode, which means that the corresponding retina-quality image would only need to be 800(ish) pixels wide.

<img src="https://www.internetingishard.com/html-and-css/responsive-images/screen-width-optimization-with-srcset-6dd918.png" width="400px">

The lesson here is that we want to optimize larger images based on their final rendered dimensions, not just the device’s screen resolution.
<br/>
We have the same ```srcset``` element as the last section, but instead of the 1x and 2x descriptors, we’re providing the inherent physical width of the image. The ```2000w``` tells the browser that the ```photo-big.jpg``` file is 2000 pixels wide. Likewise, the ```1000w``` means ```photo-small.jpg``` has a width of 1000 pixels. The w character is a special unit used only for this kind of image optimization scenario.

<img src="https://www.internetingishard.com/html-and-css/responsive-images/img-srcset-physical-width-2153b0.png" width="400px">

Image width alone isn’t enough for a device to determine which image it should load. We also need to tell it what the final rendered width of the image will be. That’s where the ```sizes``` attribute comes in. It defines a series of media queries along with the image’s rendered width when that media query is in effect. In our ```.header``` &lt;img&gt; we’re saying that when the screen is at least ```960px``` wide, the image will also be 960 pixels wide. Otherwise, the ```100vw``` default value tells the browser that the image’s width will be 100% of the “viewport width” (a fancy term for screen width).
<br/>
Remember that our low-resolution photo is 1000 pixels wide, which means that 2x retina devices can use it as long as their screen is less than 500 pixels wide. We’re now serving a 115KB image to mobile devices instead of forcing them to use the high-res 445KB image. That’s a big deal, especially for websites that use a lot of photos.
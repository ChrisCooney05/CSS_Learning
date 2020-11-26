# Responsive Design

“Responsive design” refers to the idea that your website should display equally well in everything from widescreen monitors to mobile phones. It’s an approach to web design and development that eliminates the distinction between the mobile-friendly version of your website and its desktop counterpart. With responsive design, they’re the same thing.
<br/>
Responsive design is accomplished through CSS “media queries”. Think of media queries as a way to conditionally apply CSS rules. They tell the browser that it should ignore or apply certain rules depending on the user’s device.

<img src="https://www.internetingishard.com/html-and-css/responsive-design/how-responsive-websites-work-5f0a33.png" width="400px">

### Media Queries

A good place to start is to change the background colour based on screen size. This is a good way to make sure our media queries are actually working before getting into complicated layouts. 

<img src="https://www.internetingishard.com/html-and-css/responsive-design/simple-responsive-media-queries-703f8b.png" width="400px">

Media queries always begin with the @media “at-rule” followed by some kind of conditional statement, and then some curly braces. Inside the curly braces, you put a bunch of ordinary CSS rules. The browser only pays attention to those rules if the condition is met.

<img src="https://www.internetingishard.com/html-and-css/responsive-design/media-query-terms-137d06.png" width="400px">

The ```only screen``` “media type” means that the contained styles should only be applied to devices with screens (opposed to printed documents, like when you hit Cmd+P in a browser). The ```min-width``` and ```max-width``` parts are called “media features”, and they specify the device dimensions you’re targeting. Whilst these are the most common, there are [loads more](https://developer.mozilla.org/en-US/docs/Web/CSS/@media) including whether the device is in portrait or landscape mode, the resolution of its screen, and whether it has a mouse or not.

There’s a few well [defined patterns](https://developers.google.com/web/fundamentals/design-and-ux/responsive/patterns?hl=en) for how a desktop layout collapses into a mobile layout (ours is “layout shifter”) and there are two concepts that you must understand as a developer:

<img src="https://www.internetingishard.com/html-and-css/responsive-design/mobile-first-design-be30e4.png" width="400px">

- A “fluid” layout is one that stretches and shrinks to fill the width of the screen, just like the flexible boxes we covered a few chapters ago.
- A “fixed-width” layout is the opposite: it has the same width regardless of the screen dimensions 

<img src="https://www.internetingishard.com/html-and-css/responsive-design/fixed-width-vs-fluid-layouts-258df9.png" width="400px">

In responsive.html the mobile and tablet versions are fluid, and the desktop version is fixed-width.

### Note on Breakpoints

Most of those responsive design patterns have similar behavior, using fluid layouts for mobile/tablet devices and fixed-width layouts for wider screens. There’s a reason for this.

Fluid layouts let us target a range of screen widths instead of specific mobile devices. This is very important for web designers. When they set out to create a mobile layout, they aren’t trying to make something that looks good on an iPhone 6s, Galaxy S7, or iPad mini—they’re designing a fluid layout that looks good anywhere between 300 pixels and 500 pixels (or whatever).

In other words, the exact pixel values for the min-width and max-width parameters in a media query (collectively known as the “breakpoints” for a responsive website) don’t actually matter. Our website doesn’t care about the specific device the user is on. All it needs to know is that it should display a layout that looks pretty at 400 pixels wide (or whatever).

### Mobile-First Development

It’s always a good idea to start with the mobile layout and work your way up to the desktop version. Desktop layouts are typically more complex than their mobile counterparts, and this “mobile-first” approach maximizes the amount of CSS that you can reuse across your layouts.
<br/>
By adding base styles outside of the media queries and making the screen smaller we already have the mobile layout done. No media queries required. That’s why it’s called “mobile-first”—the mobile version doesn’t require any special handling.   

<img src="https://www.internetingishard.com/html-and-css/responsive-design/mobile-layout-55fdad.png" width="400px">

By keeping these base styles outside of the media queries, we’re able to override and add on to them as we implement our specific layouts. This is really convenient when, for instance, your designer wants to tweak the color scheme for the entire website. Instead of tracking down redundant ```background-color``` declarations in several ```@media``` rules, you only have to update it here. That change automatically applies to the mobile, tablet, and desktop layouts.

### Tablet Layout

The only difference between the mobile and tablet mockups is that the Sign Up and Feature sections form a 2×2 grid instead of a single column. Because of ```.page``` having the ```flex-wrap: wrap``` property, this will be easy to add. By Simply adjusting the widths of the flex items to be half the screen and ```flex-wrap``` will take care of the rest. This should only apply to tablets so needs to go in a ```@media``` rule. 

<img src="https://www.internetingishard.com/html-and-css/responsive-design/tablet-layout-081d9e.png" width="400px">

Again, it doesn’t matter what the exact width of the screen is: this layout will fluidly respond to any width in the media query’s range.

### Desktop Layout

We don’t want our web page to expand endlessly, so we’re going to give it a fixed width and center it with auto-margins. As with tablet styles, this needs to go into a media query. Finally, the desktop layout calls for some reordering: the Sign Up and Content boxes should appear underneath all the Feature sections.

<img src="https://www.internetingishard.com/html-and-css/responsive-design/desktop-layout-8479d0.png" width="400px">

Finally, we can use flexbox's ```order``` property, to correctly order our page. by setting ```.sign-up``` to ```order: 1``` and ```.content``` to ```order: 2``` we can easily reorder the page without effecting all elements. 

### Disabling Viewport Zooming

Before responsive design was a thing, mobile devices only had a desktop layout to work with. To cope with this, they zoomed out to fit the entire desktop layout into the width of the screen, letting the user interact with it by zooming in when necessary. This default behavior will prevent mobile devices from using our mobile layout. To disable it, add the following element to the &lt;head&gt; of our document.
```html
<meta name='viewport'
      content='width=device-width, initial-scale=1.0, maximum-scale=1.0' />
```
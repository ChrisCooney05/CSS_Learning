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
# Typography

Around 2010, browsers began supporting custom web fonts, which was great, except for the fact that each browser and device required a different file format. Accordingly, most websites provided 4 different web font files:

| File  | Format Browser/Device               |
| ----- | ----------------------------------- |
| .svg  | Very old Safari (iOS and Desktop)   |
| .eot  | Internet Explorer                   |
| .ttf  | Everything except Internet Explorer |
| .woff | Newer browsers                      |

This resulted in the [“Bulletproof @font-face syntax”](https://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/)

### WOFF fonts

The industry has standardized on the Web Open Font Format (WOFF), so things have gotten a little bit simpler for us. Over 98% of modern browsers support .woff fonts, and over 95% for .woff2.

### Locally Hosted Web Fonts

There are two distinct methods of adding web fonts to your website: locally hosted or externally hosted. To add a locally hosted web font there are three steps:

- Download a web font and add it to your project.
- Embed the web font in your stylesheet.
- Use the font elsewhere in your stylesheet.

### Embedding A Web Font

We’ve got a WOFF file. To actually use it in our web page, we need to embed it into our stylesheet with the `@font-face` “at-rule”. Web fonts must always be included at the top of a stylesheet
<br/>
The `font-family` property defines how we’ll refer to this font later on. This operates as an internal label, so it can be anything you want. the `src` property, which defines the path to the .woff file via the url() notation. The path can be absolute, relative, or root-relative. `@font-face` only gave us access to our .woff file. We still need to use it somewhere else in our stylesheet.

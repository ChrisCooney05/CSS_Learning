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

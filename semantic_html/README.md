# Semantic HTML

“Semantic HTML” refers to the idea that all your HTML markup should convey the underlying meaning of your content—not its appearance. There’s a whole set of elements designed for the sole purpose of adding more meaning to the overall layout of a web page. They’re called “sectioning elements”.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/html-sectioning-elements-00c3fd.png" width="400px">

Using these as an alternative to &lt;div&gt; elements is an important aspect of modern web development because it makes it easier for search engines, screen readers, and other machines to identify the different parts of your website. It also helps you as a developer keep your site organized, which, in turn, makes it easier to maintain.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/semantic-html-ffab7c.png" width="400px">

### Document Outline

Every HTML document has an “outline,” which is how search engines and screen readers view the hierarchy of the content on the page. The &lt;h1&gt; through &lt;h6&gt; heading elements all contribute to a page’s document outline.

The [HTML5 Outliner](https://gsnedders.html5.org/outliner/) is a convenient tool for inspecting the document outline of a page.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/document-outline-heading-elements-576433.png" width="400px">

Each &lt;h1&gt; element creates a new section in the document outline, and any less prominent headings that follow it are considered subsections under that top-level heading. E.g., the Semantic HTML section has two subsections in it: The Document Outline and Inline Semantic HTML. The same goes for &lt;h2&gt; and &lt;h3&gt; elements, and so on down to &lt;h6&gt;. Note that the actual value of the heading level doesn’t matter: what’s important is whether or not it’s greater than or less than the heading of the current section.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/document-outline-section-creation-45ee48.png" width="400px">

How’s this document outline stuff relate to semantic HTML? Well, headings are some of the most semantic things in a web page. They play a significant role in how search engines determine what’s important in your web page. In addition, semantic HTML elements add more meaning to and sometimes even alter the default outlining behavior discussed here.

### Articles 

The &lt;article&gt; element represents an independent article in a web page. It should only wrap content that can be plucked out of your page and distributed in a completely different context. For instance, an app like d[Flipboard](https://flipboard.com/) should be able to grab an &lt;article&gt; element from your site, display it in its own app, and have it make perfect sense to its readers.
<br/>
By Wrapping the blog post in an &lt;article&gt; element we are marking it as the main content of the page as a self-contained unit. Notice how we left the copyright notice outside the &lt;article&gt; element because it’s a footer for the entire site—not specifically for our article.
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

<img src="https://www.internetingishard.com/html-and-css/semantic-html/html-article-element-82490e.png" width="400px">

By Wrapping the blog post in an &lt;article&gt; element we are marking it as the main content of the page as a self-contained unit. Notice how we left the copyright notice outside the &lt;article&gt; element because it’s a footer for the entire site—not specifically for our article.
<br/>
&lt;article&gt;’s are essentially mini web pages in your HTML document. They have their own headers, footers, and document outline that are completely isolated from the rest of your site.

### Using Multiple Article Elements

For things like blog posts, newspaper articles, or web pages dedicated to a single topic, there’s often only one &lt;article&gt; element on the page. But, it’s perfectly legal to have more than one &lt;article&gt; element per page. A good example is a page that displays a bunch of blog posts. Each one of them can be wrapped in a separate set of &lt;article&gt; tags.

```html
<article>
  <h1>First Post</h1>
  <p>Some content</p>
</article>
<article>
  <h1>Second Post</h1>
  <p>Some more content</p>
  <h2>Subsection</h2>
  <p>Some details</p>
</article>
<article>
  <h1>Last Post</h1>
  <p>Final bit of content</p>
</article>
```

This tells anybody looking at our page that there are three distinct articles that can be syndicated. Think of it as a way to merge multiple HTML files into a single document without confusing search engines, browsers, or other machines that are trying to parse our content.

### Sections

The &lt;section&gt; element is sort of like an &lt;article&gt;, except it doesn’t need to make sense outside the context of the document. That is, an app like Flipboard wouldn’t try to pull out all the &lt;section&gt;’s of your page and present them as independent pieces of content.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/html-section-element-92a4d1.png" width="400px">

Think of &lt;section&gt; as an explicit way to define the sections in a document outline. Why would we want this instead of letting the heading levels do it for us? Often times, you need a container to wrap a section for layout purposes, and it makes sense to use the more descriptive &lt;section&gt; element over a generic &lt;div&gt;.
<br/>
By changing the last &lt;h2&gt; into a &lt;h6&gt; you might expect it to become part of the Footer section as its lower than the &lt;h3&gt; that proceeds it. But, that’s not the case. 

<img src="https://www.internetingishard.com/html-and-css/semantic-html/sections-and-document-outline-614f12.png" width="400px">

By adding those &lt;section&gt; elements, we’re telling the document outline that it should be defined by the nesting structure of the &lt;section&gt; elements instead of the heading levels. This basically means that each &lt;section&gt; can have its own set of <h1> through <h6> headings that are independent of the rest of the page.
<br/>
However, you shouldn’t use the &lt;section&gt; element to manipulate the document outline in this way because browsers, screen readers, and some search engines don’t properly interpret the effect of &lt;section&gt; on the document outline. Instead, always define a page’s outline via heading levels, using &lt;section&gt; only as a replacement for container &lt;div&gt;’s when appropriate.
Also note that each &lt;section&gt; element should contain at least one heading, otherwise it will add an “untitled section” to your document outline.
<br/>
As defined by the HTML5 specification, &lt;section&gt; is a pretty generic element. That, plus the fact that browsers and screen readers can’t properly interpret its role in document outlines makes it difficult to know when and how to leverage it properly. Only use &lt;section&gt; as a more descriptive &lt;Div&gt; wrapper for the implicitly defined sections of your page. Don’t use it for self-contained content (that’s what &lt;article&gt; is for) or when it’s purely for layout purposes.

### Navs

The &lt;nav&gt; element lets you mark up the various navigation sections of your website. This goes for the main site navigation, links to related pages in a sidebar, tables of content, and pretty much any group of links. This is a great piece of semantic information for search engines. It helps them quickly identify the structure of your entire website, making it easier to discover other pages. It’s possible to include multiple &lt;nav&gt; elements on a single page if you have different sets of related links.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/html-nav-element-d1e716.png" width="400px">

### Headers

The &lt;header&gt; element denotes introductory content for a section, article, or entire web page. “Introductory content” can be anything from your company’s logo to navigational aids or author information. It’s a best practice to wrap a website’s name/logo and main navigation in a &lt;header&gt;.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/html-header-element-7b4e01.png" width="400px">

Headers are only associated with the nearest sectioning element—typically a &lt;body&gt;, &lt;section&gt;, or &lt;article&gt; element. This means that you can use multiple &lt;header&gt; elements to add introductory content to different parts of a document. For instance, the title, author, and publication date of our &lt;article&gt;
<br/>
Without this &lt;header&gt;, search engines and screen readers wouldn’t know that first &lt;p&gt; was separate from the main content of the article. Like &lt;section&gt;, it also serves as a convenient CSS hook, since the title and author info for a blog post are often styled differently than the rest of the article. Again, think of &lt;header&gt; as a more semantic alternative to a &lt;div&gt; container.

### Footers

Conceptually, footers are basically the same as headers, except they generally come at end of an article/website opposed to the beginning. Common use cases include things like copyright notices, footer navigation, and author bios at the end of blog posts.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/html-footer-element-0c927a.png" width="400px">

Footers behave the same as &lt;header&gt; in that they’re associated with the nearest sectioning element. So, we can use it for our page’s copyright notice and the author information inside our &lt;article&gt;.

### Asides

Headers and footers are ways to add extra information to an article, but sometimes we want to remove information from an article. For example, a sponsored blog post might contain an advertisement about the sponsoring company; however, we probably don’t want to make it part of the article text. This is what the &lt;aside&gt; element is for.

<img src="https://www.internetingishard.com/html-and-css/semantic-html/html-footer-element-0c927a.png" width="400px">

Even though the image is inside the &lt;article&gt; element, machine readers know that it’s only tangentially related to the article content. In addition to advertisements, &lt;aside&gt; is also appropriate for highlighting definitions, stats, or quotations. If it looks different than the rest of the article, chances are it’s an aside. When used outside an &lt;article&gt;, an &lt;aside&gt; is associated with the page as a whole. This makes it a good choice for marking up a site-wide sidebar.
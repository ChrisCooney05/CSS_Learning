# CSS Selectors

### Pseudo-classes for links

CSS “pseudo-classes” provide a mechanism for hooking into this kind of temporary user information. At any given time, an &lt;a href&gt; element can be in a number of different states, and you can use pseudo-classes to style each one of them individually. Think of them as class selectors that you don’t have to write on your own because they’re built into the browser.
<br/>
Pseudo-classes begin with a colon followed by the name of the desired class. The most common link pseudo-classes are as follows:

- **:link** - A link the user has never visited.
- **:visited** - A link the user has visited before.
- **:hover** - a link with the user's mouse over it.
- **:active** - A link that's being pressed down by a mouse.

### Caveats

Ok, so actually the pseudo-class method is a little more complicated. They’re still a useful tool—as long as you know their ins-and-outs. The :first-of-type and :last-of-type selectors only operate inside their parent element. That is to say, p:first-of-type selects the first &lt;p&gt; in every container element.
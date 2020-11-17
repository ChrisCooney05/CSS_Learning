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

### CSS Specificity

Unfortunately, not all CSS selectors are created equal. “CSS specificity” is the weight given to different categories of selectors. This means that certain selectors will always override other ones, regardless of where they appear in the stylesheet.
<br/>
ID selectors have higher specificity than class selectors, so this will turn our second button red even though we try to set the background-color with .call-to-action:link later in our stylesheet. The whole “order matters” concept only works when all your rules have the same specificity.

<img src="https://www.internetingishard.com/html-and-css/css-selectors/css-specificity-and-rule-order-ec25f3.png" width="500px">

The specificity of selectors we’ve seen in this chapter are show below, from greatest to least:

- #button-2
- .button:link
- a:link and .synopsis em (they’re equal)
- .button
- a
  
This can get very confusing. It’s such a big problem that an entire methodology called [“BEM”](http://getbem.com/introduction/) has evolved. BEM attempts to make CSS rules more reusable by making everything a class selector. This completely eliminates the potential for specificity issues.
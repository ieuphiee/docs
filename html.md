## HTML
### What is a doctype?
Stands for “document type”, tells the browser what version of HTML the document is written so the browser knows what to expect. Defines things like whether a button can contain a span or not. Every HTML document must have a doctype, is the first line that appears in the webpage.

### What are data- attributes good for?
Used to store custom data on HTML elements when there are no appropriate attributes that can be used. Can be useful as hooks for end-to-end testing frameworks such as Selenium that need to be able to quickly identify elements on a page to test.

### Describe the difference between a cookie, sessionStorage and localStorage.
All 3 technologies are ways to cache information on the client side.
![image](https://user-images.githubusercontent.com/24919123/139177812-31799200-5122-44d5-9d5c-e81c313b55f6.png)

 
### Describe the difference between `<script>`, `<script async>` and `<script defer>`
- Script – script is fetched & executed immediately, and HTML parsing gets blocked (“waits”) until the script finishes loading
- Script async – script is fetched in parallel to HTML parsing, will be executed as soon as it’s available, good to use when a script has no dependency on other scripts 
- Script defer – script is fetched in parallel to HTML parsing, will be executed after the entire page has finished parsing, good to use when a script relies on a fully-parsed dom (like manipulating DOM elements). Same as placing a script at the end of <body> tag.

### What is progressive rendering?
Techniques for improving performance of a webpage (perceived load time), such as:
- Lazy loading images – images on the page are not loaded all at once, JS will be used to load an image as the user encounters them on the page
- Prioritizing visible content – load the bare minimum HTML and stylesheets for displaying the amount of the page the user would see on his/her browser, progressively load other html/styles as user encounters them
CSS

### What is CSS selector specificity and how does it work?
CSS specificity refers to which CSS rule is applied by the browser. If two selectors apply to the same element, the one with the higher specificity wins. Some rules that govern which selector has the highest precedence:
-	When 2 selectors have the same level of specificity, the latest one WINS.
-	The selector with the highest specificity wins
-	ID selectors > attribute selectors
-	Class selectors > element selectors
-	Inline styles > classes
-	!important wins all
Generally, it is good practice to write selectors with low specificity so that they can be easily overwritten, this is especially true if you’re writing a UI components library. 

### Describe floats and how they work.
Float is a CSS positioning property; floated elements remain a part of the page flow and will not affect the positioning of other elements (text will “wrap” around floated elements).

Float can have 4 values: left, right, none, inherit.
Float’s sister property is clear. An element that has the clear property set on it will not move adjacent to the float but will move itself down past the float.

One interesting issue with floats is that if you have a container with all floated elements, the height of the container “collapses to nothing” (zero height). To fix this, one can clear the float after the floated elements but before the close of the parent container. 

This is a better alternative to setting overflow: auto / hidden on the parent container.
 
### Describe z-index and how stacking context is formed.
Determines the vertical stacking order of elements, only works on elements that do not have position: static. Without explicit z-index, elements stack in the order they appear in the DOM.

### How would you approach fixing browser-specific styling issues?
-	Identify offending browser
-	Create a separate stylesheet containing styles just for that browser
-	Use an autoprefixer which automatically applies browser/vendor prefixes for you 
What are the different ways to visually hide content (and make it available only for screen readers)?
-	Set width and height to 0, essentially taking up no space
-	Position: absolute, left: -999999
-	Aria tags

### Can you give an example of an @media property other than screen?
-	All – for all media type devices
-	Screen – computers, tablets, mobile devices
-	Print – for printers
-	Speech – for screen readers

### What are the advantages/disadvantages of using CSS preprocessors?
A CSS preprocessor compiles code into plain CSS, an example would be if you Sass/SCSS, node-sass or dart-sass is the preprocessor.
-	Easy to write nested selectors
-	More maintainable code
-	Speeds up development, reduce repeated code using features like variables and mixins (functions)
-	Compilation takes time

### Describe pseudo-elements and discuss what they are used for.
A keyword added to a selector that lets you style a specific part of the element. Can be used for decorative purposes or for adding additional elements to the markup w/o having to modify the markup (insert content onto a page w/o it needing to be in the HTML).
```
div::before {
  content: "before";
}
div::after {
  content: "after";
}
```
 
### What is box model?
Every HTML element can be considered a “box”. The box model wraps around every HTML element and consists of margins, borders, padding, and the actual content. 
-	Determines the size that a block element takes, the size of the box, whether borders and/or margins overlap
What is box-sizing: border-box?
Border-box is a type of box model. By default, elements have box-sizing: content-box.
-	Content-box: the size of the box only considers the size of the content
-	Border-box: size of the box includes content+padding+borders

### What is the display property? Give some examples of types of display property values.
Describes display behavior (the type of rendering box)
-	Block: element takes up whole line, starts on a new line
-	None: element does not display, as if element doesn’t exist
-	Inline: elements laid out beside each other
-	Inline-block: same as inline but allows setting width and height 
-	Flex: flex box

### What's the difference between a relative, fixed, absolute and statically positioned element?
-	Static: default position, element flows on the page as it normally would (right next to each other)
-	Relative: same thing as static, but allows you to specify an offset from where it would normally sit on the page (offset is relative to where it would normally be placed in the flow), often used in conjunction with position: absolute to position absolutely-positioned elements relative to the relative-positioned element
-	Absolute: removes element from the flow of the page, offset is relative to the closest relatively positioned element (if none, then relative to the document)
-	Fixed: removes element from the flow of the page, positioned relative to the viewport and doesn’t move when scrolled

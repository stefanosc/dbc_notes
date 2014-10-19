# HTML and CSS CHEATSHEET

### Elements, Tags and Attributes

```
a, div, span, strong -> elements
<a> -> tags
id, class, src, href -> attributes
<a href="http://www.google.com">Google</a>
```
### Basic HTML Template

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Hello world</title>
  </head>
</html>

```
### Referencing CSS, headings, strong, b, em and i elements

```
<link rel="stylesheet" href="main.css">
<h1>,<h2>,.....<h6>
<strong> -> strong emphasis
<b> -> stylistically offset text
<em> -> stressed emphasis
<i> -> alternative voice or tone
```
### HTML5 elements

```
<header> -> heading of a segment of a page
<nav> -> Identifies a section of major navigational links on a page.
<article> -> To identify a section of independant, self contained content.
<section> -> To identify a thematic grouping of content
<aside> -> Appears off to the left/right of a page. Holds content such as sidebars
           and brief explanations related to the content surrounding it.
<footer> -> Identifies the closing or end of a page,article, section or other segment
            of a page.
<small> -> content within <small> is rendered as small.

```
### Relative Paths and Absolute Paths

```
Relative Path: Links pointing to other pages of the same website will have relative path.
Absolute Path: Links to other websites requires an absolute path.

<a href="../about.html">About</a>  -> Relative path
<a href="http://www.google.com">Google</a> -> Absolute path
```
### Linking to Email Address

```
href attribute value should be mailto:shambu1985@gmail.com
The first parameter following the email address must begin with a question mark(?) to bind it to
the hyper link.. Multiple words within a subject line require that spaces be encoded with %20.
When binding one parameter to another, use the ampersand & to separate the two. Line breaks must
be encoded with %0A.

<a href="mailto:shambu1985@gmail.com?subject=Reaching%20Out&body=How%20are%20you">Email Me</a>
```
### Opening links in a new window:

```
<a href="http://www.google.com" target="_blank">Hello</a>
```
### Linking to Parts of the same page:

```
<body id="top">
  ...
  <a href="#top">Back to Top</a>
  ...
</body>
```

### Specificity

```
All styles cascade from top to bottom in the .css file.<br/>
Specificity order: id>class>type.<br>

Higher the specificity weight, the more superiority the selector is given when a..
styling conflict occurs.
Point value of class selector is : 0-1-0
Point value of type selector is : 0-0-1
Point value of id selector is : 1-0-0
Combined value of all selectors is : 1-1-1


To select only the paragraph elements having a class of musturd that belongs to
the class of hotdog:
CSS will be .hotdog p.musturd { }  , specificity weight is : 0-2-1
.hotdog p {} , specificity weight is 0-1-1. So .hotdog p.musturd { } has higher
specificity than .hotdog p {}
When selectors are combined, they are read from right to left. p.musturd is the
key selector and .hotdog is the pre-qualifier.

```
### Colors

```
Colors: keyword colors, rgb, rgba, hexadecimal colors
rgba(0 to 255, 0 to 255, 0 to 255, alpha is transparency (0 to 1)) 0- fully
transparent, 1- fully opaque

hsla(0 to 360 (degree of color), 0 to 100%,0 to 100%,alpha- transparency(0 to 1))
 - saturation : 0 - grayscale, 100 - fully saturated.
 - brightness : 0 - completely dark, 100 - completely white.

```
### Lengths

```
Lengths: px, percentage, em
1em = font-size eg: 5em  = 5 * font-size of element.
If element's font size not specified, then 1em = font-size of closest parent element.

```

### Display: block, inline, inline-block

```
inline-block will behave like a block-level element taking all box-model properties.
eg: P1 P2 P3
Usually a small space will exist between the inline-block elements by default.

display: block/inline-block/inline/none ;  none hides the element completely.

```
### Margin

```
Margin only work horizontally left and right on inline level elements.
Padding works on all four sides of inline level elements.

margin: top/bottom left/right
margin: top right bottom left

Longhand: margin/padding/border-left/right/top/bottom
```
### Border

```
border: width style color
Longhand - border-width/style/color : width/style/color

eg: border-bottom-width: width_value

border-radius: top-left/top-right/bottom-right/bottom-left
border-radius: top-left top-right bottom-right bottom-left

Longhand: border-top-left-radius: value

```
### Box-sizing

```
-webkit-box-sizing: content-box/padding-box/border-box
content-box is the default box-sizing - included just width and height
padding-box - includes padding + width/height
border-box - includes border + padding + width/height

Best box-sizing to use is the border-box.
```
### Floating properties

```
float : left/right

eg: section { float: left ; width: 30% ; margin: 1 1.5% }

To clear floats, use the clear property, clear: left/right/both

```

### Containing floats:

```

<div class="group">
    <section> ... </section>
    <aside> ... </aside>
</div>

.group:before,
.group:after { content: ""; display:table; }
.group:after { clear:both; }
.group {  clear:both; *zoom : 1; }
section {  float:left ; margin: ... ; width: ... ; }
aside {  float:right ; margin: ... ; width: ... ; }

```
### Another alternative: Using inline-block

```
Another alternative is to use inline-block. Using inline-block elements, allows us to take full advantage
of the box model without having to worry about floating elements.

section { display: inline-block ; margin: ... ; width: ... ; }

To remove default white space between inline block elements:

 <section>
  ..
</section><!--
--><section>
...
</section>

```
### Relative and Absolute positioning

```
Relative positioning means elements are positioned with respect to their original position. It preserves
the original position of the element. Absolutely positioned elements are moved in relation to their closest
relatively positioned parent element.
Original position will not be preserved and other elements can occupy that position.

position: relative                  position:absolute;
top/bottom/left/right: 20px;        top/left/right/bottom: 20px

```
### Font

```
font-family: "Helvetica Neue", Helvetica;
font-size: 14px;
font-style: normal/italic/oblique/inherit;
font-variant: normal/small-caps/inherit;
font-weight: normal/bold/bolder/lighter/inherit/0 to 900;
line-height: 22px/150%/1.5;

Shorthand:
font: font-style font-variant font-weight font-size/line-height font-family

```
### CSS pseudo-classes:

```
a:hover { }
```
### Applying text properties:

```
text-align: left/right/center/justify/inherit;
text-decoration: none/underline/overline/line-through/inherit
text-indent: 20px ; Positive values aligns text inward, negative values aligns text outward
text-shadow: horizontal_offset vertical_offset blur_radius shadow_color
(text-shadow: 3px 6px 2px rgba(0,0,0,0.3));
horizontal offset is distance from the left. vertical offset is distance from the right.
negative values for horizontal and vertical offset move the shadows towards the left and right.
Multiple text shadows can also be chained together using comma separated values, adding one more
shadow to the text.

box-shadow: inset horizontal_offset vertical_offset blur_radius shadow_spread shadow_color;
positive length value: spread will expand the shadow larger than the size of the element.
negative length value: spread will shrink the shadow smaller than the size of the element.

text-transform: none/capitalize/uppercase/lowercase/inherit;

letter-spacing: -.5em; letters will appear 0.5em closer to each other.
word-spacing: .25em; every word will be spaced 0.25em apart.
```

### Cite, q and blockquote elements

```
<cite> - used to reference a creative work, author or resource
(title of work/author's name/URL reference). Content wrapped within <cite>
will appear in italics within the browser.
<q> - used for short inline quotations(dialogue or prose)
<blockquote> - used for longer external quotations

Optional attribute to include in the <q> is the cite attribute
<q cite="http:// ...">...</q>

<blockquote cite="http://...">
<cite>...</cite>
</blockquote>

```
### Background

```
  background-color: keyword/hex_value/rgb/rgba/hsl/hsla;

  You can add a fallback background color as:
  background-color: blue;
  background-color: rgba(0,0,0,.3);

  Adding a background image:
  background-image: url("relative/absolute path of image");

  background-repeat: repeat/repeat-x/repeat-y/no-repeat
  Default value is repeat.

  background-position: horizontal_offset vertical_offset;
  Only one value specified then it is used for both horizontal and vertical offsets.
  background-position: 20px 20px;
  background-position: left top/right top/left bottom/right bottom
  background-position: 0 0/ 100% 0/0 100%/100% 100%

  Shorthand background property:
  background: color image position repeat;
  background: #b2b2b2 url("alert.png") 20px 10px no-repeat;

```
### Cursor
```
cursor:pointer;
min-width : 960px;
```

### Designing Gradient Backgrounds<br>
### Linear Gradient and Radial Gradient background

```
-webkit-linear-gradient(beginning color value, ending color value)
background: -webkit-linear-gradient(color1,color2...colorN);
background: -webkit-linear-gradient(#648880,#293f40);

Radial gradient : transition from center to outside
-webkit-radial-gradient(center color, outside color)
background: -webkit-radial-gradient(#648880,#293f40);

Include a fallback color as:
background: #466386;
background: -webkit-radial-gradient(#648880,#293f40);

Radial gradient full syntax:
radial-gradient( position, size and shape, color1, color2,...colorN);
-webkit-radial-gradient(50% 50%, circle, rgb(75,75,200), rgb(0,0,75));
Place the gradient center at 50% 50% position
-webkit-radial-gradient(50% 50%, 40px circle, rgb(75,75,200), rgb(0,0,75));
Make the gradient circular and give it a radius of 40px.

background: -webkit-linear-gradient(to right,#648880 85%,#293f40);

Using Multiple Background images:
background: url("fore.png") 0 0 no-repeat, url("three.png") 0 0 no-repeat;

background-size: width height;
width and height may contain keyword values like auto, cover and contain or percentages/px/em
background-size: auto/cover/contain 75%;
auto maintains the image's aspect ratio and height will be 75% of its parent.

cover keyword : completely covers the element's width and height.
Background image may be cut off.

contain keyword: image resides entirely within the element's width and height.
However image may not occupy the full available space of the element.

background-clip: padding-box/border-box/content-box;  Default: border-box
background-origin: padding-box/border-box/content-box; Default: padding-box
background-clip specifies the surface area  a background image will cover
background-origin specifies where the background image should originate.

```
### Creating Lists

```
<ul>                      <ol>
  <li>...</li>               <li>...</li>
  <li>...</li>               <li>...</li>
  <li>...</li>               <li>...</li>
</ul>                     </ol>

start attribute defines the start number
reversed is a boolean attribute that allows the list to appear in reversed order.

<ol start="30">      <ol reversed>        <ol>
  <li>...</li>           <li>...</li>       <li>...</li>
  <li>...</li>           <li>...</li>       <li value="9">...</li>
</ol>                </ol>                  <li>...</li>
                                          </ol>
value attribute is used to change its value within the list. Any list item
appearing below a list item with a value attribute will be recalculated accordingly.

```

### Description Lists

```
<dl> is description list
<dt> is description term
<dd> is description element

<dl>
  <dt>..</dt>
    <dd>...<dd>
    <dd>...<dd>
  <dt>..</dt>
    <dd>...<dd>
    <dd>...<dd>
</dl>

```

### Nesting Lists

```

<ol>
  <li>..</li>
  <li>..</li>
  <li>..
    <ul>
      <li>..</li>
      <li>..</li>
    </ul>
  </li>
  <li>..</li>
</ol>

CSS:  list-style-type: none/disc/square/circle

Using an image as a list item marker:
li {
  background: url("arrow.png") 0 50% no-repeat;
  list-style-type: none;
  padding-left: 12px;
}

```

### List style position property:

```
list-style-position: outside/inside; Default: outside
outside: does not allow content to wrap below the list item marker
inside: allows other content to wrap below it as needed.

Shorthand list property:
list-style: type position
list-style: circle inside;

Horizontally displaying list:

li {
  display: inline-block;
  margin: 0 10px;
}

Changing the display property to inline-block removes all the list item markers
like bullet, number or any other style.

If the list item marker is needed, then floating each li element is a better option.

li {
  float: left;
  margin: 0 20px;
}

Floating any element, breaks the flow of the page, so remember to clear our floats.

```

### ADDING MEDIA

```

<img src="dog.jpg" alt= "Hello">
images may be sized using the width and height properties in CSS
<img> is by default an inline level element.

img {
  display:block;
}

To float images to the left/right:

img { float:right; margin: .. ; padding: ..; }

```

### ADDING AUDIO

```
<audio src="jazz.ogg"></audio>
<audio src="jazz.ogg autoplay controls loop preload=none/auto/metadata"></audio>

Additional boolean attributes included are: autoplay, controls, loop.
autoplay - file will automatically play upon loading
controls - To display the default audio controls including play, pause, seek
and volume controls.
loop - cause an audio file to repeat continually from beginning to end.
preload attribute accepts three values none, auto and  metadata.
preload=none -> wont preload any information
preload=auto -> preload all information
preload=metadata -> preload any available metadata information.
Default is preload= auto

Audio Fallbacks and multiple resources:

<audio controls>
  <source src="jazz.ogg" type="audio/ogg">
  <source src="jazz.mp3" type="audio/mp3">
  <source src="jazz.wav" type="audio/wav">
  <a href="jazz.mp3" download> Download</a>
</audio>

download attribute is used to download the audio file.
```

### ADDING VIDEO

```
video element is same as audio element with the same attributes of src, autoplay,
controls, loop and preload

<video src="earth.ogv" controls></video>

poster attribute specifies the image to be displayed before the video is played.

<video src="earth.ogv" controls poster = "earth.jpg"></video>

Video fallbacks:

<video controls>
  <source src="earth.ogv" type="video/ogv">
  <source src="earth.mp4" type="video/mp4">
  <a href="earth.mp4" download> Download</a>
</video>

```

### ADDING INLINE FRAMES

```
To embed another HTML page within the current page, use the <iframe> element
<iframe> accepts the URL of another page within the src attribute value.
Value within the src attribute may be a relative URL or an absolute URL.

<iframe src="http://www.google.com/maps/embed?..."></iframe>

seamless boolean attribute allows the styles from the page that includes the iframe
element to be inherited by the page referenced within the <iframe> element. Further
links within an <iframe> element will be opened within the same window.

<iframe src="http://www.google.com/maps/embed?..." seamless></iframe>

```

### FIGURE

```
The <figure> block level element is used to identify and wrap self contained content
often in the form of media. It may surround images, audio clips, videos, blocks of code,
diagrams, illustrations, or self contained media.

<figure>
    <img src="dog.jpg" alt="dog">
</figure>

To add a caption to the <figure> element, use the <figcaption>  element.
The <figcaption> may appear at the top of, bottom of, or anywhere within the
<figure> element.

<figure>
    <img src="dog.jpg" alt="dog">
    <figcaption>Hello dog!</figcaption>
</figure>

```

### BUILDING FORMS

```
<form action="/login" method="post">
</form>

action attribute will include the URL wherein the contents included within the form
will be sent to for processing by the server.
method is the HTTP method browsers should use to submit the form data.

```

### Text fields & Text areas

```
<input type="text" name="username">
<input type="date" name="birthday">
<input type="email" name="email-address">
<input type="time" name="game-time">
<input type="url" name="website">
<input type="number" name="cost">
<input type="tel" name="phone-number">

<textarea name="comment">Add a comment</textarea>
Add a comment will appear inside the text box as the default text.
The textarea sizing is identified using the width and height property of CSS.

```
### Radio Buttons

```
<input type="radio" name="day" value="Friday" checked>Friday
<input type="radio" name="day" value="Saturday" checked>Saturday
<input type="radio" name="day" value="Sunday" checked>Sunday
<input type="radio" name="day" value="Monday" checked>Monday

```
### Check Boxes

```
<input type="checkbox" name="day" value="Monday" checked>Monday
<input type="checkbox" name="day" value="Tuesday" checked>Tuesday
<input type="checkbox" name="day" value="Wednesday" checked>Wednesday

```
### Drop Down Lists

```
<select name="day">
  <option value="Friday">Friday</option>
  <option value="Saturday">Saturday</option>
  <option value="Sunday">Sunday</option>
</select>

```
### Multiple Selections

```
Boolean attribute value : multiple allows user to select multiple values
from the drop down list. Using the selected boolean attribute on more
than one <option> element will preselect multiple options.

<select name="day" multiple>
  <option value="Friday" selected>Friday</option>
  <option value="Saturday">Saturday</option>
  <option value="Sunday">Sunday</option>
</select>

To choose multiple options, users need to hold down the shift key while
clicking to make their selections.

```
### Form Buttons

```
Submit input:

<input type="submit" name="submit" value="Send">
value attribute is used to specify the text that appears within the button.

Submit Button:

<button name="submit"><strong>Send</strong></button>

```
### Hidden Input

```
Hidden inputs provide a way to pass data to the server without displaying it
to the users. It contains info that is not pertinent to the users. The info
can be accessed by viewing the source code of the page.

<input type="hidden" name="tracking-code" value="abc-123">

```
### File input

```
To add a file to the form, use the file value to the type attribute of input.
<input type="file" name="file">

```

### Organizing Form elements

```
By using labels, fieldsets and legends, we can better organize our forms.

labels provide captions/heading for form controls.
THe for attribute of labels should be same as the id attribute of input
<label for="username">Username</label>
<input type="text" name="username" id="username">

labels can also wrap form controls, such as radio buttons and checkboxes.
<label>
  <input type="radio" name="day" value="Friday" checked>Friday
</label>

<label>
  <input type="radio" name="day" value="Saturday" checked>Saturday
</label>

<label>
  <input type="radio" name="day" value="Sunday" checked>Sunday
</label>

```
### Fieldset

```
Fieldsets group form controls and labels into organized sections.
Fieldset is a block level element that wraps related elements.
Fieldset by default also include a border outline.

<fieldset>
  <label>
  Username
    <input type="text" name="username">
  </label>

  <label>
  Password
    <input type="password" name="password">
  </label>
</fieldset>

```
### Legend

```
Legend provides a caption to the <fieldset> element.
The legend will appear within the top left part of the fieldset border.

<fieldset>
  <legend>Login</legend>
  <label>
  Username
    <input type="text" name="username">
  </label>

  <label>
  Password
    <input type="password" name="password">
  </label>
</fieldset>

```
### Disabled boolean attribute

```
disabled boolean attribute turns off an element or control, so that it is not
sent for interaction. Hidden boolean attribute is ignored.

<label>
  Username
    <input type="text" name="text" disabled>
</label>

```
### Placeholder attribute

```
placeholder attribute is used to provide a hint or tip within the form control
and disappears when the control is clicked or gain focus.

<label>
  Email address
    <input type="email" name="email-address" placeholder="name@domain.com">
</label>

<label>
  Email address
    <input type="email" name="email-address" value="name@domain.com">
</label>

The difference between value and the placeholder attribute is that the value
attribute value text stays in play when the control gains focus unless the user
manually deletes it.

```
### Required attribute

```
required boolean attribute enforces that an element or form control must contain a
value upon being submitted to the server.

<label>
  Email address
    <input type="email" name="email-address" required>
</label>

Other attributes : maxlength, min, max, autocomplete, autofocus
```

### ORGANIZING DATA WITH TABLES

```
  scope attribute is used to identify what content a table header relates to.
  col attribute value indicates that every cell wthin the column directly relates to the table header.
  row attribute value indicates that every cell wthin the row directly relates to the table header.
  <caption> element provides a caption or title for the table. It is positioned at the top of the table
  by default.

  thead(table head), tbody(table body) and tfoot(table foot)
  thead wraps the heading row
  tbody wraps the primary data of the table
  tfoot wraps the data that contains the outline of the table like: Subtotal, Tax or Total

  colspan attribute is used to combine two or more columns into one.
  rowspan attribute is used to combine two or more rows into one.
  Both work on either td or th elements.

  <table>
    <caption>Title of table</caption>
    <thead>
      <tr>
        <th scope="row/col/rowgroup/colgroup" colspan="2">...</th>
        <th scope="row/col/rowgroup/colgroup">...</th>
        <th scope="row/col/rowgroup/colgroup">...</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>...</td>
        <td>...</td>
        <td colspan="3">...</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td>...</td>
        <td>...</td>
        <td>...</td>
        <td></td>  -> empty column
      </tr>
    </tfoot>
</table>

```

### Table Borders

```
The border collapse property condenses the border into one, choosing the table cell as the primary border.
The border separate property allows borders to be stacked up against one another.
border-collapse: collapse/separate/inherit       Default is separate

When the border collapse property is set to separate, the border spacing property determines how much space
appears between the borders. Border spacing of 4 pixels separates the borders by 4 pixels.

border-collapse: separate;
border-spacing: 4px;

Border spacing property may accept two length values: horizontal spacing and vertical spacing
border-spacing: 4px 10px;
will place 5 pixels of horizontal spacing between borders and 10px of vertical spacing between borders.

```

### Adding borders to rows

```
table { border-collapse: collapse; }
th,td { border-bottom: 1px solid black; padding: 10px 15px; }
tfoot tr:last-child td { border-bottom : 0; }

```

### Table stripping

```
"stripe" table rows with alternating background colors.

table { border-collapse: separate; border-spacing:0; }
tbody tr:nth-child(even) { background: grey; }

```
### Vertical allign property

```
vertical-align works on inline and table cell elements.
vertical-align: top/middle/bottom
These values vertically position the text in relation to the table cell or to the closest
parent element for inline elements.

```
### Writing your Best Code

```
Use lowercase letters within element names, attributes and values
Indent nested elements
Strictly use double quotes
Remove the forward slash at the end of the self closing elements
Omit the values on the boolean attributes
Separate content from style by using external stylesheets.
Add comments to the CSS code indicating each section.
Write CSS using multiple lines and spaces.
Use shorter and primary direct selectors. Nest them only two or three levels deep.
Use specific classes whenever necessary.
Use shorthand properties and values whenever required.
Drop units from zero values
When using vendor prefixes, make sure to place the unprefixed property and value last
after all prefixed versions.
```

# 前端

Web Frontend Core Concerpt:

HTML (the Hypertext Markup Language) and CSS (Cascading Style Sheets) are two of the core technologies for building Web pages. HTML provides the structure of the page, CSS the (visual and aural) layout, for a variety of devices. Along with graphics and scripting, HTML and CSS are the basis of building Web pages and Web Applications.

## HTML

HTML is the standard markup language for Web pages.

标记语言（英语：markup language），也称置标语言、标记语言、标志语言、标识语言，是一种将文本（Text）以及文本相关的其他信息结合起来，展现出关于文档结构和数据处理细节的计算机文字编码。与文本相关的其他信息（包括例如文本的结构和表示信息等）与原来的文本结合在一起，但是使用标记（markup）进行标志。当今广泛使用的标记语言是超文本置标语言（HyperText Markup Language，HTML）和可扩展置标语言（eXtensible Markup Language，XML）。标记语言广泛应用于网页和网络应用程序。标记最早用于出版业，是作者、编辑以及出版商之间用于描述出版作品的排版格式所使用的。

### Elements

元素由开始标签，内容和结束标签组成。（An HTML element is defined by a start tag, some content, and an end tag.）

    <tagname>content</tagname>
    <h1>title</h1>

### Attributes

HTML属性提供关于元素的更多信息。（HTML attributes provide additional information about HTML elements.）

    <img src="" width="500px" height="500px" alt="tips">

#### onclick

The onclick attribute is part of the Event Attributes, and can be used on any HTML elements.

    <button onclick="myFunction()">Click me</button>

### Styles

The HTML style attribute is used to add styles to an element, such as color, font, size, and more.

    <body style="background-color:powderblue;"></body>

### Block && Inline Elements

#### Block

A block-level element always starts on a new line, and the browsers automatically add some space (a margin) before and after the element.

A block-level element always takes up the full width available (stretches out to the left and right as far as it can).

Two commonly used block elements are:

    <p>Hello World</p>
    <div>Hello World</div>

#### Inline

An inline element does not start on a new line.
An inline element only takes up as much width as necessary.

    <span>Hello World</span>

### Form

An HTML form is used to collect user input. The user input is most often sent to a server for processing.

The form element is a container for different types of input elements, such as: text fields, checkboxes, radio buttons, submit buttons, etc.

    <input>
    <label>
    <select>
    <textarea>
    <button>
    <fieldset>
    <legend>
    <datalist>
    <output>
    <option>
    <optgroup>

### Canvas

The HTML canvas element is used to draw graphics, on the fly, via JavaScript.

    <canvas id="myCanvas" width="200" height="100"></canvas>

### SVG

SVG defines vector-based graphics in XML format.
SVG stands for Scalable Vector Graphics
SVG is used to define graphics for the Web
SVG is a W3C recommendation

    <svg width="100" height="100">
        <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
    </svg>

### Video

The HTML video element is used to show a video on a web page.

    <video width="320" height="240" controls>
        <source src="movie.mp4" type="video/mp4">
        <source src="movie.ogg" type="video/ogg">
    Your browser does not support the video tag.
    </video>

### Audio

The HTML audio element is used to play an audio file on a web page.

    <audio controls>
        <source src="horse.ogg" type="audio/ogg">
        <source src="horse.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
    </audio>

### HTML APIS

#### Web Storage

HTML web storage provides two objects for storing data on the client:

    window.localStorage - stores data with no expiration date
    window.sessionStorage - stores data for one session (data is lost when the browser tab is closed)

Events

HTML has the ability to let events trigger actions in a browser, like starting a JavaScript when a user clicks on an element.

##### Window Event Attributes

Events triggered for the window object (applies to the body tag)

##### Form Events

Events triggered by actions inside a HTML form (applies to almost all HTML elements, but is most used in form elements):

##### Keyboard Events

##### Mouse Events

##### Drag Events

##### Clipboard Events

##### Media Events

## CSS

CSS is the language we use to style an HTML document.
CSS describes how HTML elements should be displayed.

### Box Model

All HTML elements can be considered as boxes.

    Content - The content of the box, where text and images appear
    Padding - Clears an area around the content. The padding is transparent
    Border - A border that goes around the padding and content
    Margin - Clears an area outside the border. The margin is transparent

Important: When you set the width and height properties of an element with CSS, you just set the width and height of the content area. To calculate the full size of an element, you must also add padding, borders and margins.

### Display

The display property specifies if/how an element is displayed.

### Position

1. static（默认)
2. relative（相对于原有位置）
3. absolute（相对于最近设置的position，没有则是body）
4. fixed（相对于viewport，就是相对于屏幕）
5. sticky（部分浏览器不支持，认为是fixed和relative的结合）

### Overflow

The CSS overflow property controls what happens to content that is too big to fit into an area.

The overflow property specifies whether to clip the content or to add scrollbars when the content of an element is too big to fit in the specified area.

The overflow property has the following values:

    visible - Default. The overflow is not clipped. The content renders outside the element's box
    hidden - The overflow is clipped, and the rest of the content will be invisible
    scroll - The overflow is clipped, and a scrollbar is added to see the rest of the content
    auto - Similar to scroll, but it adds scrollbars only when necessary

### CSS Float

#### Float

The CSS float property specifies how an element should float.

The CSS clear property specifies what elements can float beside the cleared element and on which side.

The float property is used for positioning and formatting content e.g. let an image float left to the text in a container.

The float property can have one of the following values:

    left - The element floats to the left of its container
    right - The element floats to the right of its container
    none - The element does not float (will be displayed just where it occurs in the text). This is default
    inherit - The element inherits the float value of its parent

In its simplest use, the float property can be used to wrap text around images.

#### Float Clear

When we use the float property, and we want the next element below (not on right or left), we will have to use the clear property.

The clear property specifies what should happen with the element that is next to a floating element.

The clear property can have one of the following values:

    none - The element is not pushed below left or right floated elements. This is default
    left - The element is pushed below left floated elements
    right - The element is pushed below right floated elements
    both - The element is pushed below both left and right floated elements
    inherit - The element inherits the clear value from its parent

When clearing floats, you should match the clear to the float: If an element is floated to the left, then you should clear to the left. Your floated element will continue to float, but the cleared element will appear below it on the web page.

### Inline-block

Compared to display: inline, the major difference is that display: inline-block allows to set a width and height on the element.

Also, with display: inline-block, the top and bottom margins/paddings are respected, but with display: inline they are not.

Compared to display: block, the major difference is that display: inline-block does not add a line-break after the element, so the element can sit next to other elements.

### Align

To horizontally center a block element (like div), use margin: auto;

To just center the text inside an element, use text-align: center;

### Pseudo-class

A pseudo-class is used to define a special state of an element.

For example, it can be used to:

    Style an element when a user mouses over it
    Style visited and unvisited links differently
    Style an element when it gets focus

The syntax of pseudo-classes:

    selector:pseudo-class {
        property: value;
    }

    /* unvisited link */
    a:link {
        color: #FF0000;
    }

    /* visited link */
    a:visited {
        color: #00FF00;
    }

    /* mouse over link */
    a:hover {
        color: #FF00FF;
    }

    /* selected link */
    a:active {
        color: #0000FF;
    }

An example of using the :hover pseudo-class on a div element:

    div:hover {
        background-color: blue;
    }

### Pseduo-element

A CSS pseudo-element is used to style specified parts of an element.

For example, it can be used to:

Style the first letter, or line, of an element
Insert content before, or after, the content of an element

The syntax of pseudo-elements:

    selector::pseudo-element {
        property: value;
    }

    p::first-line {
        color: #ff0000;
        font-variant: small-caps;
    }

    Notice the double colon notation - ::first-line versus :first-line

    The double colon replaced the single-colon notation for pseudo-elements in CSS3. This was an attempt from W3C to distinguish between pseudo-classes and pseudo-elements.

    The single-colon syntax was used for both pseudo-classes and pseudo-elements in CSS2 and CSS1.

    For backward compatibility, the single-colon syntax is acceptable for CSS2 and CSS1 pseudo-elements.

::after p::after Insert something after the content of each p element
::before p::before Insert something before the content of each p element

## JavaScript

### Event

HTML events are "things" that happen to HTML elements.

When JavaScript is used in HTML pages, JavaScript can "react" on these events.

    <element event='some JavaScript'>
    <button onclick="document.getElementById('demo').innerHTML = Date()">The time is?</button>

### HTML DOM

With the HTML DOM, JavaScript can access and change all the elements of an HTML document.

In other words: The HTML DOM is a standard for how to get, change, add, or delete HTML elements.

### HTML Browser BOM

The Browser Object Model (BOM) allows JavaScript to "talk to" the browser.

#### Window

The window object is supported by all browsers. It represents the browser's window.

#### Screen

The window.screen object contains information about the user's screen.

#### Location

The window.location object can be used to get the current page address (URL) and to redirect the browser to a new page.

#### History

The window.history object contains the browsers history.

#### Navigator

The window.navigator object contains information about the visitor's browser.

#### Popup Boxes

JavaScript has three kind of popup boxes: Alert box, Confirm box, and Prompt box.

#### Timing Events

The window object allows execution of code at specified time intervals.

These time intervals are called timing events.

The two key methods to use with JavaScript are:

    setTimeout(function, milliseconds)
    Executes a function, after waiting a specified number of milliseconds.

    setInterval(function, milliseconds)
    Same as setTimeout(), but repeats the execution of the function continuously.

#### Cookies

Cookies let you store user information in web pages.

    document.cookie = "username=John Doe; expires=Thu, 18 Dec 2013 12:00:00 UTC";

## 常见问题

* React和VUE的选择？

  * 我简单看了VUE，感觉VUE是相对来说比较简单易用，但是最后还是选择使用React，考虑主要是大厂商的支持还是相对更稳定些，社区更丰富，另外我这些年看身边主流的做的好的基本还是React的，VUE基本还是新手选择或者小项目选择，从招聘看React人更难找些，VUE好多，可能和学习曲线等有些关系。

* 浏览器页面左上方的图标哪里来的？
  * favicon.ico，网站根目录下存放的图标显示出来的。
    * [HTML Favicon](https://www.w3schools.com/html/html_favicon.asp)
    * [免费favicon生成网站](https://favicon.io/favicon-generator)

## 参考文献

1. [HTML & CSS Standards](https://www.w3.org/standards/webdesign/htmlcss)
2. [Cascading Style Sheets](https://www.w3.org/Style/CSS/)
3. [HTML Tutorial](https://www.w3schools.com/html/default.asp)
4. [CSS Layout - The position Property](https://www.w3schools.com/css/default.asp)
5. [JavaScript Tutorial](https://www.w3schools.com/js/default.asp)
6. [mdn](https://developer.mozilla.org/en-US/)
7. [React哲学](https://zh-hans.reactjs.org/docs/thinking-in-react.html)
8. [replit](https://replit.com)

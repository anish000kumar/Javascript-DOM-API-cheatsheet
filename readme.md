# Accessing Dom Elements

### Nodes

![DOM Element Traversal](https://i.ibb.co/H4Bx8KJ/dom.png)


```javascript
// Returns a reference to the element by its ID.
document.getElementById("someid");

// Returns an array-like object of all child elements which have all of the given class names.
document.getElementsByClassName("someclass");

// Returns an HTMLCollection of elements with the given tag name.
document.getElementsByTagName("LI");

// Returns the first element within the document that matches the specified group of selectors.
document.querySelector(".someclass");

// Returns a list of the elements within the document (using depth-first pre-order traversal of the document's nodes)
// that match the specified group of selectors.
document.querySelectorAll("div.note, div.alert");
```

#### Grab Children/Parent Node(s)

```javascript
// Get child nodes
var stored = document.getElementById("someid");
var children = stored.childNodes;

// Get parent node
var parental = children.parentNode;
```

#### Create New DOM Elements

```javascript
// create new elments
var newHeading = document.createElement("h1");
var newParagraph = document.createElement("p");

// create text nodes for new elements
var h1Text = document.createTextNode("This is a nice header text!");
var pText = document.createTextNode("This is a nice paragraph text!");

// attach new text nodes to new elements
newHeading.appendChild(h1Text);
newParagraph.appendChild(pText);

// elements are now created and ready to be added to the DOM.
```

#### Add Elements to the DOM

```javascript
// grab element on page you want to add stuff to
var firstHeading = document.getElementById("firstHeading");

// add both new elements to the page as children to the element we stored in firstHeading.
firstHeading.appendChild(newHeading);
firstHeading.appendChild(newParagraph);

// can also insert before like so

// get parent node of firstHeading
var parent = firstHeading.parentNode;

// insert newHeading before FirstHeading
parent.insertBefore(newHeading, firstHeading);
```

#### Add Elements to the DOM cont.

Suppose you have the following HTML:

```html
<div id="box1"><p>Some example text</p></div>
<div id="box2"><p>Some example text</p></div>
```

You can insert another snippet of HTML between #box1 and #box2:

```javascript
var box2 = document.getElementById("box2");
box2.insertAdjacentHTML("beforebegin", "<div><p>This gets inserted.</p></div>");

// beforebegin - The HTML would be placed immediately before the element, as a sibling.
// afterbegin - The HTML would be placed inside the element, before its first child.
// beforeend - The HTML would be placed inside the element, after its last child.
// afterend - The HTML would be placed immediately after the element, as a sibling.
```

#### Add/Remove/Toggle/Check Classes

```javascript
// grab element on page you want to use
var firstHeading = document.getElementById("firstHeading");

// will remove foo if it is a class of firstHeading
firstHeading.classList.remove("foo");

// will add the class 'anotherClass' if one does not already exist
firstHeading.classList.add("anotherclass");

// add or remove multiple classes
firstHeading.classList.add("foo", "bar");
firstHeading.classList.remove("foo", "bar");

// if visible class is set remove it, otherwise add it
firstHeading.classList.toggle("visible");

// will return true if it has class of 'foo' or false if it does not
firstHeading.classList.contains("foo");
```

### Using template literals

```html
<body></body>
```

```javascript
function render(props) {
  return `
            <div class="container"> 
                <h1> ${props.name} </h1>
            </div>
        `;
}

document.body.innerHTML = render("John");
```

### Other node methods

```javascript
// Creates newNode as a copy (clone) of node. If bool is true, the clone includes clones of all the child nodes of the original.

newNode = node.cloneNode(bool);

// Removes the child oldNode from node.
node.removeChild(oldNode):

// Replaces the child node oldNode of node with newNode.
node.replaceChild(newNode, oldNode)

// Retrieves the value of the attribute with the name attribute
node.getAttribute('attribute')

// Sets the value of the attribute with the name attribute to value
node.setAttribute('attribute', 'value')

// Reads the type of the node (1 = element, 3 = text node)
node.nodeType

// Reads the name of the node (either element name or #textNode)
node.nodeName

// Reads or sets the value of the node (the text content in the case of text nodes)
node.nodeValue
```

### Events

- INLINE EVENT HANDLERS

```html
<a href="site.com" onclick="dosomething();">A link</a>
```

- DOM ON-EVENT HANDLERS

```javascript
window.onload = () => {
  //window loaded
};

const xhr = new XMLHttpRequest();
xhr.onreadystatechange = () => {
  //.. do something
};
```

- USING ADDEVENTLISTENER()

```javascript
window.addEventListener("load", onLoad);
window.removeEventListener("load", onLoad);
```

#### Custom events

```javascript
//A CustomEventInit dictionary, having the following fields: "detail", optional and defaulting to null, of type any, that is an event-dependent value associated with the event.
event = new CustomEvent(typeArg, customEventInit);
```

- Dispatching

```javascript
var event = new Event("build");
// Listen for the event.
elem.addEventListener(
  "build",
  function(e) {
    /* ... */
  },
  false
);
// Dispatch the event.
elem.dispatchEvent(event);
```

#### Date and time

```javascript
//Sun Nov 18 2018 23:18:58 GMT+0530 (India Standard Time)
var d = new Date();
//1542563338408 miliseconds passed since 1970
Number(d);
Date("2017-06-23"); // date declaration
Date("2017"); // is set to Jan 01
Date("2017-06-23T12:00:00-09:45"); // date - time YYYY-MM-DDTHH:MM:SSZ
Date("June 23 2017"); // long date format
Date("Jun 23 2017 07:45:00 GMT+0100 (Tokyo Time)"); // time zone

var d = new Date();
a = d.getDay(); // getting the weekday

getDate(); // day as a number (1-31)
getDay(); // weekday as a number (0-6)
getFullYear(); // four digit year (yyyy)
getHours(); // hour (0-23)
getMilliseconds(); // milliseconds (0-999)
getMinutes(); // minutes (0-59)
getMonth(); // month (0-11)
getSeconds(); // seconds (0-59)
getTime(); // milliseconds since 1970

var d = new Date();
d.setDate(d.getDate() + 7); // adds a week to a date

setDate(); // day as a number (1-31)
setFullYear(); // year (optionally month and day)
setHours(); // hour (0-23)
setMilliseconds(); // milliseconds (0-999)
setMinutes(); // minutes (0-59)
setMonth(); // month (0-11)
setSeconds(); // seconds (0-59)
setTime(); // milliseconds since 1970)
```

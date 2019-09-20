# Discussion Questions: Events

## Objectives

* Recall the different types of JavaScript Events
* Identify when the `DOMContentLoaded` event will trigger
* Implement a callback attached to an event handler

## Exercise

Take a look at each of the code samples below. For each sample, work with your group to answer the following questions.

1. What does each line of code do?
2. How does this piece of code work?
3. Given this code sample, what can you learn or describe about JavaScript

### Example 1

```html
// index.html
...

<button id="notify">Click Me!</button>

<script src="index.js" />
```
The first line of code creates a `button` element with an `id` of "notify" and content of "Click Me!" The second line creates a `script` element which references executable code in a local file, `index.js`.
```js
// index.js

const button = document.getElementById("notify")
button.addEventListener('click', function(){
  console.log("Printing a Message!")
})
```
The first line of code in this case declares a constant `button` to an element of the `document` object. The element with the `id` of "notify" object is nabbed by the `.getElementById` method (aka the `button` element created in the previous code block). The second line of code calls the `.addEventListener` on the `button` element object. An event listener sets up a function which will be called any time the specified event is delivered to the element. In this case, the `click` event on the `button` element resulves in a function being called which logs "Printing a Message!" to a console. 
### Example 2

```html
// index.html
...

<button id="notify">Click Me!</button>

<script src="index.js" />
```

```js
// index.js

const button = document.getElementById("notify")
button.addEventListener('mouseover', function(){
  console.log("Printing a Message!")
})
```
Ditto with regards to Example 1, except the event listener function is triggered when a `mouseover` event is delivered to the `button` element.
### Example 3

```html
// index.html
...
<script src="index.js" />

<button id="notify">Click Me!</button>

```

```js
// index.js

const button = document.getElementById("notify")
button.addEventListener('mouseover', function(){
  console.log("Printing a Message!")
})
```
Ditta with regards to Example 2, except the JavaScript is referenced before the button is created. This arrangement changes the load order of the page, and will result in an error because `button` does not exist when the JavaScript is requested and executed.

[A reminder from StackOverflow's Masih IT](https://stackoverflow.com/questions/436411/where-should-i-put-script-tags-in-html-markup):
> Here's what happens when a browser loads a website with a `<script>` tag on it:
> 1. Fetch the HTML page (e.g. index.html)
> 2. Begin parsing the HTML
> 3. The parser encounters a `<script>` tag referencing an external script file.
> 4. The browser requests the script file. Meanwhile, the parser blocks and stops parsing the other HTML on your page.
> 5. After some time the script is downloaded and subsequently executed.
> 6. The parser continues parsing the rest of the HTML document.

### Example 4

```html
// index.html
...
<script src="index.js" />

<button id="notify">Click Me!</button>

```

```js
// index.js
document.addEventListener("DOMContentLoaded", function(){
  const button = document.getElementById("notify")
  button.addEventListener('mouseover', function(){
    console.log("Printing a Message!")
  })
});
```
Ditto in reference to Example 4, but here we ensure that the event listener is not assigned to `button` until the DOM is loaded (i.e. the HTML file is completely parsed). This safety is achieved by assigning an event listener to the entire document, whose function (our JavaScript from Example 3) isn't fired until the event `DOMContentLoaded`.
### Example 5

Oops. Looks like this developer made some mistakes typing. Identify the mistakes.

```html
// index.html
...
<script src="index.js" />

<button id="notifiable">Click Me!</button>

```

```js
// index.js
document.addListenerEvent("DOMContentLoaded", function(){
  const button = document.getElementById("notifliable")
  button.addListenerEvent('click', function(){
    console.log("Printing a Message!")
  })
});
```
Galdurned typos. `notifliable` should be `notifiable`, and the method is `addEventListener`, not `addListenerEvent`.
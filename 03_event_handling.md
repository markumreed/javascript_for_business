# Tutorial: Event Handling in JavaScript

In this tutorial, we will explore event handling in JavaScript with examples that separate the HTML structure and JavaScript logic into their own respective files.

## 1. What are Events in JavaScript?

**Events** are actions or occurrences that happen in the browser, such as clicks, key presses, form submissions, or page loads. JavaScript can listen for these events and respond to them by executing a function, also known as an **event handler**.

### HTML (index.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Handling Example</title>
</head>
<body>
    <button id="myButton">Click Me</button>
    <script src="main.js"></script>
</body>
</html>
```

### JavaScript (main.js):

```javascript
document.getElementById('myButton').addEventListener('click', function() {
    alert('Button clicked!');
});
```

### Explanation:

- The **HTML file** defines the structure of the page, including a button with the ID `myButton`.
- The **JavaScript file** listens for a `click` event on the button. When the button is clicked, an alert is displayed.

---

## 2. The `addEventListener()` Method

The `addEventListener()` method is used to attach event handlers to DOM elements. It takes two arguments: the event type (e.g., `'click'`) and the function that should be executed when the event occurs.

### HTML (button.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Add Event Listener Example</title>
</head>
<body>
    <button id="subscribeButton">Subscribe</button>
    <script src="button.js"></script>
</body>
</html>
```

### JavaScript (button.js):

```javascript
const subscribeButton = document.getElementById('subscribeButton');

subscribeButton.addEventListener('click', function() {
    console.log('Subscribed successfully!');
});
```

### Explanation:

- The HTML structure includes a button labeled "Subscribe".
- In the JavaScript file, we use `addEventListener()` to listen for a `click` event on the button and log a message to the console when the button is clicked.

---

## 3. Commonly Used Event Types

Here are some common event types:
- **`click`**: Triggered when an element is clicked.
- **`submit`**: Triggered when a form is submitted.
- **`keydown`**: Triggered when a key is pressed down.

### HTML (input.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Keydown Event Example</title>
</head>
<body>
    <input type="text" id="nameInput" placeholder="Type your name">
    <script src="input.js"></script>
</body>
</html>
```

### JavaScript (input.js):

```javascript
document.getElementById('nameInput').addEventListener('keydown', function(event) {
    console.log(`Key pressed: ${event.key}`);
});
```

### Explanation:

- The **input field** listens for `keydown` events and logs the key that was pressed.

---

## 4. Removing Event Listeners

You can remove event listeners using the `removeEventListener()` method. The function passed to `addEventListener()` must be the same function reference when removing the event listener.

### HTML (remove-listener.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Remove Event Listener Example</title>
</head>
<body>
    <button id="stopButton">Stop Event</button>
    <script src="remove-listener.js"></script>
</body>
</html>
```

### JavaScript (remove-listener.js):

```javascript
function eventHandler() {
    console.log('Button clicked!');
}

const stopButton = document.getElementById('stopButton');

stopButton.addEventListener('click', eventHandler);

// Remove the event listener after 5 seconds
setTimeout(() => {
    stopButton.removeEventListener('click', eventHandler);
    console.log('Event listener removed');
}, 5000);
```

### Explanation:

- This example removes the `click` event listener after 5 seconds using `removeEventListener()`.

---

## 5. Event Objects

The **event object** contains useful information about the event, such as the type of event, the target element, and the position of the cursor.

### HTML (event-object.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Object Example</title>
</head>
<body>
    <button id="infoButton">Get Info</button>
    <script src="event-object.js"></script>
</body>
</html>
```

### JavaScript (event-object.js):

```javascript
document.getElementById('infoButton').addEventListener('click', function(event) {
    console.log(`Event type: ${event.type}`);
    console.log(`Target element: ${event.target}`);
});
```

### Explanation:

- This example logs details from the **event object** when the button is clicked.

---

## 6. Event Propagation: Bubbling and Capturing

Event propagation refers to the way events travel through the DOM. Events can be captured from the top down (capturing phase) or bubble from the bottom up (bubbling phase). By default, events bubble.

### HTML (bubbling.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Bubbling Example</title>
</head>
<body>
    <div id="parentDiv">
        <button id="childButton">Click Me</button>
    </div>
    <script src="bubbling.js"></script>
</body>
</html>
```

### JavaScript (bubbling.js):

```javascript
const parentDiv = document.getElementById('parentDiv');
const childButton = document.getElementById('childButton');

parentDiv.addEventListener('click', () => {
    console.log('Parent DIV clicked');
});

childButton.addEventListener('click', (event) => {
    console.log('Button clicked');
    event.stopPropagation();  // Prevents event from bubbling up to parentDiv
});
```

### Explanation:

- The event listener on the `childButton` stops the event from bubbling up to the parent element using `stopPropagation()`.

---

## 7. Event Delegation

**Event delegation** allows you to attach a single event listener to a parent element and manage events from its child elements.

### HTML (delegation.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Delegation Example</title>
</head>
<body>
    <ul id="itemList">
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
    <button id="addItem">Add Item</button>
    <script src="delegation.js"></script>
</body>
</html>
```

### JavaScript (delegation.js):

```javascript
const itemList = document.getElementById('itemList');
const addItemButton = document.getElementById('addItem');

// Event delegation: Handle clicks on list items
itemList.addEventListener('click', (event) => {
    if (event.target.tagName === 'LI') {
        alert(`You clicked ${event.target.textContent}`);
    }
});

// Add new list items dynamically
addItemButton.addEventListener('click', () => {
    const newItem = document.createElement('li');
    newItem.textContent = `Item ${itemList.children.length + 1}`;
    itemList.appendChild(newItem);
});
```

### Explanation:

- This example uses event delegation by attaching a single click event listener to the parent `ul` element. It handles clicks on any `<li>` item, even dynamically added ones.

---

## 8. Preventing Default Behavior

Some events have default behaviors, such as navigating to a new page when clicking a link or submitting a form. You can

 prevent these default behaviors with `event.preventDefault()`.

### HTML (prevent-default.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prevent Default Example</title>
</head>
<body>
    <form id="myForm">
        <input type="text" placeholder="Enter something" required>
        <button type="submit">Submit</button>
    </form>
    <script src="prevent-default.js"></script>
</body>
</html>
```

### JavaScript (prevent-default.js):

```javascript
document.getElementById('myForm').addEventListener('submit', function(event) {
    event.preventDefault();  // Prevents form submission and page reload
    alert('Form submission prevented!');
});
```

### Explanation:

- This example prevents the default form submission behavior, allowing you to handle the form data via JavaScript instead.

---

## 9. Business Example: E-commerce Product Selection

### Scenario:

In an e-commerce application, you want to update the price of a product based on user selection (e.g., size).

### HTML (ecommerce.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E-commerce Product Selection</title>
</head>
<body>
    <h2 id="product-name">T-Shirt</h2>
    <p id="product-price">$20</p>
    <select id="size-selector">
        <option value="20">Small - $20</option>
        <option value="25">Medium - $25</option>
        <option value="30">Large - $30</option>
    </select>
    <script src="ecommerce.js"></script>
</body>
</html>
```

### JavaScript (ecommerce.js):

```javascript
const priceElement = document.getElementById('product-price');
const sizeSelector = document.getElementById('size-selector');

sizeSelector.addEventListener('change', function(event) {
    const selectedPrice = event.target.value;
    priceElement.textContent = `$${selectedPrice}`;
});
```

### Explanation:

- When the user selects a different size, the price is updated dynamically based on the selected size.

---

## 10. Conclusion

By separating HTML and JavaScript into distinct files, you create a more organized and maintainable structure for your web projects. Event handling is essential for creating interactive and dynamic web applications. Here are the key concepts covered:

### Key Takeaways:
- **`addEventListener()`** attaches event listeners to elements for handling user actions.
- **Event Propagation** includes both bubbling and capturing phases, with `stopPropagation()` controlling event flow.
- **Event Delegation** allows for efficient event handling, particularly when dealing with dynamically added elements.
- **`preventDefault()`** stops the default actions for events like form submissions and link clicks.

By mastering event handling, you can build powerful and responsive applications that react to user input in real-time.

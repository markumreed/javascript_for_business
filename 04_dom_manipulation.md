# DOM Manipulation

#### Introduction

DOM (Document Object Model) manipulation is a fundamental skill in JavaScript, allowing you to interact with and modify the structure and content of web pages dynamically. This tutorial will cover basic DOM manipulation techniques using business-related examples. By mastering these concepts, you can create dynamic and interactive web applications.

#### Accessing DOM Elements

To manipulate the DOM, you first need to access the elements you want to interact with. You can do this using various methods provided by the `document` object.

##### 1. `getElementById`

The `getElementById` method returns the element that has the ID attribute with the specified value.

**Example**:
Suppose you need to access an element that displays the total sales amount.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Total Sales</title>
</head>
<body>
    <div id="totalSales">Total Sales: $1000</div>

    <script>
        let totalSalesElement = document.getElementById('totalSales');
        console.log(totalSalesElement.textContent); // Output: Total Sales: $1000
    </script>
</body>
</html>
```

**Explanation**:
In this example, the `getElementById` method is used to access the `div` element with the ID `totalSales`. The `textContent` property is then used to retrieve the text content of the element. This allows you to access and manipulate elements by their unique ID.

##### 2. `getElementsByClassName`

The `getElementsByClassName` method returns a live HTMLCollection of elements with the specified class name.

**Example**:
Suppose you need to access multiple elements that display the sales figures for different products.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Product Sales</title>
</head>
<body>
    <div class="sales">Laptop Sales: $5000</div>
    <div class="sales">Tablet Sales: $3000</div>
    <div class="sales">Smartphone Sales: $2000</div>

    <script>
        let salesElements = document.getElementsByClassName('sales');
        for (let i = 0; i < salesElements.length; i++) {
            console.log(salesElements[i].textContent);
        }
        // Output:
        // Laptop Sales: $5000
        // Tablet Sales: $3000
        // Smartphone Sales: $2000
    </script>
</body>
</html>
```

**Explanation**:
In this example, the `getElementsByClassName` method is used to access all `div` elements with the class `sales`. A `for` loop is then used to iterate over the collection of elements and print their text content. This allows you to work with multiple elements that share the same class.

##### 3. `querySelector` and `querySelectorAll`

The `querySelector` method returns the first element that matches a specified CSS selector, while `querySelectorAll` returns a static NodeList of all elements that match the selector.

**Example**:
Suppose you need to access a specific element and all elements of a particular type.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Sales Data</title>
</head>
<body>
    <div id="mainSales">Main Sales: $8000</div>
    <div class="sales">Laptop Sales: $5000</div>
    <div class="sales">Tablet Sales: $3000</div>

    <script>
        let mainSalesElement = document.querySelector('#mainSales');
        console.log(mainSalesElement.textContent); // Output: Main Sales: $8000

        let allSalesElements = document.querySelectorAll('.sales');
        allSalesElements.forEach((element) => {
            console.log(element.textContent);
        });
        // Output:
        // Laptop Sales: $5000
        // Tablet Sales: $3000
    </script>
</body>
</html>
```

**Explanation**:
In this example, `querySelector` is used to select the element with the ID `mainSales`, and `querySelectorAll` is used to select all elements with the class `sales`. The `forEach` method is then used to iterate over the NodeList and print the text content of each element. This approach provides a more flexible way to select elements using CSS selectors.

#### Manipulating DOM Elements

Once you have accessed the DOM elements, you can manipulate their content and attributes.

##### 1. Changing Content

You can change the text content of an element using the `textContent` or `innerHTML` properties.

**Example**:
Suppose you need to update the total sales amount displayed on the page.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Update Sales</title>
</head>
<body>
    <div id="totalSales">Total Sales: $1000</div>
    <button id="updateButton">Update Sales</button>

    <script>
        let totalSalesElement = document.getElementById('totalSales');
        let updateButton = document.getElementById('updateButton');

        updateButton.addEventListener('click', () => {
            totalSalesElement.textContent = 'Total Sales: $1500';
        });
    </script>
</body>
</html>
```

**Explanation**:
In this example, the `getElementById` method is used to access the `div` element with the ID `totalSales` and the `button` element with the ID `updateButton`. An event listener is added to the button to update the text content of the `totalSales` element when the button is clicked. This demonstrates how to dynamically update the content of elements in response to user actions.

##### 2. Modifying Attributes

You can change the attributes of an element using the `setAttribute` and `removeAttribute` methods.

**Example**:
Suppose you need to update the URL of a link based on user input.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Update Link</title>
</head>
<body>
    <a id="productLink" href="https://example.com">Product Page</a>
    <input type="text" id="urlInput" placeholder="Enter new URL">
    <button id="updateButton">Update Link</button>

    <script>
        let productLink = document.getElementById('productLink');
        let urlInput = document.getElementById('urlInput');
        let updateButton = document.getElementById('updateButton');

        updateButton.addEventListener('click', () => {
            let newUrl = urlInput.value;
            productLink.setAttribute('href', newUrl);
            productLink.textContent = 'Updated Product Page';
        });
    </script>
</body>
</html>
```

**Explanation**:
In this example, the `getElementById` method is used to access the `a` element with the ID `productLink`, the `input` element with the ID `urlInput`, and the `button` element with the ID `updateButton`. An event listener is added to the button to update the `href` attribute of the `productLink` element with the value entered in the input field and change the link text when the button is clicked. This shows how to modify the attributes of elements dynamically.

##### 3. Adding and Removing Elements

You can add and remove elements dynamically using methods like `appendChild`, `insertBefore`, and `removeChild`.

**Example**:
Suppose you need to add new product entries to a list and remove them based on user actions.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Manage Products</title>
</head>
<body>
    <ul id="productList">
        <li>Laptop</li>
        <li>Tablet</li>
    </ul>
    <input type="text" id="productInput" placeholder="Enter product name">
    <button id="addButton">Add Product</button>
    <button id="removeButton">Remove Last Product</button>

    <script>
        let productList = document.getElementById('productList');
        let productInput = document.getElementById('productInput');
        let addButton = document.getElementById('addButton');
        let removeButton = document.getElementById('removeButton');

        addButton.addEventListener('click', () => {
            let newProduct = productInput.value;
            let newProductElement = document.createElement('li');
            newProductElement.textContent = newProduct;
            productList.appendChild(newProductElement);
        });

        removeButton.addEventListener('click', () => {
            if (productList.lastElementChild) {
                productList.removeChild(productList.lastElementChild);
            }
        });
    </script>
</body>
</html>
```

**Explanation**:
In this example, the `getElementById` method is used to access the `ul` element with the ID `productList`, the `input` element with the ID `productInput`, and the buttons with the IDs `addButton` and `removeButton`. An event listener is added to the `addButton` to create a new `li` element with the product name entered in the input field and append it to the `productList`. Another event listener is added to the `removeButton` to remove the last `li` element from the `productList`. This demonstrates how to add and remove elements dynamically in response to user actions.

#### Conclusion

By understanding and using DOM manipulation techniques in JavaScript through these business-related examples, you can create dynamic and interactive web applications that respond to user interactions and modify the page content on the fly

. Practice these concepts to build a strong foundation in JavaScript DOM manipulation.

### Further Reading
- [MDN Web Docs: Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [MDN Web Docs: Document Object Model (DOM)](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)
- [JavaScript.info: DOM Navigation](https://javascript.info/dom-navigation)
- [Eloquent JavaScript: The Document Object Model](https://eloquentjavascript.net/14_dom.html)
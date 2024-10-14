# Tutorial: DOM Manipulation and Events in JavaScript (with Business Examples)

In modern web development, it is common practice to separate HTML and JavaScript into different files. This helps maintain a clean structure and allows for better scalability and maintainability of code. This tutorial will guide you through DOM manipulation and event handling using separate files for HTML and JavaScript, with business-related examples to illustrate key concepts.


## 1. What is DOM Manipulation?

### What is the DOM?

The **Document Object Model (DOM)** represents the structure of an HTML document as a tree of objects. Using JavaScript, you can interact with this tree, changing the content, structure, and style of the webpage dynamically. This is referred to as **DOM manipulation**.

### Why is DOM Manipulation Important in Business?

DOM manipulation allows businesses to create dynamic web applications that respond to user interactions in real-time. This is essential for e-commerce, customer engagement, and inventory management, where updates to the webpage (like showing current stock or updating prices) must be reflected immediately.

---

## 2. Selecting Elements

### How to Select Elements

To manipulate elements in the DOM, you first need to select them. This can be done using JavaScript methods like `getElementById`, `querySelector`, and `querySelectorAll`.

### HTML (product.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Page</title>
</head>
<body>
    <h1 id="product-title">Laptop</h1>
    <button id="change-product">Select Smartphone</button>

    <script src="product.js"></script>
</body>
</html>
```

### JavaScript (product.js):

```javascript
const productTitle = document.getElementById("product-title");
const changeProductButton = document.getElementById("change-product");

changeProductButton.addEventListener("click", () => {
    productTitle.textContent = "Smartphone";
});
```

### Explanation:

- The HTML file (`product.html`) includes the basic structure of the webpage with an `h1` element representing the product title and a button for changing the product.
- The JavaScript file (`product.js`) contains the logic to update the product title when the button is clicked.

---

## 3. Modifying Content and Attributes

### How to Change Content and Attributes

You can dynamically modify the content and attributes of elements in the DOM using properties like `textContent`, `innerHTML`, and methods like `setAttribute`.

### HTML (discount.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Discount Page</title>
</head>
<body>
    <p id="price">$1200</p>
    <button id="apply-discount">Apply 10% Discount</button>

    <script src="discount.js"></script>
</body>
</html>
```

### JavaScript (discount.js):

```javascript
const priceElement = document.getElementById("price");
const applyDiscountButton = document.getElementById("apply-discount");

const originalPrice = 1200;

applyDiscountButton.addEventListener("click", () => {
    const discount = 0.1;
    const discountedPrice = originalPrice * (1 - discount);
    priceElement.textContent = `$${discountedPrice}`;
});
```

### Explanation:

- The HTML file (`discount.html`) contains a price element and a button to apply a discount.
- The JavaScript file (`discount.js`) updates the displayed price when the button is clicked by applying a 10% discount.

---

## 4. Adding and Removing Elements

### How to Add or Remove Elements

You can dynamically add or remove elements from the DOM using methods like `createElement`, `appendChild`, and `removeChild`.

### HTML (product-list.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product List</title>
</head>
<body>
    <ul id="product-list">
        <li>Phone</li>
        <li>Tablet</li>
    </ul>
    <button id="add-product">Add Smartwatch</button>

    <script src="product-list.js"></script>
</body>
</html>
```

### JavaScript (product-list.js):

```javascript
const productList = document.getElementById("product-list");
const addProductButton = document.getElementById("add-product");

addProductButton.addEventListener("click", () => {
    const newProduct = document.createElement("li");
    newProduct.textContent = "Smartwatch";
    productList.appendChild(newProduct);
});
```

### Explanation:

- The HTML file (`product-list.html`) contains an unordered list (`ul`) of products and a button for adding a new product.
- The JavaScript file (`product-list.js`) listens for a click event on the "Add Smartwatch" button and appends a new list item (`li`) to the product list.

---

## 5. Handling Events

### What are Events?

**Events** are actions that occur on a webpage, such as clicks, form submissions, or key presses. JavaScript allows us to listen for these events using **event listeners** and respond to them.

### HTML (cart.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shopping Cart</title>
</head>
<body>
    <button id="add-to-cart">Add to Cart</button>
    <p id="cart-status">Cart is empty.</p>

    <script src="cart.js"></script>
</body>
</html>
```

### JavaScript (cart.js):

```javascript
const addToCartButton = document.getElementById("add-to-cart");
const cartStatus = document.getElementById("cart-status");

addToCartButton.addEventListener("click", () => {
    cartStatus.textContent = "Product added to cart!";
});
```

### Explanation:

- The HTML file (`cart.html`) contains a button for adding a product to the cart and a paragraph to display the cart status.
- The JavaScript file (`cart.js`) listens for a click event on the "Add to Cart" button and updates the cart status when the button is clicked.

---

## 6. Business Example 1: Product Display and Dynamic Pricing

### Scenario:

In an e-commerce application, you want to update the price displayed when the user selects different sizes of a product.

### HTML (product-pricing.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Pricing</title>
</head>
<body>
    <h2 id="product-name">T-Shirt</h2>
    <p id="product-price">$20</p>

    <select id="size-selector">
        <option value="20">Small - $20</option>
        <option value="25">Medium - $25</option>
        <option value="30">Large - $30</option>
    </select>

    <script src="product-pricing.js"></script>
</body>
</html>
```

### JavaScript (product-pricing.js):

```javascript
const priceElement = document.getElementById("product-price");
const sizeSelector = document.getElementById("size-selector");

sizeSelector.addEventListener("change", (event) => {
    const selectedPrice = event.target.value;
    priceElement.textContent = `$${selectedPrice}`;
});
```

### Explanation:

- The HTML file (`product-pricing.html`) contains a dropdown menu (`select`) for product sizes and a paragraph showing the price.
- The JavaScript file (`product-pricing.js`) updates the price based on the selected size.

---

## 7. Business Example 2: Customer Feedback Form

### Scenario:

You want to collect customer feedback on your site and display a thank-you message when the form is submitted.

### HTML (feedback-form.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Customer Feedback</title>
</head>
<body>
    <form id="feedback-form">
        <label for="feedback">Your Feedback:</label>
        <textarea id="feedback" name="feedback"></textarea>
        <button type="submit">Submit Feedback</button>
    </form>
    <p id="form-response"></p>

    <script src="feedback-form.js"></script>
</body>
</html>
```

### JavaScript (feedback-form.js):

```javascript
const form = document.getElementById("feedback-form");
const formResponse = document.getElementById("form-response");



form.addEventListener("submit", (event) => {
    event.preventDefault(); // Prevent page reload on form submission
    const feedback = document.getElementById("feedback").value;

    if (feedback.length > 0) {
        formResponse.textContent = "Thank you for your feedback!";
        form.reset(); // Clear the form after submission
    } else {
        formResponse.textContent = "Please provide feedback before submitting.";
    }
});
```

### Explanation:

- The HTML file (`feedback-form.html`) contains a simple feedback form with a `textarea` for customer input.
- The JavaScript file (`feedback-form.js`) handles form submission, prevents the default page reload, validates the input, and displays a message to the user.

---

## 8. Business Example 3: Inventory Management

### Scenario:

You want to display the current inventory count of a product and disable the "Add to Cart" button if the product is out of stock.

### HTML (inventory.html):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inventory Management</title>
</head>
<body>
    <h3>Product: Smartwatch</h3>
    <p id="inventory-count">In Stock: 5</p>
    <button id="add-to-cart" disabled>Add to Cart</button>

    <script src="inventory.js"></script>
</body>
</html>
```

### JavaScript (inventory.js):

```javascript
let stock = 5;
const inventoryCount = document.getElementById("inventory-count");
const addToCartButton = document.getElementById("add-to-cart");

function updateInventory() {
    if (stock > 0) {
        addToCartButton.disabled = false;
        inventoryCount.textContent = `In Stock: ${stock}`;
    } else {
        addToCartButton.disabled = true;
        inventoryCount.textContent = "Out of Stock";
    }
}

addToCartButton.addEventListener("click", () => {
    stock--;
    updateInventory();
});

updateInventory(); // Initialize the page
```

### Explanation:

- The HTML file (`inventory.html`) displays the inventory count and an "Add to Cart" button.
- The JavaScript file (`inventory.js`) handles real-time inventory updates and disables the "Add to Cart" button when the stock reaches zero.

---

## 9. Conclusion

By separating HTML and JavaScript into different files, your codebase remains organized, scalable, and easier to maintain. **DOM manipulation** and **event handling** allow you to create interactive, dynamic web pages essential for modern business applications. Whether you're building an e-commerce site, handling form submissions, or managing inventory, understanding these concepts is key to delivering engaging user experiences.

### Key Takeaways:
- **DOM Manipulation**: Modify the content, structure, and style of a webpage using JavaScript.
- **Event Handling**: Respond to user interactions such as clicks, form submissions, and dropdown selections.
- **Separation of Concerns**: Keep HTML and JavaScript in separate files to improve code readability and maintainability.

Mastering DOM manipulation and event handling will enable you to create more dynamic, user-friendly business applications. 

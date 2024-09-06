# JavaScript Tutorial: Working with Objects

In JavaScript, objects are one of the most important and versatile data types. They are used to store collections of key-value pairs, making them incredibly useful for modeling real-world entities such as customers, products, and orders in business applications. In this tutorial, we'll explore how to use objects in JavaScript, including how to define them, access their properties, and use methods to perform actions.

## What is an Object in JavaScript?

An object in JavaScript is a collection of related data and functionality. Objects are made up of properties and methods. A **property** is a key-value pair, and a **method** is a function associated with an object.

### Creating an Object

You can create an object using object literals or using the `new Object()` syntax. Here's an example of an object using object literals:

```javascript
// Creating an object representing a product
let product = {
  name: "Laptop",
  price: 1200,
  inStock: true
};

// Accessing object properties
console.log(product.name);  // Output: Laptop
console.log(product.price); // Output: 1200
console.log(product.inStock); // Output: true
```

### Explanation:

- **Object Literal Syntax**: We define an object by using curly braces `{}` and specifying properties inside as key-value pairs.
- **Accessing Properties**: We use the dot notation (`object.property`) to access individual properties of the object. You can also use bracket notation (`object['property']`), which is useful for dynamic property names.

---

## Modifying and Adding Properties

You can easily modify an existing property or add new ones to an object.

### Example: Modifying and Adding Properties

```javascript
// Modify existing property
product.price = 1100; // Applying a discount

// Add a new property
product.category = "Electronics";

console.log(product.price);  // Output: 1100
console.log(product.category); // Output: Electronics
```

### Explanation:

- **Modifying a Property**: We simply assign a new value to an existing property.
- **Adding a New Property**: You can add new properties to an object dynamically, even after the object has been created.

---

## Using Methods in Objects

A **method** in JavaScript is a function stored as a property inside an object. Methods allow you to perform actions related to the object.

### Example: Defining Methods in an Object

Let's say you're managing an online store and you want to define a product object that includes methods to perform actions, such as calculating a discount and displaying product details.

```javascript
// Product object with methods
let productWithMethods = {
  name: "Smartphone",
  price: 700,
  inStock: true,

  // Method to apply a discount
  applyDiscount: function(discountRate) {
    productWithMethods.price = productWithMethods.price - (productWithMethods.price * discountRate);
    return productWithMethods.price;
  },

  // Method to display product details
  displayDetails: function() {
    return `Product: ${productWithMethods.name}\nPrice: $${productWithMethods.price}\nIn Stock: ${productWithMethods.inStock}`;
  }
};

// Using the methods
productWithMethods.applyDiscount(0.1); // Applying 10% discount
console.log(productWithMethods.displayDetails());
```

### Explanation:

- **Methods in Objects**: Methods are defined just like properties, but their values are functions. The `applyDiscount` method takes a `discountRate` and updates the `price` property of the object.
- **Calling Methods**: You can call methods using dot notation (`object.method()`), just like accessing properties.

---

## Working with Nested Objects

Objects in JavaScript can also contain other objects, known as nested objects. This is useful in real-world scenarios where an entity (like an order) contains multiple related entities (like customer information and items).

### Example: Working with Nested Objects

```javascript
let order = {
  orderID: 12345,
  customer: {
    name: "Jane Smith",
    email: "jane.smith@example.com"
  },
  items: [
    { productName: "Laptop", price: 1200 },
    { productName: "Mouse", price: 25 }
  ],

  // Method to calculate total order value
  calculateTotal: function() {
    return order.items.reduce((total, item) => total + item.price, 0);
  },

  // Method to display order summary
  displaySummary: function() {
    return `Order ID: ${order.orderID}\nCustomer: ${order.customer.name}\nTotal: $${order.calculateTotal()}`;
  }
};

// Display order summary
console.log(order.displaySummary());
```

### Explanation:

- **Nested Object**: The `customer` property is itself an object, containing customer details like `name` and `email`.
- **Array of Objects**: The `items` property is an array of objects, each representing a product in the order.
- **Using Methods with Nested Data**: The `calculateTotal` method uses `reduce()` to sum up the prices of items in the `items` array.

---

## Object Methods: `Object.keys()`, `Object.values()`, and `Object.entries()`

JavaScript provides built-in methods to work with objects, such as retrieving keys, values, and key-value pairs.

### Example: Using `Object.keys()`, `Object.values()`, and `Object.entries()`

```javascript
let product = {
  name: "Tablet",
  price: 400,
  inStock: true
};

// Get all keys of the object
console.log(Object.keys(product)); // Output: ["name", "price", "inStock"]

// Get all values of the object
console.log(Object.values(product)); // Output: ["Tablet", 400, true]

// Get key-value pairs of the object
console.log(Object.entries(product)); // Output: [["name", "Tablet"], ["price", 400], ["inStock", true]]
```

### Explanation:

- **`Object.keys()`**: Returns an array of the keys (property names) of an object.
- **`Object.values()`**: Returns an array of the values of the object's properties.
- **`Object.entries()`**: Returns an array of key-value pairs, where each pair is an array with two elements (the key and its value).

---

## Using Object Destructuring

Object destructuring is a syntax that allows you to unpack values from an object into variables, making it easier to work with complex objects.

### Example: Destructuring an Object

```javascript
let customer = {
  name: "Alice Johnson",
  email: "alice.johnson@example.com",
  phone: "123-456-7890"
};

// Destructuring object properties
let { name, email, phone } = customer;

console.log(`Customer Name: ${name}`);
console.log(`Customer Email: ${email}`);
console.log(`Customer Phone: ${phone}`);
```

### Explanation:

- **Object Destructuring**: The `{ name, email, phone }` syntax allows us to extract properties from the `customer` object and assign them to variables with the same name.
- **Simplified Code**: This technique reduces the amount of repetitive code when accessing multiple properties of an object.

---

## Conclusion

In JavaScript, objects are fundamental to building applications, especially in business use cases. They allow you to model real-world entities, store and manage data, and define behaviors using methods. By mastering objects, including properties, methods, and techniques like nested objects and destructuring, you can build more complex and dynamic applications.

**Key Takeaways:**
1. Objects are collections of key-value pairs.
2. Methods are functions stored in objects to define behavior.
3. Objects can be nested and can hold arrays, allowing you to model complex data structures.
4. JavaScript provides built-in methods like `Object.keys()` and `Object.entries()` for working with objects efficiently.

By practicing with these examples, you will gain a deeper understanding of how to work with objects in JavaScript, a critical skill for any developer working on business applications.
# Advanced JavaScript

#### Introduction

This tutorial will cover advanced JavaScript concepts, including objects and arrays, asynchronous JavaScript (promises, async/await, and callbacks), and error handling (try-catch blocks and error objects) using business case examples. By the end of this guide, you'll have a solid understanding of these essential JavaScript concepts applied to business scenarios.

#### Objects and Arrays

Objects and arrays are fundamental data structures in JavaScript that help in organizing and managing data efficiently.

##### 1. Objects

Objects are collections of key-value pairs. They are useful for storing related data and representing real-world entities.

- **Creating Objects**:
  - Objects can be created using object literals or the `new Object()` syntax.
  ```javascript
  let employee = {
      name: "John Doe",
      position: "Manager",
      department: "Sales",
      salary: 75000
  };
  console.log(employee); // Output: { name: 'John Doe', position: 'Manager', department: 'Sales', salary: 75000 }
  ```

- **Accessing Object Properties**:
  - Properties can be accessed using dot notation or bracket notation.
  ```javascript
  console.log(employee.name); // Output: John Doe
  console.log(employee["position"]); // Output: Manager
  ```

- **Adding and Updating Properties**:
  - Properties can be added or updated dynamically.
  ```javascript
  employee.email = "john.doe@company.com";
  employee.salary = 80000;
  console.log(employee); // Output: { name: 'John Doe', position: 'Manager', department: 'Sales', salary: 80000, email: 'john.doe@company.com' }
  ```

- **Deleting Properties**:
  - Properties can be deleted using the `delete` operator.
  ```javascript
  delete employee.department;
  console.log(employee); // Output: { name: 'John Doe', position: 'Manager', salary: 80000, email: 'john.doe@company.com' }
  ```

- **Business Case Example**:
  - Imagine you need to store and manage data about different products in your inventory:
  ```javascript
  let product = {
      id: 101,
      name: "Laptop",
      price: 1200,
      stock: 30
  };
  console.log(product); // Output: { id: 101, name: 'Laptop', price: 1200, stock: 30 }

  // Update stock after a sale
  product.stock -= 5; // 5 units sold
  console.log(product.stock); // Output: 25

  // Add a new property for category
  product.category = "Electronics";
  console.log(product); // Output: { id: 101, name: 'Laptop', price: 1200, stock: 25, category: 'Electronics' }
  ```

##### 2. Arrays

Arrays are ordered collections of values. They are useful for storing lists of data.

- **Creating Arrays**:
  - Arrays can be created using array literals or the `new Array()` syntax.
  ```javascript
  let products = ["Laptop", "Tablet", "Smartphone"];
  console.log(products); // Output: [ 'Laptop', 'Tablet', 'Smartphone' ]
  ```

- **Accessing Array Elements**:
  - Elements can be accessed using their index.
  ```javascript
  console.log(products[0]); // Output: Laptop
  console.log(products[1]); // Output: Tablet
  ```

- **Adding and Removing Elements**:
  - Elements can be added using `push()` (to the end) or `unshift()` (to the beginning).
  - Elements can be removed using `pop()` (from the end) or `shift()` (from the beginning).
  ```javascript
  products.push("Smartwatch"); // Add to the end
  products.unshift("Desktop"); // Add to the beginning
  console.log(products); // Output: [ 'Desktop', 'Laptop', 'Tablet', 'Smartphone', 'Smartwatch' ]

  products.pop(); // Remove from the end
  products.shift(); // Remove from the beginning
  console.log(products); // Output: [ 'Laptop', 'Tablet', 'Smartphone' ]
  ```

- **Iterating Over Arrays**:
  - Arrays can be iterated over using `forEach()`, `for...of`, or traditional `for` loops.
  ```javascript
  products.forEach((product) => {
      console.log("Product:", product);
  });
  // Output:
  // Product: Laptop
  // Product: Tablet
  // Product: Smartphone
  ```

- **Business Case Example**:
  - Suppose you need to manage a list of orders in an e-commerce application:
  ```javascript
  let orders = [
      { orderId: 1, product: "Laptop", quantity: 2 },
      { orderId: 2, product: "Tablet", quantity: 1 },
      { orderId: 3, product: "Smartphone", quantity: 3 }
  ];

  // Iterate over the orders and display order details
  orders.forEach((order) => {
      console.log(`Order ${order.orderId}: ${order.quantity} x ${order.product}`);
  });
  // Output:
  // Order 1: 2 x Laptop
  // Order 2: 1 x Tablet
  // Order 3: 3 x Smartphone

  // Add a new order
  orders.push({ orderId: 4, product: "Smartwatch", quantity: 1 });
  console.log(orders);
  // Output: [
  //   { orderId: 1, product: 'Laptop', quantity: 2 },
  //   { orderId: 2, product: 'Tablet', quantity: 1 },
  //   { orderId: 3, product: 'Smartphone', quantity: 3 },
  //   { orderId: 4, product: 'Smartwatch', quantity: 1 }
  // ]

  // Remove the first order
  orders.shift();
  console.log(orders);
  // Output: [
  //   { orderId: 2, product: 'Tablet', quantity: 1 },
  //   { orderId: 3, product: 'Smartphone', quantity: 3 },
  //   { orderId: 4, product: 'Smartwatch', quantity: 1 }
  // ]
  ```

#### Asynchronous JavaScript

Asynchronous programming allows JavaScript to perform tasks without blocking the main thread, making it possible to handle operations like API calls, file reading, and timers efficiently.

##### 1. Callbacks

Callbacks are functions passed as arguments to other functions and are executed after the completion of asynchronous operations.

- **Using Callbacks**:
  - Callbacks can be used to handle the results of asynchronous operations.
  ```javascript
  function fetchData(callback) {
      setTimeout(() => {
          let data = "Sample data";
          callback(data);
      }, 1000);
  }

  function processData(data) {
      console.log("Processing:", data);
  }

  fetchData(processData); // Output after 1 second: Processing: Sample data
  ```

- **Business Case Example**:
  - Fetching user data from a server and processing it:
  ```javascript
  function getUserData(userId, callback) {
      setTimeout(() => {
          let userData = { id: userId, name: "Jane Doe" };
          callback(userData);
      }, 2000);
  }

  function displayUserData(userData) {
      console.log(`User ID: ${userData.id}, Name: ${userData.name}`);
  }

  getUserData(1, displayUserData); // Output after 2 seconds: User ID: 1, Name: Jane Doe
  ```

##### 2. Promises

Promises provide a cleaner way to handle asynchronous operations and avoid callback hell.

- **Creating and Using Promises**:
  - Promises represent the eventual completion (or failure) of an asynchronous operation and its resulting value.
  ```javascript
  let fetchData = new Promise((resolve, reject) => {
      setTimeout(() => {
          let data = "Sample data";
          resolve(data);
      }, 1000);
  });

  fetchData.then((data) => {
      console.log("Processing:", data);
  }).catch((error) => {
      console.error("Error:", error);
  });
  ```

- **Business Case Example**:
  - Fetching product details from a server:
  ```javascript
  function getProductDetails(productId) {
      return new Promise((resolve, reject) => {
          setTimeout(() => {
              let product = { id: productId, name: "Laptop", price: 1200 };
              resolve(product);
          }, 2000);
      });
  }

  getProductDetails(101).then((product) => {
      console.log(`Product ID: ${product.id}, Name: ${product.name}, Price: $${product.price}`);
  }).catch((error) => {
      console.error("Error:", error);
  });
  // Output after 2 seconds: Product ID: 101, Name: Laptop, Price: $1200
  ```

##### 3. Async/Await

Async/await is syntactic sugar for promises, providing a more readable and concise way to handle asynchronous operations.

- **Using Async/Await**:
  - Async functions return a promise, and `await` can be used to wait for the promise to resolve.
  ```javascript
  async function fetchData() {
      let data = await new Promise((resolve) => {
          setTimeout

(() => {
              resolve("Sample data");
          }, 1000);
      });
      console.log("Processing:", data);
  }

  fetchData(); // Output after 1 second: Processing: Sample data
  ```

- **Business Case Example**:
  - Fetching order details from a server:
  ```javascript
  async function getOrderDetails(orderId) {
      let order = await new Promise((resolve) => {
          setTimeout(() => {
              resolve({ id: orderId, product: "Laptop", quantity: 2 });
          }, 2000);
      });
      console.log(`Order ID: ${order.id}, Product: ${order.product}, Quantity: ${order.quantity}`);
  }

  getOrderDetails(1); // Output after 2 seconds: Order ID: 1, Product: Laptop, Quantity: 2
  ```

#### Error Handling

Error handling is crucial in JavaScript to manage and respond to runtime errors gracefully.

##### 1. Try-Catch Blocks

Try-catch blocks allow you to catch and handle errors that occur during code execution.

- **Using Try-Catch**:
  - Try-catch blocks can be used to handle synchronous errors.
  ```javascript
  try {
      let result = 10 / 0; // This will not throw an error
      console.log(result); // Output: Infinity
  } catch (error) {
      console.error("Error:", error.message);
  }

  try {
      let result = JSON.parse('{"key": "value"}'); // Valid JSON
      console.log(result); // Output: { key: 'value' }
  } catch (error) {
      console.error("Error:", error.message);
  }

  try {
      let result = JSON.parse('Invalid JSON'); // Invalid JSON
      console.log(result);
  } catch (error) {
      console.error("Error:", error.message); // Output: Error: Unexpected token I in JSON at position 0
  }
  ```

- **Business Case Example**:
  - Handling errors during data processing:
  ```javascript
  function processData(data) {
      try {
          if (!data) {
              throw new Error("No data provided");
          }
          console.log("Processing data:", data);
      } catch (error) {
          console.error("Error:", error.message);
      }
  }

  processData(null); // Error: No data provided
  processData("Valid data"); // Output: Processing data: Valid data
  ```

##### 2. Error Objects

Error objects provide detailed information about errors, including their name and message.

- **Creating and Throwing Error Objects**:
  - Error objects can be created and thrown to indicate specific error conditions.
  ```javascript
  function divide(a, b) {
      if (b === 0) {
          throw new Error("Division by zero");
      }
      return a / b;
  }

  try {
      let result = divide(10, 0);
      console.log(result);
  } catch (error) {
      console.error("Error:", error.message); // Output: Error: Division by zero
  }

  try {
      let result = divide(10, 2);
      console.log(result); // Output: 5
  } catch (error) {
      console.error("Error:", error.message);
  }
  ```

- **Business Case Example**:
  - Handling errors during user authentication:
  ```javascript
  function authenticateUser(username, password) {
      try {
          if (!username || !password) {
              throw new Error("Missing credentials");
          }
          if (username !== "admin" || password !== "admin123") {
              throw new Error("Invalid credentials");
          }
          console.log("User authenticated successfully");
      } catch (error) {
          console.error("Authentication Error:", error.message);
      }
  }

  authenticateUser("admin", "wrongpassword"); // Authentication Error: Invalid credentials
  authenticateUser("admin", "admin123"); // Output: User authenticated successfully

  try {
      authenticateUser("", ""); // Authentication Error: Missing credentials
  } catch (error) {
      console.error("Error:", error.message);
  }
  ```

#### Conclusion

By understanding objects and arrays, asynchronous JavaScript, and error handling through these business-related examples, you can create more robust and efficient web applications that handle real-world business scenarios effectively. Practice these concepts to build a strong foundation in advanced JavaScript programming.

### Further Reading
- [MDN Web Docs: JavaScript Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
- [MDN Web Docs: JavaScript Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [MDN Web Docs: Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN Web Docs: async/await](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await)
- [MDN Web Docs: Error Handling](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling#Exception_handling_statements)
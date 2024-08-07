# Asynchronous JavaScript

#### Introduction

Asynchronous programming is essential for handling operations that take time, such as fetching data from a server, without blocking the execution of other code. This tutorial will cover callbacks, promises, and async/await in JavaScript, using business case examples. By mastering these concepts, you can create efficient and responsive web applications.

#### Callbacks

Callbacks are functions passed as arguments to other functions and are executed after the completion of an asynchronous operation.

##### Using Callbacks

**Example**:
Suppose you need to fetch user data from a server and process it once it's retrieved.

```javascript
function fetchUserData(userId, callback) {
    // Simulate a server request with setTimeout
    setTimeout(() => {
        let userData = { id: userId, name: "Jane Doe", position: "Manager" };
        callback(userData);
    }, 2000);
}

function processUserData(userData) {
    console.log(`User ID: ${userData.id}, Name: ${userData.name}, Position: ${userData.position}`);
}

fetchUserData(1, processUserData);
```

**Explanation**:
In this example, `fetchUserData` simulates an asynchronous server request using `setTimeout`. The `callback` parameter is a function that will be executed once the user data is fetched. We pass `processUserData` as the callback function, which processes and logs the user data. This approach allows for handling asynchronous operations by passing functions that execute when the operation completes.

#### Promises

Promises provide a cleaner way to handle asynchronous operations and avoid callback hell. A promise represents a value that may be available now, or in the future, or never.

##### Creating and Using Promises

**Example**:
Suppose you need to fetch product details from a server.

```javascript
function getProductDetails(productId) {
    return new Promise((resolve, reject) => {
        // Simulate a server request with setTimeout
        setTimeout(() => {
            if (productId === 101) {
                resolve({ id: productId, name: "Laptop", price: 1200 });
            } else {
                reject("Product not found");
            }
        }, 2000);
    });
}

getProductDetails(101)
    .then((product) => {
        console.log(`Product: ${product.name}, Price: $${product.price}`);
    })
    .catch((error) => {
        console.error("Error:", error);
    });
```

**Explanation**:
In this example, `getProductDetails` returns a promise that simulates an asynchronous server request. The promise is resolved if the `productId` is `101`, returning the product details. Otherwise, it is rejected with an error message. The `.then()` method handles the resolved promise, logging the product details, while the `.catch()` method handles any errors.

##### Chaining Promises

**Example**:
Suppose you need to fetch a list of products, then fetch details for each product.

```javascript
function getProductList() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve([101, 102, 103]);
        }, 1000);
    });
}

function getProductDetails(productId) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (productId === 101) {
                resolve({ id: productId, name: "Laptop", price: 1200 });
            } else if (productId === 102) {
                resolve({ id: productId, name: "Tablet", price: 600 });
            } else if (productId === 103) {
                resolve({ id: productId, name: "Smartphone", price: 800 });
            } else {
                reject("Product not found");
            }
        }, 2000);
    });
}

getProductList()
    .then((productIds) => {
        return Promise.all(productIds.map(getProductDetails));
    })
    .then((products) => {
        products.forEach((product) => {
            console.log(`Product: ${product.name}, Price: $${product.price}`);
        });
    })
    .catch((error) => {
        console.error("Error:", error);
    });
```

**Explanation**:
In this example, `getProductList` returns a promise that resolves to a list of product IDs. We then use `Promise.all` to fetch details for each product ID concurrently. The `.then()` method processes the array of product details, logging each product's name and price. The `.catch()` method handles any errors that occur during the process.

#### Async/Await

Async/await is syntactic sugar for promises, providing a more readable and concise way to handle asynchronous operations.

##### Using Async/Await

**Example**:
Suppose you need to fetch order details from a server.

```javascript
function getOrderDetails(orderId) {
    return new Promise((resolve, reject) => {
        // Simulate a server request with setTimeout
        setTimeout(() => {
            if (orderId === 1) {
                resolve({ id: orderId, product: "Laptop", quantity: 2 });
            } else {
                reject("Order not found");
            }
        }, 2000);
    });
}

async function displayOrderDetails(orderId) {
    try {
        let order = await getOrderDetails(orderId);
        console.log(`Order ID: ${order.id}, Product: ${order.product}, Quantity: ${order.quantity}`);
    } catch (error) {
        console.error("Error:", error);
    }
}

displayOrderDetails(1);
```

**Explanation**:
In this example, `getOrderDetails` returns a promise that simulates an asynchronous server request. The `displayOrderDetails` function is an async function that uses the `await` keyword to wait for the promise to resolve. If the promise is resolved, the order details are logged. If the promise is rejected, an error is caught and logged. This approach makes the code more readable and easier to manage compared to chaining `.then()` and `.catch()` methods.

##### Handling Multiple Asynchronous Operations

**Example**:
Suppose you need to fetch multiple orders and process them concurrently.

```javascript
function getOrderDetails(orderId) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (orderId === 1) {
                resolve({ id: orderId, product: "Laptop", quantity: 2 });
            } else if (orderId === 2) {
                resolve({ id: orderId, product: "Tablet", quantity: 1 });
            } else if (orderId === 3) {
                resolve({ id: orderId, product: "Smartphone", quantity: 3 });
            } else {
                reject("Order not found");
            }
        }, 2000);
    });
}

async function displayAllOrderDetails() {
    try {
        let orderIds = [1, 2, 3];
        let orderPromises = orderIds.map(getOrderDetails);
        let orders = await Promise.all(orderPromises);
        orders.forEach((order) => {
            console.log(`Order ID: ${order.id}, Product: ${order.product}, Quantity: ${order.quantity}`);
        });
    } catch (error) {
        console.error("Error:", error);
    }
}

displayAllOrderDetails();
```

**Explanation**:
In this example, we create an async function `displayAllOrderDetails` to fetch and process multiple orders concurrently. We map the `orderIds` array to an array of promises using `getOrderDetails`, then use `Promise.all` to wait for all promises to resolve. The `orders` array contains the resolved order details, which are then logged. If any promise is rejected, the error is caught and logged. This approach allows handling multiple asynchronous operations efficiently.

#### Conclusion

By understanding and using callbacks, promises, and async/await in JavaScript through these business-related examples, you can create efficient and responsive web applications that handle asynchronous operations effectively. Practice these concepts to build a strong foundation in JavaScript programming.

### Further Reading
- [MDN Web Docs: Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN Web Docs: async/await](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await)
- [JavaScript.info: Promises](https://javascript.info/promise-basics)
- [JavaScript.info: Async/await](https://javascript.info/async-await)
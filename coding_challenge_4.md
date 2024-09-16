### Answer Key for the Inventory Management System

Below is the solution for the **Inventory Management System** coding challenge. Each function is explained in detail to help understand how to solve the problem.

---

### 1. **Initialize Inventory with Product Objects**

We will start by initializing the `inventory` array with the sample product objects.

**Code:**
```javascript
const inventory = [
    { name: 'Laptop', price: 1200, quantity: 10, lowStockLevel: 3 },
    { name: 'Smartphone', price: 800, quantity: 5, lowStockLevel: 2 },
    { name: 'Tablet', price: 400, quantity: 7, lowStockLevel: 1 },
    { name: 'Headphones', price: 100, quantity: 15, lowStockLevel: 5 },
    { name: 'Smartwatch', price: 250, quantity: 3, lowStockLevel: 1 }
];
```

- **Explanation**: Each product is represented as an object with four properties: `name`, `price`, `quantity`, and `lowStockLevel`. The `inventory` array stores all these product objects.

---

### 2. **Display Product Details**

**Code:**
```javascript
function displayProductDetails(product) {
    const stockStatus = product.quantity <= product.lowStockLevel ? "Low Stock" : "In Stock";
    console.log(`Product: ${product.name}, Price: $${product.price}, Quantity: ${product.quantity}, Status: ${stockStatus}`);
}
```

- **Explanation**:
  - The function takes a `product` object as input.
  - It uses a ternary operator to determine whether the stock is "Low Stock" or "In Stock" by comparing the product's quantity with its `lowStockLevel`.
  - `console.log()` is used to display the product's name, price, quantity, and stock status.

**Example Call**:
```javascript
displayProductDetails(inventory[0]);
```

---

### 3. **Update Product Stock After Sales**

**Code:**
```javascript
function updateStock(product, unitsSold) {
    if (unitsSold > product.quantity) {
        console.log(`Cannot sell ${unitsSold} units. Only ${product.quantity} units in stock.`);
    } else {
        product.quantity -= unitsSold;
        console.log(`${unitsSold} units of ${product.name} sold. Remaining stock: ${product.quantity}`);
        if (product.quantity <= 0) {
            console.log(`${product.name} is now out of stock!`);
        } else if (product.quantity <= product.lowStockLevel) {
            console.log(`${product.name} is running low on stock!`);
        }
    }
}
```

- **Explanation**:
  - The function first checks if the number of units sold exceeds the available quantity. If so, it logs an error message.
  - If the sale is valid, it subtracts `unitsSold` from the product's quantity and logs the new stock level.
  - The function also checks whether the product is out of stock or running low and logs the appropriate message.

**Example Call**:
```javascript
updateStock(inventory[0], 5);
```

---

### 4. **Check Low Stock Products**

**Code:**
```javascript
function checkLowStock(inventory) {
    inventory.forEach(product => {
        if (product.quantity <= product.lowStockLevel) {
            console.log(`${product.name} is low on stock. Remaining quantity: ${product.quantity}`);
        }
    });
}
```

- **Explanation**:
  - The `checkLowStock` function loops through the `inventory` array using `forEach()`.
  - It checks each product’s quantity against its `lowStockLevel`. If a product is low on stock, it logs the product's name and remaining quantity.

**Example Call**:
```javascript
checkLowStock(inventory);
```

---

### 5. **Calculate Total Inventory Value**

**Code:**
```javascript
function calculateInventoryValue(inventory) {
    const totalValue = inventory.reduce((sum, product) => sum + (product.price * product.quantity), 0);
    return totalValue;
}
```

- **Explanation**:
  - The `reduce()` method is used to sum the total value of the inventory. The value of each product is calculated by multiplying its `price` by its `quantity`, and the result is added to the running total (`sum`).
  - The function returns the total inventory value.

**Example Call**:
```javascript
const totalValue = calculateInventoryValue(inventory);
console.log(`Total Inventory Value: $${totalValue}`);
```

---

### 6. **Process a Sale**

**Code:**
```javascript
function processSale(productName, unitsSold, inventory) {
    const product = inventory.find(item => item.name === productName);
    if (product) {
        updateStock(product, unitsSold);
    } else {
        console.log(`Error: ${productName} is not in the inventory.`);
    }
}
```

- **Explanation**:
  - The function first tries to find the product in the `inventory` array using the `find()` method, which returns the product object if a match is found by `name`.
  - If the product is found, it calls `updateStock()` to reduce the quantity by `unitsSold`.
  - If the product is not found, an error message is logged.

**Example Call**:
```javascript
processSale('Laptop', 2, inventory);
```

---

### Testing the Complete Solution with Sample Data

To test all the functions, you can run the following code:

```javascript
console.log("--- Displaying Product Details ---");
displayProductDetails(inventory[1]);

console.log("\n--- Processing a Sale ---");
processSale('Smartphone', 3, inventory);

console.log("\n--- Checking Low Stock ---");
checkLowStock(inventory);

console.log("\n--- Calculating Total Inventory Value ---");
const totalInventoryValue = calculateInventoryValue(inventory);
console.log(`Total Inventory Value: $${totalInventoryValue}`);
```

**Expected Output**:
```
--- Displaying Product Details ---
Product: Smartphone, Price: $800, Quantity: 5, Status: In Stock

--- Processing a Sale ---
3 units of Smartphone sold. Remaining stock: 2
Smartphone is running low on stock!

--- Checking Low Stock ---
Smartphone is low on stock. Remaining quantity: 2
Smartwatch is low on stock. Remaining quantity: 3

--- Calculating Total Inventory Value ---
Total Inventory Value: $27250
```

---

### Summary

- The solution covers creating product objects, updating stock levels, checking for low stock, calculating inventory value, and processing sales.
- **Control Structures** like `if` statements and loops are used for decision-making and iterations.
- **Array Methods** like `forEach()`, `reduce()`, and `find()` are used to manipulate and process the `inventory` array.
- The functions are modular, reusable, and can easily be adapted for more complex business logic.

By following this answer key, students will gain hands-on experience with objects, arrays, control structures, and key JavaScript methods relevant to business scenarios like inventory management.
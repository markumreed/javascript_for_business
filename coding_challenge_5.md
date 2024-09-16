### Coding Challenge: Customer Order Management System

**Introduction**: In this challenge, you will create a simple system to manage customer orders for a small coffee shop. The system will track customer orders, calculate the total amount due for each order, check the status of orders, and manage inventory for the coffee shop. You’ll use objects to represent orders and products, arrays to store multiple orders, and array/object methods to manipulate the data.

---

### Business Case

**Scenario**: A coffee shop wants to automate their customer order process. They need a system that:
1. Takes customer orders and adds them to the list of current orders.
2. Calculates the total amount due for each customer based on their order.
3. Manages the inventory, ensuring there are enough products available to fulfill orders.
4. Tracks the status of orders (Pending, Completed).

---

### Tasks

1. **Create an Inventory Array of Product Objects**

   - Create an array named `inventory` that contains at least 4 product objects. Each product should have the following properties:
     - `name` (string): The name of the product.
     - `price` (number): The price of one unit of the product.
     - `quantity` (number): The number of units currently in stock.
   - **Commit**: `"Initialize inventory with product objects"`

2. **Create an Orders Array of Order Objects**

   - Create an empty array named `orders` to store customer orders. Each order object will have the following properties:
     - `customerName` (string): The name of the customer.
     - `items` (array of objects): Each object in the array represents a product ordered and should have the `name` of the product and the `quantity` ordered.
     - `status` (string): The status of the order, which is either `"Pending"` or `"Completed"`.
   - **Commit**: `"Initialize orders array"`

3. **Create a Function to Place an Order**

   - Write a function named `placeOrder` that accepts the customer name and an array of ordered items. The function should:
     - Check if there are enough products in stock for each item in the order. If any item has insufficient stock, log an error message and do not place the order.
     - If all items are available, subtract the ordered quantity from the product's stock in the `inventory` array.
     - Add a new order to the `orders` array with the `status` set to `"Pending"`.
   - **Commit**: `"Create placeOrder function"`

4. **Create a Function to Calculate Total for an Order**

   - Write a function named `calculateOrderTotal` that accepts an order object and calculates the total price of the order by summing the prices of all ordered items.
   - **Commit**: `"Create calculateOrderTotal function"`

5. **Create a Function to Mark an Order as Completed**

   - Write a function named `completeOrder` that accepts a customer name. The function should find the order with the matching `customerName` in the `orders` array and change its `status` to `"Completed"`. If the order is not found, log an error message.
   - **Commit**: `"Create completeOrder function"`

6. **Create a Function to Check Pending Orders**

   - Write a function named `checkPendingOrders` that iterates over the `orders` array and logs the details of all orders that are still `"Pending"`.
   - **Commit**: `"Create checkPendingOrders function"`

---

### Hints

- Use the `find()` method to locate a product or order by name.
- Use the `forEach()` method to iterate over arrays for operations like checking inventory or orders.
- Use `reduce()` or simple loops to calculate the total price of an order.
- Handle edge cases, such as insufficient stock or attempting to complete an order that doesn’t exist.

---

### Sample Data for Inventory Initialization

```javascript
const inventory = [
    { name: 'Espresso', price: 3, quantity: 10 },
    { name: 'Latte', price: 4, quantity: 5 },
    { name: 'Cappuccino', price: 4, quantity: 6 },
    { name: 'Mocha', price: 5, quantity: 4 }
];
```

---

### Submission Guidelines

- **GitHub Repository**: Share the location of your GitHub repository containing your project. Your repository should include a well-documented JavaScript file named `order_management_system.js`, along with any additional files or documentation pertinent to the project.
  
- **Key Points for Submission**:
  - **Repository Link**: Ensure your repository is public or accessible to your instructors. Share the direct URL to your repository.
  - **Code Organization and Documentation**: Your code should be well-organized, clearly commented, and easy to understand. Use consistent naming conventions for variables and functions, and ensure proper indentation and spacing.
  - **Version Control Practices**: Commit changes frequently with clear, descriptive messages to track your development progress.

---

### Expected Outcomes

After completing this challenge, students will understand how to:

- Create and manipulate objects and arrays in JavaScript.
- Use array methods like `find()`, `forEach()`, and `reduce()` for various operations.
- Implement control structures to check conditions and handle real-world problems, such as stock availability.
- Use GitHub for version control and demonstrate professional coding practices.
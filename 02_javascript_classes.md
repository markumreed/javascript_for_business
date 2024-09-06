# JavaScript Classes Tutorial

JavaScript introduced classes in ES6 (ECMAScript 2015) to provide a more intuitive and cleaner way to define objects and manage inheritance. Classes in JavaScript are syntactical sugar over the prototype-based inheritance model and allow developers to easily define object blueprints, organize methods, and handle inheritance. In this tutorial, we'll explore how to use JavaScript classes, focusing on practical business case examples to demonstrate real-world usage.

## What is a Class in JavaScript?

A class is a blueprint for creating objects with predefined properties and methods. It helps organize code by grouping related data and behaviors.

### Defining a Class

The basic syntax for defining a class in JavaScript is as follows:

```javascript
class ClassName {
  constructor(parameters) {
    // Initialize properties
  }

  methodName() {
    // Define method
  }
}
```

- **constructor()**: A special method that gets called when a new instance of the class is created.
- **methods**: Functions that belong to the class and can be used by any instance of the class.

---

## 1. Business Case Example: Managing Employees

Let's define a class to model employee data in a business application. This class will hold information such as the employee's name, position, and salary. It will also have methods to promote the employee and adjust their salary.

### Example: Employee Class

```javascript
// Employee Class
class Employee {
  constructor(name, position, salary) {
    this.name = name;
    this.position = position;
    this.salary = salary;
  }

  // Method to promote an employee
  promote(newPosition) {
    this.position = newPosition;
    console.log(`${this.name} has been promoted to ${this.position}`);
  }

  // Method to increase salary
  increaseSalary(amount) {
    this.salary += amount;
    console.log(`${this.name}'s new salary is $${this.salary}`);
  }

  // Method to display employee details
  displayDetails() {
    return `Employee: ${this.name}, Position: ${this.position}, Salary: $${this.salary}`;
  }
}

// Creating a new Employee object
let employee1 = new Employee("John Doe", "Junior Developer", 50000);

// Promoting the employee and increasing salary
employee1.promote("Senior Developer");
employee1.increaseSalary(10000);

// Displaying employee details
console.log(employee1.displayDetails());
```

### Explanation:

- **constructor()**: The `constructor()` method is used to initialize the `Employee` object with properties `name`, `position`, and `salary`.
- **promote() Method**: This method changes the employee's position and logs a promotion message.
- **increaseSalary() Method**: This method adds a specified amount to the employee's current salary and logs the updated salary.
- **displayDetails() Method**: This method returns a string summarizing the employee's details, which can be logged to the console or displayed in the UI.
- **New Employee**: We create a new `Employee` instance (`employee1`) and invoke its methods to change its state and display its details.

---

## 2. Business Case Example: Product Management in an Online Store

Let’s consider managing products in an online store. Each product will have a name, price, and stock quantity, and we'll define methods to manage the stock and apply discounts.

### Example: Product Class

```javascript
// Product Class
class Product {
  constructor(name, price, stock) {
    this.name = name;
    this.price = price;
    this.stock = stock;
  }

  // Method to apply a discount
  applyDiscount(discountRate) {
    this.price = this.price - (this.price * discountRate);
    console.log(`${this.name} is now priced at $${this.price.toFixed(2)}`);
  }

  // Method to update stock
  updateStock(amount) {
    this.stock += amount;
    console.log(`Updated stock for ${this.name}: ${this.stock} units available`);
  }

  // Method to display product details
  displayProductInfo() {
    return `Product: ${this.name}, Price: $${this.price}, Stock: ${this.stock}`;
  }
}

// Creating a new Product object
let product1 = new Product("Laptop", 1500, 20);

// Applying discount and updating stock
product1.applyDiscount(0.1); // 10% discount
product1.updateStock(50); // Adding 50 more units to stock

// Displaying product details
console.log(product1.displayProductInfo());
```

### Explanation:

- **applyDiscount() Method**: This method reduces the product's price by a specified discount rate (e.g., 10%). It uses `toFixed(2)` to format the price to two decimal places.
- **updateStock() Method**: This method adds new units to the existing stock.
- **displayProductInfo() Method**: This method returns the product's details, including its name, price, and available stock.
- **New Product**: We create a `Product` instance (`product1`) and modify its price and stock using the methods, then display the product information.

---

## 3. Business Case Example: Customer Management System

In this example, we'll model a customer in a retail system. Each customer has a name, email, and purchase history. The class will have methods for adding purchases and calculating the total amount spent.

### Example: Customer Class

```javascript
// Customer Class
class Customer {
  constructor(name, email) {
    this.name = name;
    this.email = email;
    this.purchaseHistory = [];
  }

  // Method to add a purchase
  addPurchase(item, price) {
    this.purchaseHistory.push({ item, price });
    console.log(`${item} added to ${this.name}'s purchase history.`);
  }

  // Method to calculate total amount spent
  getTotalSpent() {
    let total = this.purchaseHistory.reduce((sum, purchase) => sum + purchase.price, 0);
    return `Total amount spent by ${this.name}: $${total}`;
  }

  // Method to display customer details
  displayCustomerDetails() {
    return `Customer: ${this.name}, Email: ${this.email}, Purchases: ${this.purchaseHistory.length}`;
  }
}

// Creating a new Customer object
let customer1 = new Customer("Jane Smith", "jane.smith@example.com");

// Adding purchases and displaying total spent
customer1.addPurchase("Smartphone", 800);
customer1.addPurchase("Tablet", 400);
console.log(customer1.getTotalSpent());

// Displaying customer details
console.log(customer1.displayCustomerDetails());
```

### Explanation:

- **addPurchase() Method**: This method adds a purchase to the customer's purchase history. The purchase is represented as an object with `item` and `price`.
- **getTotalSpent() Method**: This method calculates the total amount spent by the customer by summing up all prices in the `purchaseHistory` array.
- **displayCustomerDetails() Method**: This method returns the customer's details, including their name, email, and the number of purchases.
- **New Customer**: We create a `Customer` instance (`customer1`) and add purchases, calculate the total spent, and display the customer’s details.

---

## 4. Business Case Example: Employee Hierarchy with Inheritance

In this example, we'll use inheritance to model two types of employees: Regular Employees and Managers. Managers have an additional responsibility to manage a team, so the `Manager` class will inherit from the `Employee` class.

### Example: Inheritance with `Employee` and `Manager` Classes

```javascript
// Employee Class
class Employee {
  constructor(name, position, salary) {
    this.name = name;
    this.position = position;
    this.salary = salary;
  }

  // Method to display employee details
  displayDetails() {
    return `Employee: ${this.name}, Position: ${this.position}, Salary: $${this.salary}`;
  }
}

// Manager Class inheriting from Employee
class Manager extends Employee {
  constructor(name, position, salary, teamSize) {
    super(name, position, salary); // Call the parent class constructor
    this.teamSize = teamSize;
  }

  // Method to display manager details
  displayDetails() {
    return `${super.displayDetails()}, Team Size: ${this.teamSize}`;
  }

  // Method to increase team size
  increaseTeamSize(amount) {
    this.teamSize += amount;
    console.log(`${this.name}'s team size is now ${this.teamSize}`);
  }
}

// Creating a Manager object
let manager1 = new Manager("Alice Brown", "Project Manager", 90000, 10);

// Increasing team size and displaying manager details
manager1.increaseTeamSize(5);
console.log(manager1.displayDetails());
```

### Explanation:

- **Inheritance**: The `Manager` class extends the `Employee` class, allowing it to inherit the properties and methods of `Employee`. The `super()` function is used to call the constructor of the parent class (`Employee`).
- **Overriding Methods**: The `displayDetails()` method in `Manager` overrides the one in `Employee`, but it still uses `super.displayDetails()` to include the original functionality from the parent class.
- **New Manager**: We create a `Manager` instance (`manager1`) and use its methods to modify the team size and display the manager’s details.

---

## 5. Business Case Example: Managing Orders with Static Methods

Sometimes, you need utility methods that don't belong to a specific instance of the class but instead to the class itself. In this case, we can use static methods.

### Example: Order Class with Static Methods

```javascript
// Order Class
class Order {
  constructor(orderID, product, quantity, pricePerUnit

) {
    this.orderID = orderID;
    this.product = product;
    this.quantity = quantity;
    this.pricePerUnit = pricePerUnit;
  }

  // Method to calculate the total price for this order
  calculateTotalPrice() {
    return this.quantity * this.pricePerUnit;
  }

  // Static method to calculate total sales from multiple orders
  static calculateTotalSales(orders) {
    return orders.reduce((total, order) => total + order.calculateTotalPrice(), 0);
  }
}

// Creating multiple orders
let order1 = new Order(1, "Laptop", 2, 1200);
let order2 = new Order(2, "Smartphone", 5, 800);

// Calculating total sales using static method
let totalSales = Order.calculateTotalSales([order1, order2]);
console.log(`Total Sales: $${totalSales}`);
```

### Explanation:

- **calculateTotalPrice() Method**: This method calculates the total price for a single order based on the quantity and price per unit.
- **Static Method (`calculateTotalSales`)**: Static methods are called on the class itself, not on instances. The `calculateTotalSales` method calculates the total sales from an array of `Order` objects.
- **New Orders**: We create multiple `Order` instances and then calculate the total sales using the static method.

---

## Conclusion

JavaScript classes provide a powerful way to structure and organize your code, making it easier to model real-world entities like employees, products, customers, and orders. In this tutorial, we covered:

1. Defining a class and its methods.
2. Using methods to manage employee data and promotions.
3. Managing products in an online store, including stock and discounts.
4. Handling customers and their purchase history.
5. Leveraging inheritance to create specialized types of employees.
6. Using static methods to calculate data that applies to all instances of a class.

Classes are a crucial tool for building scalable and maintainable JavaScript applications, especially in business scenarios.

**Happy coding!**
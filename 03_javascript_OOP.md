# Object-Oriented Programming (OOP) in JavaScript

Object-Oriented Programming (OOP) is a programming paradigm that organizes software design around data (objects) and the operations (methods) that can be performed on the data. OOP is widely used in JavaScript to create reusable and maintainable code. This tutorial will cover the basics of OOP in JavaScript, explaining key concepts such as objects, classes, inheritance, encapsulation, and polymorphism.

---

## 1. Introduction to Object-Oriented Programming (OOP)

OOP is a design pattern used in programming to structure and model software around objects, which represent real-world entities. These objects contain both data (properties) and functions (methods). OOP principles help make code more modular, reusable, and easier to maintain. The four core concepts of OOP are:

- **Encapsulation**: Bundling data (properties) and methods (functions) together into objects.
- **Abstraction**: Hiding implementation details and exposing only what is necessary.
- **Inheritance**: Creating new classes based on existing classes, reusing and extending their properties and methods.
- **Polymorphism**: Allowing objects of different classes to be treated as objects of a common superclass.

JavaScript is an object-based language that allows developers to implement OOP concepts using classes and objects.

---

## 2. Understanding Objects in JavaScript

In JavaScript, objects are collections of properties and methods. Each object is a standalone entity with key-value pairs.

### Syntax

```javascript
const objectName = {
  property1: value1,
  property2: value2,
  method1: function() {
    // Method body
  }
};
```

### Example

```javascript
const customer = {
  name: "John Doe",
  balance: 1000,
  deposit(amount) {
    this.balance += amount;
    console.log(`Deposited $${amount}. New balance: $${this.balance}`);
  }
};

customer.deposit(500); // Output: Deposited $500. New balance: $1500
```

**Explanation:**

- The `customer` object has two properties (`name` and `balance`) and one method (`deposit`).
- Methods inside objects can use `this` to refer to the object itself.

---

## 3. What are Classes?

In JavaScript, a **class** is a blueprint for creating objects. A class defines the properties and methods that its instances (objects) will have. Classes help group related functionalities and data together, promoting better code organization.

### Defining a Class

```javascript
class ClassName {
  constructor() {
    // Initialization logic
  }
}
```

### Example

```javascript
class Product {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }
}

const laptop = new Product("Laptop", 1200);
console.log(laptop.name);  // Output: Laptop
console.log(laptop.price); // Output: 1200
```

**Explanation:**

- The `Product` class defines a template for creating product objects with `name` and `price` properties.
- The `constructor` method initializes the object when a new instance is created.

---

## 4. The Constructor Method

The `constructor` method is a special function that is called automatically when a new object is instantiated. It is used to initialize object properties.

### Example

```javascript
class Employee {
  constructor(name, position, salary) {
    this.name = name;
    this.position = position;
    this.salary = salary;
  }
}

const employee1 = new Employee("Alice", "Developer", 70000);
console.log(employee1.name);      // Output: Alice
console.log(employee1.position);  // Output: Developer
console.log(employee1.salary);    // Output: 70000
```

**Explanation:**

- The `Employee` class initializes an object with `name`, `position`, and `salary` properties through the `constructor`.
- You can create multiple instances of the class with different values.

---

## 5. Methods in Classes

Methods are functions defined inside a class that perform operations on object data. They help encapsulate behavior within the class.

### Example

```javascript
class Product {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  displayInfo() {
    console.log(`Product: ${this.name}, Price: $${this.price}`);
  }
}

const phone = new Product("Phone", 800);
phone.displayInfo(); // Output: Product: Phone, Price: $800
```

**Explanation:**

- The `displayInfo` method is a function that prints the product's details.
- Methods in classes are defined just like regular functions but operate on object properties using `this`.

---

## 6. Inheritance

**Inheritance** allows a class (child class) to inherit properties and methods from another class (parent class). It helps reuse code and extend existing functionality.

### Syntax

```javascript
class ChildClass extends ParentClass {
  constructor() {
    super(); // Calls the parent class's constructor
  }
}
```

### Example

```javascript
class Employee {
  constructor(name, salary) {
    this.name = name;
    this.salary = salary;
  }

  work() {
    console.log(`${this.name} is working.`);
  }
}

class Manager extends Employee {
  constructor(name, salary, department) {
    super(name, salary); // Call the parent constructor
    this.department = department;
  }

  manage() {
    console.log(`${this.name} is managing the ${this.department} department.`);
  }
}

const manager = new Manager("Bob", 90000, "Sales");
manager.work();    // Output: Bob is working.
manager.manage();  // Output: Bob is managing the Sales department.
```

**Explanation:**

- The `Manager` class inherits from the `Employee` class, reusing the `name` and `salary` properties and the `work` method.
- `super()` is used to call the parent class's constructor.

---

## 7. Encapsulation

Encapsulation restricts access to certain object properties and methods, providing controlled access through getter and setter methods. In JavaScript, private fields are denoted by a `#` symbol.

### Example

```javascript
class BankAccount {
  #balance = 0; // Private field

  deposit(amount) {
    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount();
account.deposit(1000);
console.log(account.getBalance()); // Output: 1000
// console.log(account.#balance);   // Error: Private field cannot be accessed
```

**Explanation:**

- The `#balance` field is private and can only be accessed within the class.
- `deposit` and `getBalance` are public methods that provide controlled access to the private field.

---

## 8. Polymorphism

Polymorphism allows objects of different classes to be treated as instances of the same class through inheritance. It enables a method to behave differently based on the object calling it.

### Example

```javascript
class Employee {
  constructor(name) {
    this.name = name;
  }

  work() {
    console.log(`${this.name} is working.`);
  }
}

class Developer extends Employee {
  work() {
    console.log(`${this.name} is writing code.`);
  }
}

class Designer extends Employee {
  work() {
    console.log(`${this.name} is designing interfaces.`);
  }
}

const employees = [new Developer("Alice"), new Designer("Bob")];

employees.forEach(employee => employee.work());
```

**Output:**

```
Alice is writing code.
Bob is designing interfaces.
```

**Explanation:**

- Both `Developer` and `Designer` classes inherit from `Employee` but override the `work` method.
- Polymorphism allows each object to execute its own version of the `work` method.

---

## 9. Business Example: Managing Customer Orders

Let’s implement a real-world business scenario using OOP principles. We'll create a system for managing customer orders in a store.

### Example

```javascript
class Customer {
  constructor(name, balance) {
    this.name = name;
    this.balance = balance;
  }

  makePurchase(amount) {
    if (this.balance >= amount) {
      this.balance -= amount;
      console.log(`${this.name} made a purchase of $${amount}. Remaining balance: $${this.balance}`);
    } else {
      console.log(`Insufficient balance for ${this.name}.`);
    }
  }

  addFunds(amount) {
    this.balance += amount;
    console.log(`${this.name} added $${amount}. New balance: $${this.balance}`);
  }
}

class VIPCustomer extends Customer {
  constructor(name, balance, discountRate) {
    super(name, balance);
    this.discountRate = discountRate;
  }

  makePurchase(amount) {
    const discountedAmount = amount * (1 - this.discountRate);
    super.makePurchase(discountedAmount);
  }
}

const regularCustomer = new Customer("John", 500);
regularCustomer.makePurchase(200); // Output: John made a purchase of $200. Remaining balance: $300

const vipCustomer = new VIPCustomer("Jane", 1000, 0.1);
vipCustomer.makePurchase(500); // Output: Jane made a

 purchase of $450. Remaining balance: $550
```

**Explanation:**

- The `Customer` class handles basic customer operations like making purchases and adding funds.
- The `VIPCustomer` class extends `Customer`, offering a discount when purchases are made.

---

## 10. Conclusion

Object-Oriented Programming (OOP) in JavaScript provides a structured and efficient way to build reusable, scalable, and maintainable applications. By leveraging classes, inheritance, encapsulation, and polymorphism, developers can model real-world business entities and behaviors in a way that makes the code easier to understand and extend.

### Key Takeaways:
- **Objects** bundle data and methods together for easier management.
- **Classes** provide a template for creating multiple objects with shared properties and behaviors.
- **Inheritance** enables code reuse by allowing child classes to inherit from parent classes.
- **Encapsulation** protects object data and allows for controlled access.
- **Polymorphism** allows different classes to share the same method names with different implementations.

By mastering OOP principles in JavaScript, you’ll be able to build complex, scalable, and efficient applications that mimic real-world business processes.

**Happy coding!**
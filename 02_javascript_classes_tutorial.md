# Tutorial: Understanding JavaScript Classes

JavaScript classes provide a more structured and organized way to define objects, methods, and properties. Classes allow developers to use Object-Oriented Programming (OOP) principles, such as inheritance, encapsulation, and abstraction, to manage complex systems. This tutorial will guide you through the basics of JavaScript classes and how they are used in real-world business applications.

## Table of Contents

1. **What Are Classes in JavaScript?**
2. **Defining a Class**
3. **Class Constructor**
4. **Class Methods**
5. **Creating Instances of a Class**
6. **Class Inheritance**
7. **Getters and Setters**
8. **Static Methods**
9. **Private Class Fields and Methods**
10. **Business Example: Managing Employees**
11. **Conclusion**

---

## 1. What Are Classes in JavaScript?

A **class** is a blueprint for creating objects. Objects created from a class share the same properties and methods, defined by the class. JavaScript introduced classes in ES6, making it easier to implement OOP patterns that are common in other languages like Java and Python.

Classes allow you to:
- Organize code and group related data and functions together.
- Create multiple instances of objects that share the same behavior.
- Use inheritance to build upon existing classes without rewriting code.

---

## 2. Defining a Class

To define a class in JavaScript, use the `class` keyword followed by the class name.

### Syntax

```javascript
class ClassName {
  // Methods and properties
}
```

### Example

```javascript
class Product {
  // Class body (methods, constructor, etc.)
}
```

In this example, we defined a class called `Product` but haven't added any properties or methods yet.

---

## 3. Class Constructor

The **constructor** is a special method in a class that is automatically called when a new object is created (instantiated) from that class. It is typically used to initialize the object's properties.

### Syntax

```javascript
class Product {
  constructor(name, price) {
    this.name = name; // Initializing properties
    this.price = price;
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
console.log(laptop.name); // Output: Laptop
console.log(laptop.price); // Output: 1200
```

**Explanation:**
- The constructor method is used to initialize the properties (`name` and `price`) when creating a new `Product` object.
- `this.name` refers to the current object's property `name`.

---

## 4. Class Methods

Classes can also have methods, which are functions that operate on the object's properties or perform specific actions.

### Syntax

```javascript
class ClassName {
  methodName() {
    // Method body
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

  displayInfo() {
    console.log(`Product: ${this.name}, Price: $${this.price}`);
  }
}

const phone = new Product("Phone", 800);
phone.displayInfo(); // Output: Product: Phone, Price: $800
```

**Explanation:**
- The `displayInfo` method is defined inside the `Product` class. It uses `this` to access the object's properties and print information about the product.

---

## 5. Creating Instances of a Class

You can create multiple instances (objects) of a class using the `new` keyword.

### Example

```javascript
const tablet = new Product("Tablet", 500);
const smartwatch = new Product("Smartwatch", 200);

tablet.displayInfo();    // Output: Product: Tablet, Price: $500
smartwatch.displayInfo(); // Output: Product: Smartwatch, Price: $200
```

**Explanation:**
- Both `tablet` and `smartwatch` are instances of the `Product` class, each with its own values for the `name` and `price` properties.

---

## 6. Class Inheritance

JavaScript classes support **inheritance**, where a new class (child class) can inherit properties and methods from an existing class (parent class). This promotes code reusability.

### Syntax

```javascript
class ChildClass extends ParentClass {
  // Additional properties and methods
}
```

### Example

```javascript
class Employee {
  constructor(name, position) {
    this.name = name;
    this.position = position;
  }

  work() {
    console.log(`${this.name} is working as a ${this.position}`);
  }
}

class Manager extends Employee {
  constructor(name, department) {
    super(name, "Manager"); // Call the parent class constructor
    this.department = department;
  }

  assignTask(task) {
    console.log(`${this.name} is assigning task: ${task}`);
  }
}

const manager = new Manager("Alice", "Sales");
manager.work();           // Output: Alice is working as a Manager
manager.assignTask("Prepare sales report"); // Output: Alice is assigning task: Prepare sales report
```

**Explanation:**
- The `Manager` class inherits from the `Employee` class using `extends`.
- The `super()` function is used to call the constructor of the parent class (`Employee`) and initialize inherited properties.

---

## 7. Getters and Setters

Getters and setters allow you to define methods that behave like properties, providing controlled access to an object's properties.

### Syntax

```javascript
class ClassName {
  get propertyName() {
    // Code to return a value
  }

  set propertyName(value) {
    // Code to set a value
  }
}
```

### Example

```javascript
class Product {
  constructor(name, price) {
    this.name = name;
    this._price = price; // Use _ to signify private property
  }

  get price() {
    return `$${this._price}`;
  }

  set price(value) {
    if (value < 0) {
      console.log("Price cannot be negative.");
    } else {
      this._price = value;
    }
  }
}

const laptop = new Product("Laptop", 1000);
console.log(laptop.price);  // Output: $1000

laptop.price = -500;        // Output: Price cannot be negative.
laptop.price = 1200;
console.log(laptop.price);  // Output: $1200
```

**Explanation:**
- The `get price` method allows you to retrieve the price with custom formatting.
- The `set price` method enforces validation (the price cannot be negative).

---

## 8. Static Methods

Static methods belong to the class itself and not to instances of the class. They are typically used for utility functions related to the class.

### Syntax

```javascript
class ClassName {
  static methodName() {
    // Code for static method
  }
}
```

### Example

```javascript
class Utility {
  static calculateDiscount(price, discount) {
    return price - price * discount;
  }
}

console.log(Utility.calculateDiscount(100, 0.2)); // Output: 80
```

**Explanation:**
- The `calculateDiscount` method is static, meaning it is called on the class itself (`Utility.calculateDiscount`), not on an instance of the class.

---

## 9. Private Class Fields and Methods

JavaScript allows for **private** fields and methods, meaning they can only be accessed within the class. Private fields start with `#`.

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
account.deposit(100);
console.log(account.getBalance()); // Output: 100
// console.log(account.#balance); // Error: Private field cannot be accessed
```

**Explanation:**
- The `#balance` field is private and cannot be accessed directly outside the class. The `deposit` and `getBalance` methods provide controlled access to it.

---

## 10. Business Example: Managing Employees

Let’s build a more complete example using classes to manage employee records in a business.

```javascript
class Employee {
  constructor(name, position, salary) {
    this.name = name;
    this.position = position;
    this.salary = salary;
  }

  work() {
    console.log(`${this.name} is working as a ${this.position}`);
  }

  get annualSalary() {
    return this.salary * 12;
  }
}

class Manager extends Employee {
  constructor(name, department, salary) {
    super(name, "Manager", salary);
    this.department = department;
  }

  assignTask(task) {
    console.log(`${this.name} is assigning task: ${task}`);
  }
}

class Developer extends Employee {
  constructor(name, salary, programmingLanguage) {
    super(name, "Developer", salary);
    this.programmingLanguage = programmingLanguage;
  }

  code() {
    console.log(`${this.name} is coding in ${this.programmingLanguage}`);
  }
}

// Creating instances
const manager = new Manager("John", "HR", 6000);
const developer = new Developer("Alice", 5000, "JavaScript");

manager.work(); // Output: John is working as a Manager
manager.assignTask("Update employee records");

developer.work(); // Output: Alice is working as a Developer
developer.code(); // Output: Alice is coding in JavaScript

console.log(manager.annualSalary);  // Output: 

72000
console.log(developer.annualSalary); // Output: 60000
```

**Explanation:**
- The `Employee` class serves as the base class.
- The `Manager` and `Developer` classes extend `Employee` and add additional properties and methods specific to their roles.
- `annualSalary` is a getter that computes the annual salary based on the monthly salary.

---

## 11. Conclusion

JavaScript classes are a powerful way to structure and manage code in an object-oriented manner. They allow for cleaner, more organized code and offer features like inheritance, encapsulation, and static methods, making them ideal for larger, more complex applications. By understanding how to use classes, constructors, methods, inheritance, and private fields, you'll be able to build more efficient and maintainable JavaScript applications.

**Happy coding!**
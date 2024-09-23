## Introduction

- Organizing JavaScript code can be overwhelming
- JavaScript is forgiving, allowing for flexible code patterns
- Other languages often force specific patterns and structures
- JavaScript allows freedom, but with complexity, organization becomes key


## Why Organization Matters

- Flexibility in JavaScript is great for small projects
- As complexity increases, unorganized code becomes hard to maintain
- Learning design patterns helps manage larger, more complex projects



## Common JavaScript Design Patterns

1. **Plain Old JavaScript Objects (POJOs)**
2. **Object Constructors**
3. **Factory Functions**
4. **The Module Pattern**
5. **Classes**
6. **ES6 Modules**


## Benefits of Learning Patterns

- Understanding patterns helps improve:
  - Code maintainability
  - Code readability
  - Collaboration on larger projects
  
  Here's the updated markdown slide deck with all the examples modified to reflect business scenarios:

# Objects and Object Constructors in Business Applications



## Refresher: Object Basics

- Multiple ways to define objects in JavaScript
- Object literal syntax is most common:

```javascript
const employee = {
  name: 'John Doe',
  position: 'Manager',
  salary: 75000,
  displayInfo: function() {
    console.log(`${this.name} is a ${this.position} making $${this.salary}`);
  }
};
```



## Accessing Object Properties

- **Dot notation**: `employee.name`
- **Bracket notation**: `employee["position"]`
  
  - Dot notation is preferred but doesn't work with spaces or variables:

```javascript
const property = 'salary';
employee[property]; // Works
```



## Writing Object Constructors

- Use a constructor function to create multiple objects of the same type:

```javascript
function Employee(name, position, salary) {
  this.name = name;
  this.position = position;
  this.salary = salary;
}
```

- Instantiate with the `new` keyword:

```javascript
const employee1 = new Employee('Jane Smith', 'Developer', 85000);
```



## Adding Methods to Constructors

- Functions can be added to the constructor:

```javascript
function Employee(name, position, salary) {
  this.name = name;
  this.position = position;
  this.salary = salary;
  this.displayInfo = function() {
    return `${this.name} is a ${this.position} making $${this.salary}`;
  };
}
```



## Example: Organizing Business Data with Objects

- Example from an inventory management system:

```javascript
const productA = { name: "Laptop", price: 1500, stock: 20 };
const productB = { name: "Monitor", price: 300, stock: 50 };
```

- Easy to pass objects to functions:

```javascript
function printStock(product) {
  console.log(`${product.name} has ${product.stock} items left in stock`);
}
```



## The Importance of Prototypes

- All JavaScript objects have a **prototype**
- Prototypes enable inheritance:

```javascript
Employee.prototype.sayHello = function() {
   console.log(`Hello, I am ${this.name}, a ${this.position} at the company!`);
};
```

- All objects created by a constructor share its prototype's methods and properties



## Understanding Prototypal Inheritance

- Objects inherit from their constructor's prototype:

```javascript
Object.getPrototypeOf(employee1) === Employee.prototype;
```

- Methods on the prototype are shared by all instances:

```javascript
Employee.prototype.getSalary = function() {
   return `Salary: $${this.salary}`;
};
employee1.getSalary();
```



## Prototype Chain

- Inheritance works through the **prototype chain**:

```javascript
Object.getPrototypeOf(Employee.prototype) === Object.prototype;
```

- Properties and methods traverse up the chain



## Object.setPrototypeOf

- You can change the prototype of an object:

```javascript
Object.setPrototypeOf(Employee.prototype, Person.prototype);
```

- Employees can now access both `Person` and `Employee` methods



## Prototypal Inheritance in Action

- Example of setting up inheritance between constructors:

```javascript
function Person(name) {
  this.name = name;
}
function Employee(name, position, salary) {
  this.name = name;
  this.position = position;
  this.salary = salary;
}
Object.setPrototypeOf(Employee.prototype, Person.prototype);
```



## Avoiding Common Pitfalls

- Don't directly assign prototypes:

```javascript
Employee.prototype = Person.prototype; // Avoid this
```

- Use `Object.setPrototypeOf` to avoid conflicts in the future



## Understanding the `this` Keyword

- The `this` keyword changes context based on how a function is called
- Important to understand in object constructors and methods
 
## Understanding Scope

- **Global scope**: Variables available throughout the entire program.
- **Local scope**: Variables confined to specific functions or blocks.
  
Example: Managing a global company budget and department-specific budgets.

```javascript
let companyBudget = 1000000;

function allocateBudget(departmentBudget) {
  var remainingBudget = 200000;
  
  if (departmentBudget < remainingBudget) {
    const approvedBudget = departmentBudget;
    console.log(approvedBudget);
  }

  console.log(approvedBudget); // Error: approvedBudget is block scoped
}

allocateBudget(150000);
console.log(remainingBudget); // Error: remainingBudget is function scoped
```



## Introduction to Closures

- Closures allow business functions to maintain access to specific data across multiple executions.

Example: Creating an employee payroll function that retains base salary.

```javascript
function createPayroll(baseSalary) {
  const salary = baseSalary;
  return function calculateFinalPay(bonus) {
    return salary + bonus;
  };
}

const employeePayroll = createPayroll(60000);
console.log(employeePayroll(5000)); // 65000
```



## Factory Functions vs Constructors

- Factory functions address some limitations of constructors, especially in managing business entities.

Example: Managing employee creation using factory functions.

```javascript
// Constructor for employees
function Employee(name) {
  this.name = name;
  this.department = "Sales";
}

// Factory function for employees
function createEmployee(name) {
  const department = "Sales";
  return { name, department };
}
```



## Private Variables with Factory Functions

- Factory functions allow you to protect sensitive business data, such as employee performance metrics, using private variables.

Example: Employee performance evaluation system with private variables.

```javascript
function createEmployee(name) {
  let performanceRating = 0;

  function increaseRating() {
    performanceRating++;
  }

  function getRating() {
    return performanceRating;
  }

  return { name, increaseRating, getRating };
}

const employee = createEmployee("Alice");
employee.increaseRating();
console.log(employee.getRating()); // 1
```



## Factory Functions and Inheritance

- Factory functions can be extended to model different business roles, such as managers or employees.

Example: Extending employee factory to create managers with additional responsibilities.

```javascript
function createEmployee(name) {
  const department = "Sales";
  return { name, department };
}

function createManager(name, department) {
  const employee = createEmployee(name);
  return { ...employee, department };
}

const manager = createManager("John", "Marketing");
console.log(manager.name, manager.department); // John, Marketing
```



## The Module Pattern

- Use the module pattern to organize and encapsulate business logic, such as financial calculations, into isolated units.

Example: Encapsulating financial calculations for company budget management.

```javascript
const budgetCalculator = (function () {
  const addFunds = (currentBudget, newFunds) => currentBudget + newFunds;
  const allocateFunds = (currentBudget, allocation) => currentBudget - allocation;
  return { addFunds, allocateFunds };
})();

console.log(budgetCalculator.addFunds(500000, 100000)); // 600000
console.log(budgetCalculator.allocateFunds(600000, 150000)); // 450000
```



## Benefits of Encapsulation and Namespacing

- **Encapsulation**: Hides internal logic, such as sensitive financial calculations, and only exposes necessary methods.
- **Namespacing**: Prevents conflicts by grouping related business logic, like payroll calculations, under a single object.

Example: Encapsulating payroll processing logic into a module.

```javascript
const payrollModule = (function () {
  const calculateSalary = (baseSalary, bonus) => baseSalary + bonus;
  const calculateDeductions = (salary, deductions) => salary - deductions;
  return { calculateSalary, calculateDeductions };
})();

console.log(payrollModule.calculateSalary(70000, 5000)); // 75000
console.log(payrollModule.calculateDeductions(75000, 3000)); // 72000
```



## Summary

- **Factory functions**: Offer a flexible way to create business objects like employees or managers.
- **Private variables**: Protect sensitive data, such as employee performance ratings.
- **Module pattern**: Helps encapsulate and organize business logic, preventing conflicts in large applications.

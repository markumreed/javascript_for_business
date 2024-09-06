# JavaScript Basics Coding Challenge

## Challenge Overview

In this coding challenge, you will practice your JavaScript skills by working with variables, data types, assignment operators, comparison operators, and logical operators in a series of business-related scenarios. This challenge will test your understanding of basic JavaScript syntax and help you become comfortable with using different operators and data types.

### **Important Note**: 
All tasks should be saved in the **same JavaScript file** named `cc_1.js`. You must link this JavaScript file to an `index.html` file and **submit each task to GitHub with a unique commit message** before moving on to the next one. This ensures proper version control and documentation of your progress.

## Challenge Instructions

### Preparation

1. **Create an `index.html` file** in your project directory.
2. Inside the `index.html` file, create the basic HTML structure and include a script tag to link to your JavaScript file `cc_1.js`.
3. **Initialize a GitHub repository** if you haven't already and commit your initial files with the message: "Initial commit - JavaScript Basics Challenge Setup".

### `index.html` Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript Basics Challenge</title>
</head>
<body>
    <h1>JavaScript Basics Coding Challenge</h1>
    <script src="cc_1.js"></script>
</body>
</html>
```

### Task 1: Variables and Data Types

#### Scenario: Employee Information

You are working in a company's HR department and need to store and manage basic employee information.

1. **Declare variables** using `var`, `let`, and `const` to store employee details.
2. **Assign** values to these variables and output their types using `console.log()` and `typeof`.

#### Requirements:

- Declare a variable `employeeName` using `let` and assign it the employee's name as a string.
- Declare a variable `employeeID` using `const` and assign it the employee's ID as a number.
- Declare a variable `isActive` using `var` and assign it a boolean value `true` to indicate the employee is currently active.
- Log each variable's value and its type to the console.

#### Example Code (`cc_1.js`):

```javascript
// Task 1: Variables and Data Types
let employeeName = "Alice Johnson";
const employeeID = 12345;
var isActive = true;

console.log(employeeName); // "Alice Johnson"
console.log(typeof employeeName); // "string"

console.log(employeeID); // 12345
console.log(typeof employeeID); // "number"

console.log(isActive); // true
console.log(typeof isActive); // "boolean"
```

#### Submission:

- **Commit your changes** to GitHub with the message: "Task 1 - Employee Information".
- **Push** the commit to your GitHub repository.
- **Submit the GitHub repository link** before proceeding to the next task.

### Task 2: Compound Data Types

#### Scenario: Product Inventory Management

You are responsible for managing a list of products in a store's inventory.

1. **Create an array** to store a list of available products.
2. **Create an object** to represent a product with properties like `name`, `price`, and `inStock`.

#### Requirements:

- Declare an array `products` using `let` and initialize it with at least three product names.
- Declare an object `productDetails` using `const` with properties `name`, `price`, and `inStock`.
- Log the array and the object to the console.

#### Example Code (`cc_1.js` continued):

```javascript
// Task 2: Compound Data Types
let products = ["Laptop", "Smartphone", "Tablet"];
const productDetails = {
  name: "Laptop",
  price: 1200,
  inStock: true
};

console.log(products); // ["Laptop", "Smartphone", "Tablet"]
console.log(productDetails); // { name: "Laptop", price: 1200, inStock: true }
```

#### Submission:

- **Commit your changes** to GitHub with the message: "Task 2 - Product Inventory Management".
- **Push** the commit to your GitHub repository.
- **Submit the GitHub repository link** before proceeding to the next task.

### Task 3: Assignment Operators

#### Scenario: Financial Calculations

You are working in the finance department and need to perform various calculations on an account balance.

1. Use **assignment operators** to perform calculations on a customer's account balance.
2. Update and log the balance after each operation.

#### Requirements:

- Declare a variable `accountBalance` using `let` and initialize it with a number representing the initial balance.
- Use `+=`, `-=`, `*=`, `/=`, and `%=` to update the value of `accountBalance` for different transactions.
- Log the updated value of `accountBalance` after each operation.

#### Example Code (`cc_1.js` continued):

```javascript
// Task 3: Assignment Operators
let accountBalance = 1000;

accountBalance += 200; // Deposit
console.log(accountBalance); // 1200

accountBalance -= 150; // Withdrawal
console.log(accountBalance); // 1050

accountBalance *= 1.05; // Interest
console.log(accountBalance); // 1102.5

accountBalance /= 2; // Halving due to split
console.log(accountBalance); // 551.25

accountBalance %= 100; // Modulo operation
console.log(accountBalance); // 51.25
```

#### Submission:

- **Commit your changes** to GitHub with the message: "Task 3 - Financial Calculations".
- **Push** the commit to your GitHub repository.
- **Submit the GitHub repository link** before proceeding to the next task.

### Task 4: Comparison Operators

#### Scenario: Employee Performance Evaluation

You are evaluating employees based on their performance scores.

1. Use **comparison operators** to compare employee scores.
2. Log the results of these comparisons.

#### Requirements:

- Declare variables `employeeScore1` and `employeeScore2` with numerical values representing two employees' scores.
- Compare `employeeScore1` and `employeeScore2` using `>`, `<`, `>=`, `<=`, `===`, and `!==`.
- Log the results of each comparison to the console.

#### Example Code (`cc_1.js` continued):

```javascript
// Task 4: Comparison Operators
let employeeScore1 = 85;
let employeeScore2 = 90;

console.log(employeeScore1 > employeeScore2); // false
console.log(employeeScore1 < employeeScore2); // true
console.log(employeeScore1 >= 85); // true
console.log(employeeScore2 <= 90); // true
console.log(employeeScore1 === 85); // true
console.log(employeeScore1 !== employeeScore2); // true
```

#### Submission:

- **Commit your changes** to GitHub with the message: "Task 4 - Employee Performance Evaluation".
- **Push** the commit to your GitHub repository.
- **Submit the GitHub repository link** before proceeding to the next task.

### Task 5: Logical Operators

#### Scenario: Access Control System

You are developing an access control system to determine if a user has access to certain sections of a building.

1. Use **logical operators** (`&&`, `||`, `!`) to evaluate access permissions.
2. Log the results of these logical operations.

#### Requirements:

- Declare variables `hasKeyCard` and `hasPermission` with boolean values.
- Combine these variables using `&&` and `||` to determine if the user can access different areas.
- Use the `!` operator to reverse a boolean value and log the results.

#### Example Code (`cc_1.js` continued):

```javascript
// Task 5: Logical Operators
let hasKeyCard = true;
let hasPermission = false;

console.log(hasKeyCard && hasPermission); // false
console.log(hasKeyCard || hasPermission); // true
console.log(!hasKeyCard); // false
```

#### Submission:

- **Commit your changes** to GitHub with the message: "Task 5 - Access Control System".
- **Push** the commit to your GitHub repository.
- **Submit the GitHub repository link** as your final submission.

## Final Submission Guidelines

1. Ensure all tasks are saved in the **same JavaScript file**: `cc_1.js`.
2. Link the JavaScript file to the `index.html` file as shown in the template.
3. Push your changes to your GitHub repository after completing each task with a unique commit message.
4. Submit the link to your GitHub repository after each task.

**Good luck with the challenge!** Remember to follow the instructions carefully and ask for help if needed before our next session. 
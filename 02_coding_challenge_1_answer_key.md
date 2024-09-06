# JavaScript Basics Coding Challenge - Answer Key

This answer key provides solutions for each task in the JavaScript Basics Coding Challenge. Your answers might not be exactly the same, as the specific values or data you use may vary. The primary goal is to ensure you understand the fundamental concepts and can apply them correctly. 

### **Important Note**: 
When reviewing your peers' submissions, please use the provided rubric to assess each task thoroughly. Ensure that your feedback is constructive and based on the criteria outlined in the rubric.

## Task 1: Variables and Data Types

### Scenario: Employee Information

You are working in a company's HR department and need to store and manage basic employee information.

#### Requirements:

- Declare a variable `employeeName` using `let` and assign it the employee's name as a string.
- Declare a variable `employeeID` using `const` and assign it the employee's ID as a number.
- Declare a variable `isActive` using `var` and assign it a boolean value `true` to indicate the employee is currently active.
- Log each variable's value and its type to the console.

#### Answer:

```javascript
// Task 1: Variables and Data Types
let employeeName = "Alice Johnson";
const employeeID = 12345;
var isActive = true;

console.log(employeeName); // Output: "Alice Johnson"
console.log(typeof employeeName); // Output: "string"

console.log(employeeID); // Output: 12345
console.log(typeof employeeID); // Output: "number"

console.log(isActive); // Output: true
console.log(typeof isActive); // Output: "boolean"
```

### Explanation:

- **`let`** is used to declare a variable that can be reassigned, suitable for `employeeName` since names can potentially change.
- **`const`** is used for `employeeID` since an ID should be constant and not change once assigned.
- **`var`** is used for `isActive`, although it's generally advisable to use `let` or `const` in modern JavaScript for better scope management. Here, it illustrates an older style.
- `typeof` is a JavaScript operator that returns the data type of the variable.

## Task 2: Compound Data Types

### Scenario: Product Inventory Management

You are responsible for managing a list of products in a store's inventory.

#### Requirements:

- Declare an array `products` using `let` and initialize it with at least three product names.
- Declare an object `productDetails` using `const` with properties `name`, `price`, and `inStock`.
- Log the array and the object to the console.

#### Answer:

```javascript
// Task 2: Compound Data Types
let products = ["Laptop", "Smartphone", "Tablet"];
const productDetails = {
  name: "Laptop",
  price: 1200,
  inStock: true
};

console.log(products); // Output: ["Laptop", "Smartphone", "Tablet"]
console.log(productDetails); // Output: { name: "Laptop", price: 1200, inStock: true }
```

### Explanation:

- **Arrays** are used to store multiple items of the same type. Here, `products` holds a list of product names.
- **Objects** are used to store related data and functions together. `productDetails` contains properties describing a product.
- Logging these to the console helps visualize the data structure and its contents.

## Task 3: Assignment Operators

### Scenario: Financial Calculations

You are working in the finance department and need to perform various calculations on an account balance.

#### Requirements:

- Declare a variable `accountBalance` using `let` and initialize it with a number representing the initial balance.
- Use `+=`, `-=`, `*=`, `/=`, and `%=` to update the value of `accountBalance` for different transactions.
- Log the updated value of `accountBalance` after each operation.

#### Answer:

```javascript
// Task 3: Assignment Operators
let accountBalance = 1000;

accountBalance += 200; // Deposit
console.log(accountBalance); // Output: 1200

accountBalance -= 150; // Withdrawal
console.log(accountBalance); // Output: 1050

accountBalance *= 1.05; // Interest
console.log(accountBalance); // Output: 1102.5

accountBalance /= 2; // Halving due to split
console.log(accountBalance); // Output: 551.25

accountBalance %= 100; // Modulo operation
console.log(accountBalance); // Output: 51.25
```

### Explanation:

- Assignment operators (`+=`, `-=`, `*=`, `/=`, `%=`) are used to perform arithmetic operations and update the value of a variable in a single step.
- Each operation modifies `accountBalance` to reflect transactions like deposits, withdrawals, interest calculations, etc.
- The use of assignment operators simplifies the syntax and makes the code more readable.

## Task 4: Comparison Operators

### Scenario: Employee Performance Evaluation

You are evaluating employees based on their performance scores.

#### Requirements:

- Declare variables `employeeScore1` and `employeeScore2` with numerical values representing two employees' scores.
- Compare `employeeScore1` and `employeeScore2` using `>`, `<`, `>=`, `<=`, `===`, and `!==`.
- Log the results of each comparison to the console.

#### Answer:

```javascript
// Task 4: Comparison Operators
let employeeScore1 = 85;
let employeeScore2 = 90;

console.log(employeeScore1 > employeeScore2); // Output: false
console.log(employeeScore1 < employeeScore2); // Output: true
console.log(employeeScore1 >= 85); // Output: true
console.log(employeeScore2 <= 90); // Output: true
console.log(employeeScore1 === 85); // Output: true
console.log(employeeScore1 !== employeeScore2); // Output: true
```

### Explanation:

- **Comparison operators** (`>`, `<`, `>=`, `<=`, `===`, `!==`) are used to compare two values.
- These comparisons return boolean values (`true` or `false`) based on the relation between `employeeScore1` and `employeeScore2`.
- This is useful in scenarios where decisions are made based on comparisons, like performance evaluations.

## Task 5: Logical Operators

### Scenario: Access Control System

You are developing an access control system to determine if a user has access to certain sections of a building.

#### Requirements:

- Declare variables `hasKeyCard` and `hasPermission` with boolean values.
- Combine these variables using `&&` and `||` to determine if the user can access different areas.
- Use the `!` operator to reverse a boolean value and log the results.

#### Answer:

```javascript
// Task 5: Logical Operators
let hasKeyCard = true;
let hasPermission = false;

console.log(hasKeyCard && hasPermission); // Output: false
console.log(hasKeyCard || hasPermission); // Output: true
console.log(!hasKeyCard); // Output: false
```

### Explanation:

- **Logical operators** (`&&`, `||`, `!`) are used to combine or negate boolean expressions.
- `&&` (AND) returns `true` only if both operands are true.
- `||` (OR) returns `true` if at least one operand is true.
- `!` (NOT) reverses the boolean value.
- This logic is fundamental in control flow and decision-making processes, such as access control systems.

### **Note:** When conducting peer reviews, make sure to use the rubric provided to evaluate each submission based on correctness, code clarity, and adherence to JavaScript best practices. Your constructive feedback will help your peers improve their coding skills!
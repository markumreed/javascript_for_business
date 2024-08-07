# JavaScript Control Structures

#### Introduction

Control structures are fundamental in programming as they allow you to control the flow of your code. In this tutorial, we will cover conditionals and loops in JavaScript using business case examples. By mastering these concepts, you can make your programs more dynamic and responsive to different scenarios.

#### Conditionals

Conditionals allow you to execute different code based on different conditions. The primary conditional statements in JavaScript are `if`, `else if`, `else`, and `switch`.

##### 1. `if` Statement

The `if` statement executes a block of code if a specified condition is true.

**Example**:
Suppose you need to check if sales for the day have reached a certain target.

```javascript
let dailySales = 1200;
let salesTarget = 1000;

if (dailySales >= salesTarget) {
    console.log("Sales target achieved");
}
```

**Explanation**:
In this example, we use an `if` statement to check if `dailySales` is greater than or equal to `salesTarget`. If the condition is true, the code inside the `if` block is executed, printing "Sales target achieved". This demonstrates how you can use `if` statements to perform actions based on specific conditions.

##### 2. `if-else` Statement

The `if-else` statement executes one block of code if a condition is true, and another block of code if the condition is false.

**Example**:
Consider a scenario where you need to provide feedback on whether a sales target has been met.

```javascript
let dailySales = 800;
let salesTarget = 1000;

if (dailySales >= salesTarget) {
    console.log("Sales target achieved");
} else {
    console.log("Sales target not achieved");
}
```

**Explanation**:
In this example, if `dailySales` is greater than or equal to `salesTarget`, the code inside the `if` block executes, printing "Sales target achieved". Otherwise, the code inside the `else` block executes, printing "Sales target not achieved". This allows for more complex decision-making in your code.

##### 3. `else if` Statement

The `else if` statement allows you to specify a new condition if the first condition is false.

**Example**:
Imagine you want to categorize sales performance into different levels.

```javascript
let dailySales = 1500;

if (dailySales >= 2000) {
    console.log("Excellent sales");
} else if (dailySales >= 1000) {
    console.log("Good sales");
} else {
    console.log("Needs improvement");
}
```

**Explanation**:
In this example, we use `else if` to add additional conditions. If `dailySales` is greater than or equal to `2000`, it prints "Excellent sales". If `dailySales` is between `1000` and `1999`, it prints "Good sales". If `dailySales` is less than `1000`, it prints "Needs improvement". This allows for more granular control over the flow of your code based on multiple conditions.

##### 4. `switch` Statement

The `switch` statement executes different blocks of code based on different conditions. It is an alternative to using multiple `if-else` statements.

**Example**:
Suppose you need to perform different actions based on the department in a company.

```javascript
let department = "HR";

switch (department) {
    case "Sales":
        console.log("This is the Sales department");
        break;
    case "HR":
        console.log("This is the HR department");
        break;
    case "IT":
        console.log("This is the IT department");
        break;
    default:
        console.log("Unknown department");
}
```

**Explanation**:
In this example, we use a `switch` statement to handle different values of the `department` variable. Depending on the value of `department`, it executes the corresponding block of code and breaks out of the switch. If `department` does not match any of the specified cases, the `default` block executes, printing "Unknown department". This approach simplifies handling multiple possible values for a variable.

#### Loops

Loops allow you to execute a block of code multiple times. The primary loop statements in JavaScript are `for`, `while`, and `do-while`.

##### 1. `for` Loop

The `for` loop is used to repeat a block of code a specific number of times.

**Example**:
Imagine you need to print the names of products in an order.

```javascript
let products = ["Laptop", "Mouse", "Keyboard"];

for (let i = 0; i < products.length; i++) {
    console.log("Product:", products[i]);
}
```

**Explanation**:
In this example, we use a `for` loop to iterate over the `products` array. The loop starts with `i` set to `0` and continues as long as `i` is less than `products.length`. In each iteration, it prints the current product name. The `console.log` statement inside the loop prints each product's name, demonstrating how to use a `for` loop to process each item in an array.

##### 2. `while` Loop

The `while` loop repeats a block of code as long as a specified condition is true.

**Example**:
Consider a scenario where you need to count down the number of items left in inventory.

```javascript
let inventory = 10;

while (inventory > 0) {
    console.log("Items left in inventory:", inventory);
    inventory--;
}
```

**Explanation**:
In this example, we use a `while` loop to count down the number of items in inventory. The loop continues to execute as long as `inventory` is greater than `0`. In each iteration, it prints the current number of items left and decrements `inventory` by `1`. The `console.log` statement inside the loop shows the decreasing inventory count, demonstrating how to use a `while` loop to repeat actions based on a condition.

##### 3. `do-while` Loop

The `do-while` loop is similar to the `while` loop, but it guarantees that the block of code will be executed at least once.

**Example**:
Suppose you need to ensure that a message is displayed at least once, regardless of the inventory count.

```javascript
let inventory = 0;

do {
    console.log("Checking inventory, items left:", inventory);
    inventory--;
} while (inventory > 0);
```

**Explanation**:
In this example, we use a `do-while` loop to check the inventory. The loop executes the code block once before checking the condition. Even though `inventory` is `0`, the `console.log` statement inside the loop is executed once, printing "Checking inventory, items left: 0". This demonstrates how the `do-while` loop ensures that the code block runs at least once, regardless of the condition.

#### Conclusion

By understanding and using conditionals and loops in JavaScript through these business-related examples, you can create dynamic and interactive web applications that handle various scenarios efficiently. Practice these concepts to build a strong foundation in JavaScript programming.

### Further Reading
- [MDN Web Docs: Control Flow](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [JavaScript.info: Conditional Operators](https://javascript.info/ifelse)
- [JavaScript.info: Loops](https://javascript.info/while-for)
- [Eloquent JavaScript: Program Structure](https://eloquentjavascript.net/02_program_structure.html)
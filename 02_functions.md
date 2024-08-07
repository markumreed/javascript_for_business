# JavaScript Functions

#### Introduction

Functions are fundamental building blocks in JavaScript, allowing you to encapsulate code into reusable blocks. This tutorial will cover function declaration, invocation, and scope using business case examples. By mastering these concepts, you can create more modular and maintainable code.

#### Function Declaration

A function declaration defines a named function that can be called (invoked) later in your code. It consists of the `function` keyword, followed by the function name, a list of parameters enclosed in parentheses, and a block of code enclosed in curly braces.

**Example**:
Suppose you need a function to calculate the total revenue from the sales of two products.

```javascript
function calculateRevenue(product1Sales, product2Sales) {
    return product1Sales + product2Sales;
}
```

**Explanation**:
In this example, we declare a function named `calculateRevenue` that takes two parameters, `product1Sales` and `product2Sales`. The function returns the sum of these two parameters, representing the total revenue. This encapsulation allows us to reuse the revenue calculation logic whenever needed without rewriting the code.

#### Function Invocation

Function invocation is the process of executing a function by calling its name and passing the required arguments. 

**Example**:
Using the previously declared `calculateRevenue` function, we can calculate the revenue from two different sets of sales data.

```javascript
let product1Sales = 5000;
let product2Sales = 3000;

let totalRevenue = calculateRevenue(product1Sales, product2Sales);
console.log("Total Revenue:", totalRevenue); // Output: Total Revenue: 8000
```

**Explanation**:
In this example, we invoke the `calculateRevenue` function by calling its name and passing the sales figures for two products. The function calculates the total revenue and returns the result, which is then stored in the `totalRevenue` variable. The `console.log` statement prints the total revenue, demonstrating how to use functions to encapsulate and reuse logic in your code.

#### Function Expressions

Functions can also be defined as expressions, which means they can be assigned to variables. Function expressions can be anonymous or named.

**Example**:
Suppose you need a function to calculate the monthly profit for a branch and you want to store it in a variable.

```javascript
const calculateProfit = function(revenue, expenses) {
    return revenue - expenses;
};

let branchRevenue = 10000;
let branchExpenses = 7000;

let monthlyProfit = calculateProfit(branchRevenue, branchExpenses);
console.log("Monthly Profit:", monthlyProfit); // Output: Monthly Profit: 3000
```

**Explanation**:
In this example, we define an anonymous function and assign it to the variable `calculateProfit`. This function takes `revenue` and `expenses` as parameters and returns the difference, representing the profit. We then invoke the function by calling the variable name and passing the revenue and expenses for a branch. The function calculates the profit, which is stored in the `monthlyProfit` variable. The `console.log` statement prints the monthly profit, demonstrating how to use function expressions to create reusable code blocks.

#### Arrow Functions

Arrow functions provide a shorter syntax for writing function expressions and automatically bind the `this` value.

**Example**:
Imagine you need a function to calculate the discount price for a product.

```javascript
const calculateDiscountPrice = (price, discount) => {
    return price - (price * (discount / 100));
};

let originalPrice = 100;
let discountRate = 20;

let discountPrice = calculateDiscountPrice(originalPrice, discountRate);
console.log("Discount Price:", discountPrice); // Output: Discount Price: 80
```

**Explanation**:
In this example, we use an arrow function to define `calculateDiscountPrice`. The arrow function takes `price` and `discount` as parameters and returns the discounted price. We invoke the function by passing the original price and discount rate, and the function calculates the discounted price, which is stored in the `discountPrice` variable. The `console.log` statement prints the discount price, showing how to use arrow functions to simplify function expressions.

#### Function Scope

Scope determines the accessibility of variables. There are three types of scope in JavaScript: global scope, function scope, and block scope.

##### 1. Global Scope

Variables declared outside any function or block have global scope and are accessible from anywhere in the code.

**Example**:
Suppose you need a global variable to store the company name.

```javascript
let companyName = "Tech Corp";

function showCompanyName() {
    console.log(companyName);
}

showCompanyName(); // Output: Tech Corp
```

**Explanation**:
In this example, `companyName` is a global variable because it is declared outside any function. The `showCompanyName` function can access and print the `companyName` variable. This demonstrates how global variables are accessible from any part of the code.

##### 2. Function Scope

Variables declared inside a function are local to that function and cannot be accessed outside it.

**Example**:
Consider a scenario where you need to calculate and print the total sales within a function.

```javascript
function calculateTotalSales() {
    let product1Sales = 5000;
    let product2Sales = 3000;
    let totalSales = product1Sales + product2Sales;
    console.log("Total Sales:", totalSales);
}

calculateTotalSales(); // Output: Total Sales: 8000
// console.log(totalSales); // Error: totalSales is not defined
```

**Explanation**:
In this example, `product1Sales`, `product2Sales`, and `totalSales` are variables with function scope because they are declared inside the `calculateTotalSales` function. These variables are not accessible outside the function, ensuring that they do not interfere with other parts of the code. The `console.log` statement inside the function prints the total sales, demonstrating how function scope confines variables to their respective functions.

##### 3. Block Scope

Variables declared with `let` or `const` inside a block (e.g., within `{}`) have block scope and are only accessible within that block.

**Example**:
Suppose you need to check if a product is in stock and if it is on sale, and you want to use block scope for the variables.

```javascript
let inStock = true;

if (inStock) {
    let onSale = true;
    console.log("Product is in stock and on sale:", onSale); // Output: Product is in stock and on sale: true
}

// console.log(onSale); // Error: onSale is not defined
```

**Explanation**:
In this example, `onSale` is declared with `let` inside the `if` block, giving it block scope. The variable is only accessible within the `if` block. The `console.log` statement inside the block prints whether the product is on sale. Attempting to access `onSale` outside the block results in an error, demonstrating how block scope confines variables to their respective blocks.

#### Conclusion

By understanding function declaration, invocation, and scope in JavaScript through these business-related examples, you can create modular, reusable, and maintainable code that handles various business scenarios effectively. Practice these concepts to build a strong foundation in JavaScript programming.

### Further Reading
- [MDN Web Docs: Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
- [JavaScript.info: Functions](https://javascript.info/function-basics)
- [Eloquent JavaScript: Functions](https://eloquentjavascript.net/03_functions.html)
- [MDN Web Docs: Scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope)
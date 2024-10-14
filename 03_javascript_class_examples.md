Below are examples of JavaScript classes with business case examples.

```javascript
// Class for Menu Items
class MenuItem {
    // Constructor to initialize the name and price of a menu item
    constructor(name, price) {
        this.name = name;  // The name of the menu item (e.g., "Burger")
        this.price = price; // The price of the menu item (e.g., 10.99)
    }
}

// Class for Orders
class Order {
    // Constructor to initialize an order with an ID and customer name
    constructor(orderId, customerName) {
        this.orderId = orderId;  // Unique ID for the order (e.g., 101)
        this.customerName = customerName;  // Name of the customer placing the order (e.g., "John Doe")
        this.items = [];  // Initialize an empty array to store ordered items
        this.totalAmount = 0;  // Initialize totalAmount to 0, to be calculated as items are added
    }

    // Method to add an item to the order
    addItem(menuItem) {
        this.items.push(menuItem);  // Add the menu item to the order's item list
        this.totalAmount += menuItem.price;  // Update the total amount by adding the price of the item
    }

    // Method to apply a discount to the total amount
    applyDiscount(discountAmount) {
        this.totalAmount -= discountAmount;  // Subtract the discount amount from the total amount
    }

    // Method to calculate the final total amount
    calculateTotal() {
        return this.totalAmount.toFixed(2);  // Return the total amount as a string, fixed to two decimal places (e.g., "15.99")
    }

    // Method to print the details of the order
    printOrder() {
        console.log(`Order ID: ${this.orderId}`);  // Print the order ID
        console.log(`Customer: ${this.customerName}`);  // Print the customer name
        console.log("Items Ordered:");  // Print a heading for the list of ordered items
        this.items.forEach(item => {
            // For each item in the order, print its name and price
            console.log(`- ${item.name}: $${item.price.toFixed(2)}`);
        });
        console.log(`Total Amount: $${this.calculateTotal()}`);  // Print the total amount after adding all items and applying any discounts
    }
}

// Example usage:
// Create new menu items
const item1 = new MenuItem("Burger", 10.99);  // Create a menu item named "Burger" priced at $10.99
const item2 = new MenuItem("Fries", 3.49);    // Create a menu item named "Fries" priced at $3.49
const item3 = new MenuItem("Soda", 1.99);     // Create a menu item named "Soda" priced at $1.99

// Create a new order
const order1 = new Order(101, "John Doe");  // Create a new order with ID 101 for customer "John Doe"

// Add items to the order
order1.addItem(item1);  // Add the "Burger" item to the order
order1.addItem(item2);  // Add the "Fries" item to the order
order1.addItem(item3);  // Add the "Soda" item to the order

// Apply a discount to the order
order1.applyDiscount(2.00);  // Apply a discount of $2.00 to the total amount

// Print the order details to the console
order1.printOrder();  // Print the order information, including items, customer name, and total amount
```

### Summary:
- The `MenuItem` class holds individual items like "Burger" and "Fries" with their prices.
- The `Order` class manages an order by storing customer information, items, and the total cost. It has methods to add items, apply discounts, and print the order details.
- The final section creates menu items, adds them to an order, applies a discount, and prints the order summary to the console.

Here’s an example using JavaScript classes with getters and setters in a business case where we manage a subscription service for customers. The subscription plan includes the customer's details, their plan, and whether or not their subscription is active.

```javascript
// Class representing a Subscription
class Subscription {
    constructor(customerName, plan) {
        this.customerName = customerName;  // The name of the customer
        this._plan = plan;  // Subscription plan (e.g., "Basic", "Premium")
        this._isActive = false;  // Subscription is initially inactive
    }

    // Getter for the subscription plan
    get plan() {
        return this._plan;  // Return the current subscription plan
    }

    // Setter for the subscription plan
    set plan(newPlan) {
        if (newPlan === "Basic" || newPlan === "Premium" || newPlan === "VIP") {
            this._plan = newPlan;  // Update the plan if it's one of the valid options
        } else {
            console.log("Invalid plan selected. Choose either 'Basic', 'Premium', or 'VIP'.");
        }
    }

    // Getter for the subscription status
    get isActive() {
        return this._isActive;  // Return whether the subscription is active
    }

    // Setter for the subscription status
    set isActive(status) {
        if (typeof status === 'boolean') {
            this._isActive = status;  // Set the active status if a boolean is passed
        } else {
            console.log("Invalid status. Must be true or false.");
        }
    }

    // Method to display the subscription details
    displaySubscription() {
        console.log(`Customer: ${this.customerName}`);
        console.log(`Plan: ${this.plan}`);
        console.log(`Subscription Active: ${this.isActive}`);
    }
}

// Example usage:

// Create a new subscription for a customer
const customerSubscription = new Subscription("Alice Smith", "Basic");

// Access the plan using the getter
console.log(customerSubscription.plan);  // Outputs: "Basic"

// Update the plan using the setter
customerSubscription.plan = "Premium";  // Changes the plan to "Premium"

// Access the subscription status using the getter
console.log(customerSubscription.isActive);  // Outputs: false (since it's inactive initially)

// Activate the subscription using the setter
customerSubscription.isActive = true;  // Activates the subscription

// Attempt to set an invalid plan
customerSubscription.plan = "Gold";  // Outputs: "Invalid plan selected. Choose either 'Basic', 'Premium', or 'VIP'."

// Display the subscription details
customerSubscription.displaySubscription();  // Outputs:
// Customer: Alice Smith
// Plan: Premium
// Subscription Active: true
```

### Explanation:
- **Getters** and **Setters** are used to access and modify private fields (`_plan` and `_isActive`).
- The getter `get plan()` allows us to retrieve the current subscription plan, and the setter `set plan()` validates input before updating the plan.
- Similarly, `get isActive()` returns the current subscription status, and `set isActive()` ensures that only boolean values are accepted when updating the subscription status.
- The `displaySubscription()` method prints the subscription details to the console.

This pattern of using getters and setters helps ensure controlled access to the object's properties and adds validation logic whenever changes are made.

In this example, we'll use JavaScript's private class fields (denoted by `#`) along with getters and setters to manage a customer loyalty program. This program will track a customer's points, their tier (based on points), and whether they have VIP status. The private properties ensure that these values can only be modified or accessed through the defined methods, adding more control to the logic.

```javascript
// Class representing a Customer Loyalty Program
class LoyaltyProgram {
    // Private properties for points, tier, and VIP status
    #points;
    #tier;
    #isVIP;

    constructor(customerName) {
        this.customerName = customerName;  // The name of the customer
        this.#points = 0;  // Points start at 0
        this.#tier = "Bronze";  // Default tier is "Bronze"
        this.#isVIP = false;  // VIP status is initially false
    }

    // Getter for points
    get points() {
        return this.#points;
    }

    // Setter for points
    set points(newPoints) {
        if (newPoints >= 0) {  // Points cannot be negative
            this.#points = newPoints;
            this.#updateTier();  // Update the tier whenever points are changed
        } else {
            console.log("Points cannot be negative.");
        }
    }

    // Getter for tier
    get tier() {
        return this.#tier;
    }

    // Getter for VIP status
    get isVIP() {
        return this.#isVIP;
    }

    // Setter for VIP status
    set isVIP(status) {
        if (typeof status === 'boolean') {
            this.#isVIP = status;  // Update VIP status only if a boolean is passed
        } else {
            console.log("Invalid status. Must be true or false.");
        }
    }

    // Private method to update the tier based on points
    #updateTier() {
        if (this.#points >= 1000) {
            this.#tier = "Gold";
            this.isVIP = true;  // Automatically grant VIP status for Gold tier
        } else if (this.#points >= 500) {
            this.#tier = "Silver";
            this.isVIP = false;  // No automatic VIP status for Silver tier
        } else {
            this.#tier = "Bronze";
            this.isVIP = false;  // No VIP status for Bronze tier
        }
    }

    // Method to display the customer details
    displayDetails() {
        console.log(`Customer: ${this.customerName}`);
        console.log(`Points: ${this.points}`);
        console.log(`Tier: ${this.tier}`);
        console.log(`VIP Status: ${this.isVIP}`);
    }
}

// Example usage:

// Create a new loyalty program instance for a customer
const customerLoyalty = new LoyaltyProgram("Bob Johnson");

// Add points using the setter
customerLoyalty.points = 600;  // Points are updated and tier is automatically recalculated

// Check the customer's details
customerLoyalty.displayDetails();  // Outputs:
// Customer: Bob Johnson
// Points: 600
// Tier: Silver
// VIP Status: false

// Add more points
customerLoyalty.points = 1200;  // Points are updated, tier changes to Gold, and VIP status is granted

// Check the updated details
customerLoyalty.displayDetails();  // Outputs:
// Customer: Bob Johnson
// Points: 1200
// Tier: Gold
// VIP Status: true

// Attempt to set negative points (invalid)
customerLoyalty.points = -100;  // Outputs: "Points cannot be negative."

// Manually update VIP status (even though it's typically set by the tier)
customerLoyalty.isVIP = false;  // VIP status is manually overridden

// Display the details again
customerLoyalty.displayDetails();  // Outputs:
// Customer: Bob Johnson
// Points: 1200
// Tier: Gold
// VIP Status: false
```

### Explanation:
- **Private properties**: The properties `#points`, `#tier`, and `#isVIP` are private and can only be accessed or modified within the class itself. This ensures encapsulation.
- **Getters and Setters**: Getters are used to retrieve private property values, while setters allow us to validate and update the values. The setter for `points` triggers the private method `#updateTier()` to adjust the tier and VIP status automatically based on the customer's points.
- **Private methods**: The `#updateTier()` method is private and not accessible from outside the class. It automatically updates the customer's tier and VIP status based on their points.

This pattern helps maintain control over how the properties are accessed and modified, ensuring that the program's logic stays consistent and reliable.

Here’s an example using static methods in a business case for a bank that processes account transactions. Static methods are used to handle shared functionality that doesn't rely on an individual instance of the class, like calculating transaction fees based on a provided amount.

```javascript
// Class representing a Bank Account
class BankAccount {
    constructor(accountNumber, customerName, balance = 0) {
        this.accountNumber = accountNumber;  // Unique account number
        this.customerName = customerName;  // The name of the account holder
        this.balance = balance;  // Account balance, default is 0
    }

    // Method to deposit money into the account
    deposit(amount) {
        if (amount > 0) {
            this.balance += amount;  // Add the deposit amount to the balance
            console.log(`Deposited $${amount.toFixed(2)} into account.`);
        } else {
            console.log("Deposit amount must be greater than 0.");
        }
    }

    // Method to withdraw money from the account
    withdraw(amount) {
        const fee = BankAccount.calculateTransactionFee(amount);  // Static method to calculate transaction fees
        const totalAmount = amount + fee;  // Total withdrawal amount includes the fee
        if (amount > 0 && totalAmount <= this.balance) {
            this.balance -= totalAmount;  // Deduct the total withdrawal amount from the balance
            console.log(`Withdrew $${amount.toFixed(2)}, including a fee of $${fee.toFixed(2)}.`);
        } else {
            console.log("Insufficient balance or invalid withdrawal amount.");
        }
    }

    // Static method to calculate transaction fees based on the amount
    static calculateTransactionFee(amount) {
        const feeRate = 0.02;  // 2% transaction fee
        return amount * feeRate;  // Calculate fee based on the amount
    }

    // Static method to compare two accounts based on balance
    static compareAccounts(account1, account2) {
        if (account1.balance > account2.balance) {
            return `${account1.customerName} has a higher balance than ${account2.customerName}.`;
        } else if (account1.balance < account2.balance) {
            return `${account2.customerName} has a higher balance than ${account1.customerName}.`;
        } else {
            return `Both accounts have the same balance.`;
        }
    }

    // Method to display the account details
    displayDetails() {
        console.log(`Account Number: ${this.accountNumber}`);
        console.log(`Customer Name: ${this.customerName}`);
        console.log(`Balance: $${this.balance.toFixed(2)}`);
    }
}

// Example usage:

// Create two accounts
const account1 = new BankAccount(123456, "Alice Johnson", 1000);
const account2 = new BankAccount(654321, "Bob Williams", 1500);

// Deposit money into account1
account1.deposit(500);  // Deposits $500 into Alice's account

// Withdraw money from account1
account1.withdraw(300);  // Withdraws $300 from Alice's account, including a 2% fee

// Display account details
account1.displayDetails();  // Displays Alice's updated account details

// Compare balances of two accounts using the static method
console.log(BankAccount.compareAccounts(account1, account2));  // Outputs comparison of balances between Alice and Bob

// Calculate transaction fee directly using the static method
const fee = BankAccount.calculateTransactionFee(200);  // Calculates the fee for a $200 transaction
console.log(`Transaction fee for $200 is $${fee.toFixed(2)}.`);
```

### Explanation:
- **Static Methods**: `calculateTransactionFee` and `compareAccounts` are static methods that belong to the class itself rather than any specific instance. They can be called directly on the class (e.g., `BankAccount.calculateTransactionFee`) and are typically used for utility functions or class-level logic.
- **Instance Methods**: Methods like `deposit`, `withdraw`, and `displayDetails` rely on individual instances of `BankAccount` to interact with specific data like `accountNumber` or `balance`.
- **Business Case**: The static `calculateTransactionFee` method calculates a 2% fee for a withdrawal based on the amount, while the `compareAccounts` method compares the balances of two different `BankAccount` instances.

Static methods are useful when you want to create shared behavior that isn't tied to any particular instance of a class but instead provides functionality relevant to the entire class.


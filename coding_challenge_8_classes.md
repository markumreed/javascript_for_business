### Coding Challenge: Employee Management System Using JavaScript Classes and OOP

**Introduction**: In this challenge, you will implement an Employee Management System using JavaScript classes to handle employees and departments within a company. You’ll use Object-Oriented Programming (OOP) concepts such as inheritance, encapsulation, and methods to create a scalable system. This system will allow you to manage employee details, handle departments, and calculate salaries and bonuses.

---

### Business Case

**Scenario**: A company wants to create a system to manage its employees and departments. The system should:
1. Store employee information, such as name, position, salary, and department.
2. Store department information, including department name and employees within the department.
3. Calculate the total salary for a department.
4. Handle bonuses for specific employees based on their performance.
5. Allow for different types of employees, such as regular employees and managers, each with unique properties.

---

### Tasks

1. **Create an Employee Class**

   - Create a class named `Employee` with the following properties:
     - `name` (string): The name of the employee.
     - `salary` (number): The salary of the employee.
     - `position` (string): The position of the employee (e.g., "Developer", "Designer").
     - `department` (string): The name of the department the employee belongs to.
   - The class should have a method `getDetails()` that returns a string with the employee’s name, position, and salary.
   - **Commit**: `"Create Employee class with properties and methods"`

2. **Create a Department Class**

   - Create a class named `Department` with the following properties:
     - `name` (string): The name of the department.
     - `employees` (array of `Employee` objects): An array to store employees in the department.
   - The class should have the following methods:
     - `addEmployee(employee)`: Adds an `Employee` object to the `employees` array.
     - `getDepartmentSalary()`: Returns the total salary of all employees in the department.
   - **Commit**: `"Create Department class to manage employees and calculate salary"`

3. **Create a Manager Class that Inherits from Employee**

   - Create a `Manager` class that inherits from the `Employee` class. The `Manager` class should:
     - Have an additional property `bonus` (number): The manager's bonus.
     - Override the `getDetails()` method to include the bonus in the string.
   - **Commit**: `"Create Manager class with inheritance from Employee"`

4. **Handle Bonuses for Managers**

   - In the `Department` class, add a method `calculateTotalSalaryWithBonus()` that calculates the total salary for the department, including any bonuses for managers.
   - **Commit**: `"Handle bonuses in the department salary calculation"`

5. **Create and Manage Departments and Employees**

   - Create a new company structure with at least two departments and multiple employees (including at least one manager per department).
   - Assign employees to departments using the `addEmployee()` method.
   - Calculate the total salary for each department using `getDepartmentSalary()` and `calculateTotalSalaryWithBonus()`.
   - **Commit**: `"Create and manage departments and employees"`

---

### Hints

- Use **inheritance** for the `Manager` class so that it reuses properties and methods from the `Employee` class.
- **Encapsulation**: Keep properties private (or restricted) where appropriate and use getter methods if needed.
- **Method overriding**: Ensure that the `Manager` class properly overrides the `getDetails()` method of the `Employee` class.
- Use array methods like `reduce()` to calculate total salaries in the department.
- Handle edge cases, such as when there are no employees in a department.

---

### Example Data

```javascript
// Create departments
const engineering = new Department("Engineering");
const marketing = new Department("Marketing");

// Create employees
const alice = new Employee("Alice", 80000, "Developer", "Engineering");
const bob = new Employee("Bob", 75000, "Designer", "Marketing");
const charlie = new Manager("Charlie", 120000, "Engineering Manager", "Engineering", 20000);
const diana = new Manager("Diana", 130000, "Marketing Manager", "Marketing", 25000);

// Add employees to departments
engineering.addEmployee(alice);
engineering.addEmployee(charlie);
marketing.addEmployee(bob);
marketing.addEmployee(diana);

// Calculate total salary for each department
console.log(`Total salary for Engineering: $${engineering.getDepartmentSalary()}`);
console.log(`Total salary with bonuses for Engineering: $${engineering.calculateTotalSalaryWithBonus()}`);
console.log(`Total salary for Marketing: $${marketing.getDepartmentSalary()}`);
console.log(`Total salary with bonuses for Marketing: $${marketing.calculateTotalSalaryWithBonus()}`);
```

---

### Submission Guidelines

- **GitHub Repository**: Share the location of your GitHub repository containing your project. Your repository should include a well-documented JavaScript file named `employee_management.js`, along with any additional files or documentation pertinent to the project.
  
- **Key Points for Submission**:
  - **Repository Link**: Ensure your repository is public or accessible to your instructors. Share the direct URL to your repository.
  - **Code Organization and Documentation**: Your code should be well-organized, clearly commented, and easy to understand. Use consistent naming conventions for variables and functions, and ensure proper indentation and spacing.
  - **Version Control Practices**: Commit changes frequently with clear, descriptive messages to track your development progress.

---

### Expected Outcomes

After completing this challenge, students will understand how to:

- Use **JavaScript Classes** and **Object-Oriented Programming (OOP)** concepts.
- Implement **inheritance**, **encapsulation**, and **method overriding** in real-world business cases.
- Manage employee and department structures using classes.
- Use GitHub for version control and demonstrate professional coding practices.
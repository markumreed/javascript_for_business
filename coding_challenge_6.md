### Coding Challenge: Employee Shift Management System

**Introduction**: In this challenge, you will create a simple employee shift management system for a small business. The system will track employee shift schedules, check availability, assign shifts, and calculate total hours worked for each employee. You'll use objects to represent employees and shifts, arrays to store multiple employees and shift schedules, and array/object methods to manipulate the data.

---

### Business Case

**Scenario**: A small business wants to manage its employee shift schedules. They need a system that:
1. Tracks employees and their assigned shifts.
2. Checks employee availability based on their existing shifts.
3. Assigns new shifts to available employees.
4. Calculates the total hours worked by each employee for the week.

---

### Tasks

1. **Create an Employees Array of Employee Objects**

   - Create an array named `employees` that contains at least 4 employee objects. Each employee should have the following properties:
     - `name` (string): The name of the employee.
     - `shifts` (array of objects): Each object in the array represents a shift with `day` (string) and `hours` (number) worked during that shift.
   - **Commit**: `"Initialize employees with shift schedules"`

2. **Create a Function to Display Employee Shift Details**

   - Write a function named `displayEmployeeShifts` that accepts an employee object and logs the employee’s name and their assigned shifts (day and hours worked).
   - **Commit**: `"Create displayEmployeeShifts function"`

3. **Create a Function to Assign a New Shift**

   - Write a function named `assignShift` that accepts an employee name, a day, and a number of hours. The function should:
     - Find the employee by name in the `employees` array.
     - Check if the employee is already assigned a shift for that day. If so, log an error message.
     - If the employee is available, add the new shift to their `shifts` array.
   - **Commit**: `"Create assignShift function"`

4. **Create a Function to Calculate Total Hours Worked**

   - Write a function named `calculateTotalHours` that accepts an employee name and calculates the total number of hours the employee has worked during the week by summing the hours from all shifts.
   - **Commit**: `"Create calculateTotalHours function"`

5. **Create a Function to List Employees with Free Days**

   - Write a function named `listAvailableEmployees` that accepts a day as input and logs the names of employees who are not assigned a shift for that day.
   - **Commit**: `"Create listAvailableEmployees function"`

---

### Hints

- Use the `find()` method to locate an employee by name in the array.
- Use `forEach()` or `reduce()` to iterate over shifts and calculate total hours.
- To check if an employee has a shift on a certain day, you can use the `some()` method on the `shifts` array.
- Handle edge cases, such as trying to assign a shift to an employee who is already working that day.

---

### Sample Data for Employees Initialization

```javascript
const employees = [
    { name: 'John', shifts: [{ day: 'Monday', hours: 8 }, { day: 'Wednesday', hours: 6 }] },
    { name: 'Sara', shifts: [{ day: 'Tuesday', hours: 5 }, { day: 'Thursday', hours: 7 }] },
    { name: 'David', shifts: [{ day: 'Monday', hours: 8 }] },
    { name: 'Emily', shifts: [{ day: 'Friday', hours: 8 }] }
];
```

---

### Submission Guidelines

- **GitHub Repository**: Share the location of your GitHub repository containing your project. Your repository should include a well-documented JavaScript file named `employee_shift_management.js`, along with any additional files or documentation pertinent to the project.
  
- **Key Points for Submission**:
  - **Repository Link**: Ensure your repository is public or accessible to your instructors. Share the direct URL to your repository.
  - **Code Organization and Documentation**: Your code should be well-organized, clearly commented, and easy to understand. Use consistent naming conventions for variables and functions, and ensure proper indentation and spacing.
  - **Version Control Practices**: Commit changes frequently with clear, descriptive messages to track your development progress.

---

### Expected Outcomes

After completing this challenge, students will understand how to:

- Create and manipulate objects and arrays in JavaScript.
- Use array methods like `find()`, `forEach()`, and `reduce()` for operations on employee data.
- Use control structures to check conditions and handle edge cases (like checking availability before assigning shifts).
- Use GitHub for version control and demonstrate professional coding practices.
### Answer Key for the Employee Shift Management System

Below is the solution for the **Employee Shift Management System** coding challenge. The solution is broken down into sections with explanations for each function.

---

### 1. **Initialize Employees Array with Shift Schedules**

**Code:**
```javascript
const employees = [
    { name: 'John', shifts: [{ day: 'Monday', hours: 8 }, { day: 'Wednesday', hours: 6 }] },
    { name: 'Sara', shifts: [{ day: 'Tuesday', hours: 5 }, { day: 'Thursday', hours: 7 }] },
    { name: 'David', shifts: [{ day: 'Monday', hours: 8 }] },
    { name: 'Emily', shifts: [{ day: 'Friday', hours: 8 }] }
];
```

- **Explanation**: The `employees` array holds employee objects, each with a `name` and a `shifts` array. The `shifts` array contains objects with a `day` and the number of `hours` worked on that day.

---

### 2. **Display Employee Shift Details**

**Code:**
```javascript
function displayEmployeeShifts(employee) {
    console.log(`Employee: ${employee.name}`);
    employee.shifts.forEach(shift => {
        console.log(`Shift: ${shift.day}, Hours: ${shift.hours}`);
    });
}
```

- **Explanation**:
  - The `displayEmployeeShifts` function takes an `employee` object as input and logs the employee’s name.
  - It uses `forEach()` to iterate over the employee's `shifts` array and logs each shift’s day and hours.

**Example Call**:
```javascript
displayEmployeeShifts(employees[0]);
```

---

### 3. **Assign a New Shift**

**Code:**
```javascript
function assignShift(employeeName, day, hours) {
    const employee = employees.find(emp => emp.name === employeeName);

    if (!employee) {
        console.log(`Error: Employee ${employeeName} not found.`);
        return;
    }

    const isAlreadyAssigned = employee.shifts.some(shift => shift.day === day);

    if (isAlreadyAssigned) {
        console.log(`Error: ${employeeName} already has a shift on ${day}.`);
        return;
    }

    employee.shifts.push({ day, hours });
    console.log(`Shift assigned to ${employeeName} on ${day} for ${hours} hours.`);
}
```

- **Explanation**:
  - The `assignShift` function accepts an `employeeName`, `day`, and `hours`.
  - It finds the employee in the `employees` array using the `find()` method.
  - It checks if the employee already has a shift on the given day using `some()`. If the employee is already working on that day, it logs an error message.
  - If the employee is available, it adds the new shift to the `shifts` array and logs a success message.

**Example Call**:
```javascript
assignShift('Sara', 'Monday', 6);
```

---

### 4. **Calculate Total Hours Worked**

**Code:**
```javascript
function calculateTotalHours(employeeName) {
    const employee = employees.find(emp => emp.name === employeeName);

    if (!employee) {
        console.log(`Error: Employee ${employeeName} not found.`);
        return 0;
    }

    const totalHours = employee.shifts.reduce((sum, shift) => sum + shift.hours, 0);
    console.log(`${employeeName} has worked a total of ${totalHours} hours.`);
    return totalHours;
}
```

- **Explanation**:
  - The `calculateTotalHours` function takes an `employeeName` and finds the employee in the `employees` array.
  - It uses the `reduce()` method to sum the hours worked across all shifts.
  - It logs the total hours worked by the employee and returns the value.

**Example Call**:
```javascript
calculateTotalHours('John');
```

---

### 5. **List Employees with Free Days**

**Code:**
```javascript
function listAvailableEmployees(day) {
    const availableEmployees = employees.filter(emp => 
        !emp.shifts.some(shift => shift.day === day)
    );

    if (availableEmployees.length === 0) {
        console.log(`No employees available on ${day}.`);
    } else {
        console.log(`Employees available on ${day}:`);
        availableEmployees.forEach(emp => {
            console.log(emp.name);
        });
    }
}
```

- **Explanation**:
  - The `listAvailableEmployees` function takes a `day` as input and filters the `employees` array to find employees who don’t have a shift on that day using `some()`.
  - If there are no available employees, it logs a message saying so.
  - If there are available employees, it logs their names.

**Example Call**:
```javascript
listAvailableEmployees('Wednesday');
```

---

### Example of Complete Flow

```javascript
// Display shifts for a specific employee
console.log("\n--- Display Shifts for John ---");
displayEmployeeShifts(employees[0]);

// Assign a new shift to an employee
console.log("\n--- Assign Shift for Sara on Monday ---");
assignShift('Sara', 'Monday', 6);

// Calculate total hours for an employee
console.log("\n--- Calculate Total Hours for John ---");
calculateTotalHours('John');

// List employees available on a specific day
console.log("\n--- List Employees Available on Wednesday ---");
listAvailableEmployees('Wednesday');
```

### Expected Output:

```
--- Display Shifts for John ---
Employee: John
Shift: Monday, Hours: 8
Shift: Wednesday, Hours: 6

--- Assign Shift for Sara on Monday ---
Error: Sara already has a shift on Monday.

--- Calculate Total Hours for John ---
John has worked a total of 14 hours.

--- List Employees Available on Wednesday ---
Employees available on Wednesday:
Sara
David
Emily
```

### Summary

- The solution covers creating employee objects with their assigned shifts, checking their availability, assigning new shifts, and calculating total hours worked.
- **Array methods** like `find()`, `forEach()`, `some()`, and `reduce()` are used to manipulate employee data efficiently.
- **Control structures** are used to check employee availability and handle edge cases (such as attempting to assign a shift to a day when the employee is already working).
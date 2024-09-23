### Coding Challenge: Company Department Salary Calculation

**Introduction**: In this challenge, you will create a recursive function to calculate the total salary expenditure for each department in a company. The company is divided into multiple departments, and each department has employees who might be organized in a hierarchy. You'll use recursion to navigate through the employees in a department and calculate the total salary expenditure for that department.

---

### Business Case

**Scenario**: A company wants to calculate the total salary expenditure for each of its departments. Each department has multiple employees, and some employees may have subordinates who report to them. The company needs a system that:
1. Stores information about each department, including its name, employees, and their respective subordinates.
2. Allows calculation of the total salary for a department, including the salaries of all employees and their subordinates within that department.

---

### Tasks

1. **Create a Department Structure**

   - Create an object named `company` that stores the departments in the company. Each department should be represented as an object with the following properties:
     - `departmentName` (string): The name of the department.
     - `employees` (array of employee objects): An array of employees working in the department. Each employee object should have:
       - `name` (string): The name of the employee.
       - `salary` (number): The salary of the employee.
       - `subordinates` (array of employee objects): An array of subordinate employees, which may be empty if the employee has no subordinates.
   - **Commit**: `"Initialize company structure with departments and employees"`

2. **Create a Recursive Function to Calculate Total Salary for a Department**

   - Write a function named `calculateDepartmentSalary` that accepts a department object and recursively calculates the total salary for that department, including the salaries of all employees and their subordinates.
   - The function should:
     - Start by adding each employee's salary to the total.
     - If the employee has subordinates, recursively add their salaries to the total.
   - **Commit**: `"Create recursive function to calculate department salary"`

3. **Create a Function to Calculate the Total Salary for All Departments**

   - Write a function named `calculateCompanySalary` that accepts the company object and iterates over each department to calculate the total salary for the entire company by summing up the salaries of all departments.
   - **Commit**: `"Calculate total salary for all departments in the company"`

---

### Hints

- Use **recursion** to navigate through each department’s employee hierarchy, especially for tasks like calculating the total salary.
- The base case for the recursion is when an employee has no subordinates (an empty `subordinates` array).
- Use a loop to iterate over each department in the company and apply the `calculateDepartmentSalary` function to calculate the department’s total salary.
- Handle edge cases, such as when a department has no employees or an employee has no subordinates.

---

### Sample Data for Company Initialization

```javascript
const company = {
    departments: [
        {
            departmentName: 'Engineering',
            employees: [
                {
                    name: 'Alice',
                    salary: 100000,
                    subordinates: [
                        {
                            name: 'Bob',
                            salary: 80000,
                            subordinates: [
                                {
                                    name: 'Charlie',
                                    salary: 60000,
                                    subordinates: []
                                }
                            ]
                        }
                    ]
                },
                {
                    name: 'David',
                    salary: 90000,
                    subordinates: []
                }
            ]
        },
        {
            departmentName: 'Sales',
            employees: [
                {
                    name: 'Eve',
                    salary: 85000,
                    subordinates: [
                        {
                            name: 'Frank',
                            salary: 70000,
                            subordinates: []
                        }
                    ]
                },
                {
                    name: 'Grace',
                    salary: 95000,
                    subordinates: []
                }
            ]
        }
    ]
};
```

---

### Submission Guidelines

- **GitHub Repository**: Share the location of your GitHub repository containing your project. Your repository should include a well-documented JavaScript file named `department_salary.js`, along with any additional files or documentation pertinent to the project.
  
- **Key Points for Submission**:
  - **Repository Link**: Ensure your repository is public or accessible to your instructors. Share the direct URL to your repository.
  - **Code Organization and Documentation**: Your code should be well-organized, clearly commented, and easy to understand. Use consistent naming conventions for variables and functions, and ensure proper indentation and spacing.
  - **Version Control Practices**: Commit changes frequently with clear, descriptive messages to track your development progress.

---

### Expected Outcomes

After completing this challenge, students will understand how to:

- Use recursion to navigate nested employee structures.
- Apply recursive functions in real-world business cases, such as calculating department-level salary expenditures.
- Handle complex, nested data structures like objects and arrays within recursive functions.
- Use GitHub for version control and demonstrate professional coding practices.
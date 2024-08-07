# Data Cleaning

#### Introduction

Data cleaning is a crucial step in data preprocessing, ensuring the data is accurate and usable for analysis and visualization. This tutorial will cover techniques for handling missing values, duplicates, and data transformation using JavaScript. By mastering these techniques, you can prepare data efficiently for business applications.

#### Handling Missing Values

Missing values can be handled by either removing them or imputing them with appropriate values.

##### 1. Removing Missing Values

**Example**:
Suppose you have an array of sales data with some missing values.

**JavaScript**:
```javascript
let salesData = [
    { month: 'January', sales: 15000 },
    { month: 'February', sales: null },
    { month: 'March', sales: 18000 },
    { month: 'April', sales: 22000 },
    { month: 'May', sales: null },
    { month: 'June', sales: 30000 }
];

// Remove entries with missing sales values
let cleanedData = salesData.filter(d => d.sales !== null);

console.log(cleanedData);
// Output: 
// [
//   { month: 'January', sales: 15000 },
//   { month: 'March', sales: 18000 },
//   { month: 'April', sales: 22000 },
//   { month: 'June', sales: 30000 }
// ]
```

**Explanation**:
In this example, the `filter` method is used to remove entries with missing sales values (`null`). The cleaned data array contains only the entries with valid sales values.

##### 2. Imputing Missing Values

**Example**:
Suppose you want to impute missing sales values with the average sales value.

**JavaScript**:
```javascript
let salesData = [
    { month: 'January', sales: 15000 },
    { month: 'February', sales: null },
    { month: 'March', sales: 18000 },
    { month: 'April', sales: 22000 },
    { month: 'May', sales: null },
    { month: 'June', sales: 30000 }
];

// Calculate average sales
let totalSales = salesData.reduce((sum, d) => sum + (d.sales || 0), 0);
let count = salesData.filter(d => d.sales !== null).length;
let averageSales = totalSales / count;

// Impute missing sales values with the average
let imputedData = salesData.map(d => {
    if (d.sales === null) {
        return { ...d, sales: averageSales };
    }
    return d;
});

console.log(imputedData);
// Output:
// [
//   { month: 'January', sales: 15000 },
//   { month: 'February', sales: 21250 },
//   { month: 'March', sales: 18000 },
//   { month: 'April', sales: 22000 },
//   { month: 'May', sales: 21250 },
//   { month: 'June', sales: 30000 }
// ]
```

**Explanation**:
In this example, the average sales value is calculated by summing the sales and dividing by the count of non-null sales values. The `map` method is used to impute missing sales values with the calculated average.

#### Handling Duplicates

Duplicates can be identified and removed to ensure data integrity.

##### 1. Removing Duplicates

**Example**:
Suppose you have an array of product data with some duplicate entries.

**JavaScript**:
```javascript
let productData = [
    { id: 1, name: 'Laptop' },
    { id: 2, name: 'Tablet' },
    { id: 3, name: 'Smartphone' },
    { id: 1, name: 'Laptop' },
    { id: 4, name: 'Monitor' }
];

// Remove duplicates based on the product ID
let uniqueProductData = productData.filter((value, index, self) =>
    index === self.findIndex((t) => (
        t.id === value.id
    ))
);

console.log(uniqueProductData);
// Output:
// [
//   { id: 1, name: 'Laptop' },
//   { id: 2, name: 'Tablet' },
//   { id: 3, name: 'Smartphone' },
//   { id: 4, name: 'Monitor' }
// ]
```

**Explanation**:
In this example, the `filter` method is used to remove duplicates by checking if the current index matches the first index of the product ID. This ensures only unique entries are included in the resulting array.

#### Data Transformation

Data transformation involves converting data into a suitable format for analysis or visualization.

##### 1. Converting Strings to Numbers

**Example**:
Suppose you have an array of sales data where sales values are stored as strings.

**JavaScript**:
```javascript
let salesData = [
    { month: 'January', sales: '15000' },
    { month: 'February', sales: '20000' },
    { month: 'March', sales: '18000' },
    { month: 'April', sales: '22000' },
    { month: 'May', sales: '25000' },
    { month: 'June', sales: '30000' }
];

// Convert sales values to numbers
let transformedData = salesData.map(d => ({
    ...d,
    sales: parseInt(d.sales, 10)
}));

console.log(transformedData);
// Output:
// [
//   { month: 'January', sales: 15000 },
//   { month: 'February', sales: 20000 },
//   { month: 'March', sales: 18000 },
//   { month: 'April', sales: 22000 },
//   { month: 'May', sales: 25000 },
//   { month: 'June', sales: 30000 }
// ]
```

**Explanation**:
In this example, the `map` method is used to convert the sales values from strings to numbers using `parseInt`.

##### 2. Normalizing Data

**Example**:
Suppose you need to normalize sales data to a range of 0 to 1.

**JavaScript**:
```javascript
let salesData = [
    { month: 'January', sales: 15000 },
    { month: 'February', sales: 20000 },
    { month: 'March', sales: 18000 },
    { month: 'April', sales: 22000 },
    { month: 'May', sales: 25000 },
    { month: 'June', sales: 30000 }
];

// Calculate the minimum and maximum sales values
let minSales = Math.min(...salesData.map(d => d.sales));
let maxSales = Math.max(...salesData.map(d => d.sales));

// Normalize sales values
let normalizedData = salesData.map(d => ({
    ...d,
    normalizedSales: (d.sales - minSales) / (maxSales - minSales)
}));

console.log(normalizedData);
// Output:
// [
//   { month: 'January', sales: 15000, normalizedSales: 0 },
//   { month: 'February', sales: 20000, normalizedSales: 0.3333333333333333 },
//   { month: 'March', sales: 18000, normalizedSales: 0.2 },
//   { month: 'April', sales: 22000, normalizedSales: 0.4666666666666667 },
//   { month: 'May', sales: 25000, normalizedSales: 0.6666666666666666 },
//   { month: 'June', sales: 30000, normalizedSales: 1 }
// ]
```

**Explanation**:
In this example, the minimum and maximum sales values are calculated using `Math.min` and `Math.max`. The sales values are then normalized to a range of 0 to 1 using the formula `(value - min) / (max - min)`.

#### Conclusion

By understanding and using JavaScript for data cleaning through these business-related examples, you can handle missing values, duplicates, and transform data efficiently for analysis and visualization. Practice these concepts to build a strong foundation in JavaScript data cleaning techniques.

### Further Reading
- [MDN Web Docs: Array.prototype.filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
- [MDN Web Docs: Array.prototype.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [JavaScript.info: Arrays](https://javascript.info/array)
- [Eloquent JavaScript: Data](https://eloquentjavascript.net/05_higher_order.html)
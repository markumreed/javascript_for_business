# JavaScript Data Transformation

#### Introduction

Data transformation is an essential process in data preprocessing, enabling you to aggregate, merge, and reshape data for analysis and visualization. This tutorial will cover techniques for data aggregation, merging, and reshaping using JavaScript with business-related examples. By mastering these techniques, you can efficiently handle complex data manipulations.

#### Data Aggregation

Data aggregation involves summarizing data by grouping and performing calculations such as sum, average, count, etc.

##### Example: Aggregating Sales Data by Month

**JavaScript**:
```javascript
let salesData = [
    { month: 'January', product: 'Laptop', sales: 15000 },
    { month: 'January', product: 'Tablet', sales: 8000 },
    { month: 'February', product: 'Laptop', sales: 20000 },
    { month: 'February', product: 'Tablet', sales: 12000 },
    { month: 'March', product: 'Laptop', sales: 18000 },
    { month: 'March', product: 'Tablet', sales: 10000 }
];

// Aggregate sales data by month
let aggregatedData = salesData.reduce((acc, curr) => {
    let found = acc.find(item => item.month === curr.month);
    if (found) {
        found.sales += curr.sales;
    } else {
        acc.push({ month: curr.month, sales: curr.sales });
    }
    return acc;
}, []);

console.log(aggregatedData);
// Output:
// [
//   { month: 'January', sales: 23000 },
//   { month: 'February', sales: 32000 },
//   { month: 'March', sales: 28000 }
// ]
```

**Explanation**:
In this example, the `reduce` method is used to aggregate sales data by month. For each entry in `salesData`, it checks if the month is already in the accumulator. If it is, the sales values are summed; otherwise, a new entry is created.

#### Data Merging

Data merging involves combining two or more datasets based on a common key.

##### Example: Merging Product Details with Sales Data

**JavaScript**:
```javascript
let productDetails = [
    { productId: 1, productName: 'Laptop' },
    { productId: 2, productName: 'Tablet' },
    { productId: 3, productName: 'Smartphone' }
];

let salesData = [
    { productId: 1, month: 'January', sales: 15000 },
    { productId: 2, month: 'January', sales: 8000 },
    { productId: 1, month: 'February', sales: 20000 },
    { productId: 2, month: 'February', sales: 12000 },
    { productId: 3, month: 'March', sales: 10000 }
];

// Merge product details with sales data
let mergedData = salesData.map(sale => {
    let product = productDetails.find(p => p.productId === sale.productId);
    return { ...sale, productName: product ? product.productName : 'Unknown' };
});

console.log(mergedData);
// Output:
// [
//   { productId: 1, month: 'January', sales: 15000, productName: 'Laptop' },
//   { productId: 2, month: 'January', sales: 8000, productName: 'Tablet' },
//   { productId: 1, month: 'February', sales: 20000, productName: 'Laptop' },
//   { productId: 2, month: 'February', sales: 12000, productName: 'Tablet' },
//   { productId: 3, month: 'March', sales: 10000, productName: 'Smartphone' }
// ]
```

**Explanation**:
In this example, the `map` method is used to iterate over the `salesData` array. For each sale, the corresponding product details are found using the `find` method, and the product name is added to the sale entry.

#### Data Reshaping

Data reshaping involves changing the structure of data, such as pivoting and unpivoting data.

##### Example: Pivoting Sales Data

**JavaScript**:
```javascript
let salesData = [
    { month: 'January', product: 'Laptop', sales: 15000 },
    { month: 'January', product: 'Tablet', sales: 8000 },
    { month: 'February', product: 'Laptop', sales: 20000 },
    { month: 'February', product: 'Tablet', sales: 12000 },
    { month: 'March', product: 'Laptop', sales: 18000 },
    { month: 'March', product: 'Tablet', sales: 10000 }
];

// Pivot sales data to have products as columns
let pivotedData = salesData.reduce((acc, curr) => {
    let found = acc.find(item => item.month === curr.month);
    if (found) {
        found[curr.product] = curr.sales;
    } else {
        let newItem = { month: curr.month };
        newItem[curr.product] = curr.sales;
        acc.push(newItem);
    }
    return acc;
}, []);

console.log(pivotedData);
// Output:
// [
//   { month: 'January', Laptop: 15000, Tablet: 8000 },
//   { month: 'February', Laptop: 20000, Tablet: 12000 },
//   { month: 'March', Laptop: 18000, Tablet: 10000 }
// ]
```

**Explanation**:
In this example, the `reduce` method is used to pivot sales data so that each product becomes a column. For each entry in `salesData`, it checks if the month is already in the accumulator. If it is, the sales value is added as a new property for the product; otherwise, a new entry is created.

##### Example: Unpivoting Sales Data

**JavaScript**:
```javascript
let pivotedData = [
    { month: 'January', Laptop: 15000, Tablet: 8000 },
    { month: 'February', Laptop: 20000, Tablet: 12000 },
    { month: 'March', Laptop: 18000, Tablet: 10000 }
];

// Unpivot sales data to have a row for each product and month
let unpivotedData = pivotedData.flatMap(item => {
    return Object.keys(item)
        .filter(key => key !== 'month')
        .map(key => ({
            month: item.month,
            product: key,
            sales: item[key]
        }));
});

console.log(unpivotedData);
// Output:
// [
//   { month: 'January', product: 'Laptop', sales: 15000 },
//   { month: 'January', product: 'Tablet', sales: 8000 },
//   { month: 'February', product: 'Laptop', sales: 20000 },
//   { month: 'February', product: 'Tablet', sales: 12000 },
//   { month: 'March', product: 'Laptop', sales: 18000 },
//   { month: 'March', product: 'Tablet', sales: 10000 }
// ]
```

**Explanation**:
In this example, the `flatMap` method is used to unpivot sales data so that each product and month combination becomes a row. The `flatMap` method iterates over each entry in `pivotedData`, creating a new array for each product, which is then flattened into a single array.

#### Conclusion

By understanding and using JavaScript for data transformation through these business-related examples, you can efficiently aggregate, merge, and reshape data for analysis and visualization. Practice these concepts to build a strong foundation in JavaScript data transformation techniques.

### Further Reading
- [MDN Web Docs: Array.prototype.reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
- [MDN Web Docs: Array.prototype.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [MDN Web Docs: Array.prototype.flatMap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap)
- [JavaScript.info: Arrays](https://javascript.info/array)
- [Eloquent JavaScript: Data](https://eloquentjavascript.net/05_higher_order.html)
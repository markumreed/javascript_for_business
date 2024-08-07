### Tutorial: Data Visualization Using Chart.js for Business

#### Introduction

Chart.js is a popular JavaScript library for creating beautiful and interactive charts. It provides a simple way to visualize data using various chart types, including bar charts, line charts, pie charts, and more. This tutorial will cover the basics of Chart.js using business-related examples to help you create dynamic data visualizations.

#### Setting Up Chart.js

To use Chart.js, you need to include the Chart.js library in your HTML file. You can do this by adding a script tag with a CDN link.

**Example**:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Chart.js Data Visualization</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
    <h1>Sales Data Visualization</h1>
    <canvas id="myChart" width="400" height="200"></canvas>
</body>
</html>
```

**Explanation**:
In this example, the Chart.js library is included by adding a script tag with a CDN link in the HTML file. The `canvas` element with the ID `myChart` will be used to contain the chart.

#### Creating a Bar Chart

A bar chart is a common way to visualize categorical data with rectangular bars. Let’s create a bar chart to visualize monthly sales data.

##### 1. Preparing the Data

**Example**:
```javascript
<script>
    let salesData = {
        labels: ['January', 'February', 'March', 'April', 'May', 'June'],
        datasets: [{
            label: 'Monthly Sales',
            data: [15000, 20000, 18000, 22000, 25000, 30000],
            backgroundColor: 'rgba(75, 192, 192, 0.2)',
            borderColor: 'rgba(75, 192, 192, 1)',
            borderWidth: 1
        }]
    };
</script>
```

**Explanation**:
In this example, the `salesData` object contains the labels for the months and the sales figures for each month. The `datasets` array includes the data, background color, border color, and border width for the bars.

##### 2. Creating the Bar Chart

**Example**:
```javascript
<script>
    let ctx = document.getElementById('myChart').getContext('2d');
    let myChart = new Chart(ctx, {
        type: 'bar',
        data: salesData,
        options: {
            scales: {
                y: {
                    beginAtZero: true
                }
            }
        }
    });
</script>
```

**Explanation**:
In this example, a new Chart instance is created by passing the context of the `canvas` element and an object containing the chart type, data, and options. The `type` is set to 'bar', the `data` is set to the `salesData` object, and the `options` object configures the y-axis to begin at zero.

#### Creating a Line Chart

A line chart is useful for visualizing data trends over time. Let’s create a line chart to visualize the same monthly sales data.

##### 1. Preparing the Data

**Example**:
```javascript
<script>
    let salesData = {
        labels: ['January', 'February', 'March', 'April', 'May', 'June'],
        datasets: [{
            label: 'Monthly Sales',
            data: [15000, 20000, 18000, 22000, 25000, 30000],
            backgroundColor: 'rgba(75, 192, 192, 0.2)',
            borderColor: 'rgba(75, 192, 192, 1)',
            borderWidth: 1,
            fill: false,
            tension: 0.1
        }]
    };
</script>
```

**Explanation**:
The data preparation for the line chart is similar to the bar chart. The only difference is that the `fill` property is set to `false` and the `tension` property is added to control the curvature of the line.

##### 2. Creating the Line Chart

**Example**:
```javascript
<script>
    let ctx = document.getElementById('myChart').getContext('2d');
    let myChart = new Chart(ctx, {
        type: 'line',
        data: salesData,
        options: {
            scales: {
                y: {
                    beginAtZero: true
                }
            }
        }
    });
</script>
```

**Explanation**:
In this example, a new Chart instance is created with the `type` set to 'line'. The rest of the configuration is similar to the bar chart.

#### Creating a Pie Chart

A pie chart is useful for visualizing the proportions of different categories. Let’s create a pie chart to visualize the sales distribution among different products.

##### 1. Preparing the Data

**Example**:
```javascript
<script>
    let productSalesData = {
        labels: ['Laptops', 'Tablets', 'Smartphones'],
        datasets: [{
            label: 'Product Sales',
            data: [30000, 15000, 25000],
            backgroundColor: [
                'rgba(255, 99, 132, 0.2)',
                'rgba(54, 162, 235, 0.2)',
                'rgba(255, 206, 86, 0.2)'
            ],
            borderColor: [
                'rgba(255, 99, 132, 1)',
                'rgba(54, 162, 235, 1)',
                'rgba(255, 206, 86, 1)'
            ],
            borderWidth: 1
        }]
    };
</script>
```

**Explanation**:
In this example, the `productSalesData` object contains the labels for the products and the sales figures for each product. The `datasets` array includes the data, background colors, border colors, and border width for the pie slices.

##### 2. Creating the Pie Chart

**Example**:
```javascript
<script>
    let ctx = document.getElementById('myChart').getContext('2d');
    let myChart = new Chart(ctx, {
        type: 'pie',
        data: productSalesData
    });
</script>
```

**Explanation**:
In this example, a new Chart instance is created with the `type` set to 'pie'. The rest of the configuration is similar to the previous charts.

#### Customizing Charts

Chart.js allows for extensive customization of charts, including titles, legends, tooltips, and more.

##### Example: Adding a Title and Customizing Tooltips

**Example**:
```javascript
<script>
    let salesData = {
        labels: ['January', 'February', 'March', 'April', 'May', 'June'],
        datasets: [{
            label: 'Monthly Sales',
            data: [15000, 20000, 18000, 22000, 25000, 30000],
            backgroundColor: 'rgba(75, 192, 192, 0.2)',
            borderColor: 'rgba(75, 192, 192, 1)',
            borderWidth: 1
        }]
    };

    let ctx = document.getElementById('myChart').getContext('2d');
    let myChart = new Chart(ctx, {
        type: 'bar',
        data: salesData,
        options: {
            plugins: {
                title: {
                    display: true,
                    text: 'Monthly Sales Data'
                },
                tooltip: {
                    callbacks: {
                        label: function(context) {
                            let label = context.dataset.label || '';
                            if (label) {
                                label += ': ';
                            }
                            label += `$${context.parsed.y.toLocaleString()}`;
                            return label;
                        }
                    }
                }
            },
            scales: {
                y: {
                    beginAtZero: true
                }
            }
        }
    });
</script>
```

**Explanation**:
In this example, the `options` object includes a `plugins` property to add a title and customize tooltips. The `title` plugin is used to display a chart title. The `tooltip` plugin includes a `callbacks` property to customize the tooltip labels, formatting the sales figures with a dollar sign and commas.

#### Conclusion

By understanding and using Chart.js for data visualization through these business-related examples, you can create dynamic and interactive charts that help users understand complex data. Practice these concepts to build a strong foundation in data visualization with Chart.js.

### Further Reading
- [Chart.js Official Documentation](https://www.chartjs.org/docs/latest/)
- [Chart.js Samples](https://www.chartjs.org/samples/latest/)
- [MDN Web Docs: Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)

### Complete Example: Bar Chart, Line Chart, and Pie Chart

**Complete HTML and JavaScript Example**:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Chart.js Data Visualization</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        canvas {
            display: block;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <h1>Sales Data Visualization</h1>
    <canvas id="myChart" width="400" height="200"></canvas>

    <script>
        let salesData = {
            labels: ['January', 'February', 'March', 'April', 'May', 'June'],
            datasets: [{
                label: 'Monthly Sales',
                data: [15000, 20000, 180

00, 22000, 25000, 30000],
                backgroundColor: 'rgba(75, 192, 192, 0.2)',
                borderColor: 'rgba(75, 192, 192, 1)',
                borderWidth: 1,
                fill: false,
                tension: 0.1
            }]
        };

        let productSalesData = {
            labels: ['Laptops', 'Tablets', 'Smartphones'],
            datasets: [{
                label: 'Product Sales',
                data: [30000, 15000, 25000],
                backgroundColor: [
                    'rgba(255, 99, 132, 0.2)',
                    'rgba(54, 162, 235, 0.2)',
                    'rgba(255, 206, 86, 0.2)'
                ],
                borderColor: [
                    'rgba(255, 99, 132, 1)',
                    'rgba(54, 162, 235, 1)',
                    'rgba(255, 206, 86, 1)'
                ],
                borderWidth: 1
            }]
        };

        let ctx = document.getElementById('myChart').getContext('2d');

        // Bar Chart
        let barChart = new Chart(ctx, {
            type: 'bar',
            data: salesData,
            options: {
                plugins: {
                    title: {
                        display: true,
                        text: 'Monthly Sales Data'
                    },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                let label = context.dataset.label || '';
                                if (label) {
                                    label += ': ';
                                }
                                label += `$${context.parsed.y.toLocaleString()}`;
                                return label;
                            }
                        }
                    }
                },
                scales: {
                    y: {
                        beginAtZero: true
                    }
                }
            }
        });

        // Line Chart
        let lineChart = new Chart(ctx, {
            type: 'line',
            data: salesData,
            options: {
                plugins: {
                    title: {
                        display: true,
                        text: 'Monthly Sales Data'
                    },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                let label = context.dataset.label || '';
                                if (label) {
                                    label += ': ';
                                }
                                label += `$${context.parsed.y.toLocaleString()}`;
                                return label;
                            }
                        }
                    }
                },
                scales: {
                    y: {
                        beginAtZero: true
                    }
                }
            }
        });

        // Pie Chart
        let pieChart = new Chart(ctx, {
            type: 'pie',
            data: productSalesData
        });
    </script>
</body>
</html>
```

This complete example combines a bar chart, line chart, and pie chart using Chart.js, showcasing how different types of visualizations can be created and customized.
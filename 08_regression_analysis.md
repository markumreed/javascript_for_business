### Tutorial: Regression Analysis in JavaScript: Linear Regression, Multiple Regression, Logistic Regression

#### Introduction

Regression analysis is a powerful statistical method used to examine the relationships between variables. It allows us to understand and predict the behavior of dependent variables based on one or more independent variables. This tutorial will cover linear regression, multiple regression, and logistic regression using JavaScript and the `simple-statistics` library.

### Setting Up Simple-statistics

To use Simple-statistics, you can include it in your HTML file or install it via npm if you're using Node.js.

##### Example: Including Simple-statistics in an HTML File

**HTML**:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Regression Analysis with JavaScript</title>
    <script src="https://cdn.jsdelivr.net/npm/simple-statistics@7.4.0/dist/simple-statistics.min.js"></script>
</head>
<body>
    <h1>Regression Analysis with JavaScript</h1>
    <div id="output"></div>
</body>
</html>
```

### Linear Regression

Linear regression is used to model the relationship between a dependent variable and an independent variable by fitting a linear equation to the observed data.

#### Example: Performing Linear Regression

**JavaScript**:
```javascript
<script>
    // Sample data (x, y)
    const data = [
        [1, 2],
        [2, 3],
        [3, 4],
        [4, 5],
        [5, 6]
    ];

    // Performing linear regression
    const regressionResult = ss.linearRegression(data);
    console.log('Linear Regression Result:', regressionResult);

    // Using the regression line to predict values
    const regressionLine = ss.linearRegressionLine(regressionResult);
    console.log('Predicted value for x = 6:', regressionLine(6));
</script>
```

**Explanation**:
- The dataset `data` contains pairs of (x, y) values.
- The `ss.linearRegression` function calculates the linear regression model.
- The `ss.linearRegressionLine` function creates a function to predict values using the regression model.
- The predicted value for x = 6 is printed to the console.

### Multiple Regression

Multiple regression is used to model the relationship between a dependent variable and multiple independent variables by fitting a linear equation to the observed data.

#### Example: Performing Multiple Regression

**JavaScript**:
```javascript
<script>
    // Sample data (features and target)
    const features = [
        [1, 2],
        [2, 3],
        [3, 4],
        [4, 5],
        [5, 6]
    ];
    const target = [2, 3, 4, 5, 6];

    // Performing multiple linear regression
    const multipleRegressionResult = ss.linearRegression(features.map((f, i) => [...f, target[i]]));
    console.log('Multiple Linear Regression Result:', multipleRegressionResult);

    // Using the regression line to predict values
    const multipleRegressionLine = ss.linearRegressionLine(multipleRegressionResult);
    console.log('Predicted value for [6, 7]:', multipleRegressionLine([6, 7]));
</script>
```

**Explanation**:
- The dataset `features` contains pairs of independent variable values, and `target` contains the dependent variable values.
- The `ss.linearRegression` function calculates the multiple regression model.
- The `ss.linearRegressionLine` function creates a function to predict values using the regression model.
- The predicted value for [6, 7] is printed to the console.

### Logistic Regression

Logistic regression is used for binary classification problems, where the dependent variable is categorical with two possible outcomes. It models the probability of a binary outcome based on one or more independent variables.

#### Example: Performing Logistic Regression

**JavaScript**:
```javascript
<script>
    // Logistic regression function (using gradient descent)
    function logisticRegression(X, y, learningRate = 0.1, iterations = 1000) {
        const weights = new Array(X[0].length).fill(0);
        const sigmoid = z => 1 / (1 + Math.exp(-z));

        for (let iter = 0; iter < iterations; iter++) {
            for (let i = 0; i < X.length; i++) {
                const predicted = sigmoid(X[i].reduce((sum, x, j) => sum + x * weights[j], 0));
                const error = y[i] - predicted;
                for (let j = 0; j < weights.length; j++) {
                    weights[j] += learningRate * error * X[i][j];
                }
            }
        }
        return weights;
    }

    // Sample data (features and target)
    const X = [
        [1, 2],
        [2, 3],
        [3, 4],
        [4, 5],
        [5, 6]
    ];
    const y = [0, 0, 1, 1, 1];

    // Performing logistic regression
    const weights = logisticRegression(X, y);
    console.log('Logistic Regression Weights:', weights);

    // Predict function
    function predict(features, weights) {
        const z = features.reduce((sum, x, j) => sum + x * weights[j], 0);
        return 1 / (1 + Math.exp(-z));
    }

    // Using the model to predict a value
    console.log('Predicted probability for [6, 7]:', predict([6, 7], weights));
</script>
```

**Explanation**:
- The `logisticRegression` function uses gradient descent to calculate the logistic regression model.
- The `sigmoid` function is used to model the probability of a binary outcome.
- The `predict` function uses the weights from the logistic regression model to predict the probability of a binary outcome for new data.
- The predicted probability for [6, 7] is printed to the console.

### Practical Example: Regression Analysis on Real-World Data

Let's apply these regression techniques to a real-world dataset. For this example, we will use a dataset of house prices.

**JavaScript**:
```javascript
<script>
    // Load and preprocess the dataset
    const datasetUrl = 'path/to/house_prices.csv'; // Replace with the actual path to your dataset
    dfd.readCSV(datasetUrl).then(df => {
        // Preprocess the data
        const xs = df.iloc({columns: [0, 1, 2]}); // Select feature columns
        const ys = df.iloc({columns: [3]}); // Select target column

        // Convert to tensors
        const xsTensor = tf.tensor2d(xs.values);
        const ysTensor = tf.tensor2d(ys.values);

        // Linear Regression
        const linearRegressionResult = ss.linearRegression(xs.values.map((f, i) => [...f, ys.values[i]]));
        const linearRegressionLine = ss.linearRegressionLine(linearRegressionResult);
        console.log('Linear Regression Prediction:', linearRegressionLine([1200, 3, 2]));

        // Multiple Regression
        const multipleRegressionResult = ss.linearRegression(xs.values.map((f, i) => [...f, ys.values[i]]));
        const multipleRegressionLine = ss.linearRegressionLine(multipleRegressionResult);
        console.log('Multiple Regression Prediction:', multipleRegressionLine([1500, 4, 3]));

        // Logistic Regression (using a binary target column)
        const yBinary = ys.values.map(price => (price > 300000 ? 1 : 0)); // Example threshold
        const logisticWeights = logisticRegression(xs.values, yBinary);
        console.log('Logistic Regression Prediction:', predict([1500, 4, 3], logisticWeights));
    });
</script>
```

**Explanation**:
- The house prices dataset is loaded and preprocessed.
- Feature columns and the target column are selected and converted to tensors.
- Linear regression and multiple regression are performed, and predictions are made.
- Logistic regression is performed using a binary target column, and a prediction is made.

### Conclusion

Regression analysis is a powerful tool for understanding and predicting the behavior of dependent variables based on one or more independent variables. By using JavaScript and the `simple-statistics` library, you can easily perform linear regression, multiple regression, and logistic regression to analyze and make predictions based on your data.

### Further Reading
- [Simple-statistics Official Documentation](https://simplestatistics.org/)
- [JavaScript.info: Data types](https://javascript.info/data-types)
- [MDN Web Docs: Working with objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
- [Eloquent JavaScript: Data](https://eloquentjavascript.net/04_data.html)
- [Linear Regression Analysis](https://en.wikipedia.org/wiki/Linear_regression)
- [Multiple Regression Analysis](https://en.wikipedia.org/wiki/Multiple_regression)
- [Logistic Regression Analysis](https://en.wikipedia.org/wiki/Logistic_regression)

By following this tutorial and exploring further resources, you can master the use of regression analysis in JavaScript and apply it effectively in your projects.
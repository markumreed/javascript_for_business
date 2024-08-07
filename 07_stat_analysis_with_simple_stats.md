# Statistical Analysis with Simple-statistics

#### Introduction

Simple-statistics is a robust JavaScript library that enables developers to perform statistical analysis in a straightforward and efficient manner. The library offers a wide array of statistical functions, ranging from basic descriptive statistics to more complex regression analysis. This tutorial will delve into these functions, providing practical examples to illustrate how Simple-statistics can be leveraged for data analysis.

### 1. Setting Up Simple-statistics

To use Simple-statistics, you can include it in your HTML file or install it via npm if you're using Node.js.

##### Example: Including Simple-statistics in an HTML File

**HTML**:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Statistical Analysis with Simple-statistics</title>
    <script src="https://cdn.jsdelivr.net/npm/simple-statistics@7.4.0/dist/simple-statistics.min.js"></script>
</head>
<body>
    <h1>Statistical Analysis with Simple-statistics</h1>
    <div id="output"></div>
</body>
</html>
```

This example includes the Simple-statistics library via a CDN link, making it easy to start using its functionalities directly in a browser environment.

### 2. Descriptive Statistics

Descriptive statistics provide simple summaries about the sample and the measures. Common descriptive statistics include mean, median, mode, variance, and standard deviation. These metrics help understand the distribution and central tendency of the data.

#### Example: Calculating Descriptive Statistics

**JavaScript**:
```javascript
<script>
    // Sample data
    const data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    // Calculating mean
    const mean = ss.mean(data);
    console.log('Mean:', mean);

    // Calculating median
    const median = ss.median(data);
    console.log('Median:', median);

    // Calculating mode
    const mode = ss.mode(data);
    console.log('Mode:', mode);

    // Calculating variance
    const variance = ss.variance(data);
    console.log('Variance:', variance);

    // Calculating standard deviation
    const standardDeviation = ss.standardDeviation(data);
    console.log('Standard Deviation:', standardDeviation);
</script>
```

**Discussion**:
- **Mean**: The average value of the dataset. It is calculated by summing all the values and dividing by the number of values.
- **Median**: The middle value of the dataset when it is ordered. If the number of values is even, it is the average of the two middle numbers.
- **Mode**: The most frequently occurring value in the dataset. If all values are unique, the mode may not be meaningful.
- **Variance**: Measures the spread of the data points. It is the average of the squared differences from the mean.
- **Standard Deviation**: The square root of the variance, providing a measure of the average distance of the data points from the mean.

### 3. Probability Distributions

Probability distributions describe how the values of a random variable are distributed. Simple-statistics provides functions to work with various probability distributions, such as the normal distribution.

#### Example: Working with Normal Distribution

**JavaScript**:
```javascript
<script>
    // Mean and standard deviation
    const mean = 0;
    const standardDeviation = 1;

    // Probability density function (PDF)
    const pdf = ss.normalDistribution.pdf(mean, standardDeviation);
    console.log('PDF at x = 0:', pdf(0));

    // Cumulative distribution function (CDF)
    const cdf = ss.normalDistribution.cdf(mean, standardDeviation);
    console.log('CDF at x = 0:', cdf(0));

    // Inverse cumulative distribution function (ICDF)
    const icdf = ss.normalDistribution.icdf(mean, standardDeviation);
    console.log('ICDF at p = 0.5:', icdf(0.5));
</script>
```

**Discussion**:
- **PDF (Probability Density Function)**: Describes the likelihood of a random variable taking on a particular value. For the normal distribution, it gives the height of the bell curve at any given point.
- **CDF (Cumulative Distribution Function)**: Represents the probability that a random variable is less than or equal to a certain value. For the normal distribution, it provides the area under the bell curve to the left of a specific point.
- **ICDF (Inverse Cumulative Distribution Function)**: The inverse of the CDF. It finds the value corresponding to a given cumulative probability. For example, `icdf(0.5)` gives the median of the distribution.

### 4. Hypothesis Testing

Hypothesis testing is a statistical method used to make decisions about the population based on sample data. It involves testing an assumption (hypothesis) and determining whether there is enough evidence to reject it.

#### Example: Performing a T-Test

**JavaScript**:
```javascript
<script>
    // Sample data
    const sample1 = [1, 2, 3, 4, 5];
    const sample2 = [2, 3, 4, 5, 6];

    // Performing a t-test
    const tTestResult = ss.tTestTwoSample(sample1, sample2);
    console.log('T-Test Result:', tTestResult);
</script>
```

**Discussion**:
- **T-Test**: Compares the means of two samples to determine if they are significantly different. The result indicates whether the observed difference could have occurred by random chance.

### 5. Regression Analysis

Regression analysis is used to understand the relationship between dependent and independent variables. It helps in predicting the value of the dependent variable based on the values of the independent variables.

#### Example: Performing a Linear Regression

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

    // Performing a linear regression
    const regressionResult = ss.linearRegression(data);
    console.log('Linear Regression Result:', regressionResult);

    // Using the regression line to predict values
    const regressionLine = ss.linearRegressionLine(regressionResult);
    console.log('Predicted value for x = 6:', regressionLine(6));
</script>
```

**Discussion**:
- **Linear Regression**: Finds the best-fit line for the data points, minimizing the sum of the squared differences between the observed values and the values predicted by the line. The regression result includes the slope and intercept of the line.
- **Prediction**: The regression line can be used to predict the dependent variable for new values of the independent variable.

#### Example: Multiple Linear Regression

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

**Discussion**:
- **Multiple Linear Regression**: Extends simple linear regression to multiple features. It finds the best-fit plane in a multi-dimensional space to predict the dependent variable based on multiple independent variables.
- **Prediction**: The regression model can predict the dependent variable for new data points with multiple features.

### Conclusion

By understanding and using Simple-statistics for statistical analysis, you can perform descriptive statistics, work with probability distributions, conduct hypothesis testing, and perform regression analysis efficiently. These skills are crucial for building sophisticated data-driven applications directly in JavaScript.

### Further Reading
- [Simple-statistics Official Documentation](https://simplestatistics.org/)
- [Simple-statistics GitHub Repository](https://github.com/simple-statistics/simple-statistics)
- [Statistical Functions in Simple-statistics](https://simplestatistics.org/docs/)
- [Hypothesis Testing Overview](https://en.wikipedia.org/wiki/Hypothesis_testing)
- [Linear Regression Analysis](https://en.wikipedia.org/wiki/Linear_regression)

### Additional Examples

To further deepen your understanding, here are additional examples demonstrating more functionalities of Simple-statistics.

#### Example: Correlation Coefficient

**JavaScript**:
```javascript
<script>
    // Sample data
    const x = [1, 2, 3, 4, 5];
    const y = [2, 3, 4, 5, 6];

    // Calculating the Pearson correlation coefficient
    const correlation = ss.sampleCorrelation(x, y);
    console.log('Correlation Coefficient:', correlation);
</script>
```

**Discussion**:
- **Correlation Coefficient**: Measures the strength and direction of the linear relationship between two variables. A value close to 1 indicates a strong positive correlation, while a value close to -1 indicates a strong negative correlation.

#### Example: Standard Deviation and Variance

**JavaScript**:
```javascript
<script>
    // Sample data
    const data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    // Calculating

 standard deviation
    const standardDeviation = ss.standardDeviation(data);
    console.log('Standard Deviation:', standardDeviation);

    // Calculating variance
    const variance = ss.variance(data);
    console.log('Variance:', variance);
</script>
```

**Discussion**:
- **Standard Deviation**: Provides a measure of the dispersion of a dataset relative to its mean. It is the square root of the variance.
- **Variance**: Measures the average degree to which each point differs from the mean. It is the sum of squared differences from the mean, divided by the number of data points.

#### Example: Z-Score

**JavaScript**:
```javascript
<script>
    // Sample data
    const data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
    const value = 5;

    // Calculating the z-score
    const zScore = ss.zScore(data, value);
    console.log('Z-Score for value 5:', zScore);
</script>
```

**Discussion**:
- **Z-Score**: Measures the number of standard deviations a data point is from the mean. A z-score of 0 indicates that the data point is exactly at the mean, while a positive or negative z-score indicates how many standard deviations it is above or below the mean, respectively.

#### Example: Quantile

**JavaScript**:
```javascript
<script>
    // Sample data
    const data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    // Calculating the 25th quantile (first quartile)
    const q25 = ss.quantile(data, 0.25);
    console.log('25th Quantile:', q25);

    // Calculating the 50th quantile (median)
    const q50 = ss.quantile(data, 0.5);
    console.log('50th Quantile (Median):', q50);

    // Calculating the 75th quantile (third quartile)
    const q75 = ss.quantile(data, 0.75);
    console.log('75th Quantile:', q75);
</script>
```

**Discussion**:
- **Quantile**: Divides the data into equal-sized intervals. The 25th quantile (Q1) is the value below which 25% of the data falls, the 50th quantile (Q2) is the median, and the 75th quantile (Q3) is the value below which 75% of the data falls.

### Conclusion

This extended tutorial on Simple-statistics provides a comprehensive guide to performing statistical analysis using JavaScript. By following these examples and discussions, you can enhance your understanding and apply statistical methods to analyze data effectively. These skills are essential for building data-driven applications and making informed decisions based on statistical analysis.

### Further Reading
- [Simple-statistics Official Documentation](https://simplestatistics.org/)
- [Simple-statistics GitHub Repository](https://github.com/simple-statistics/simple-statistics)
- [Statistical Functions in Simple-statistics](https://simplestatistics.org/docs/)
- [Hypothesis Testing Overview](https://en.wikipedia.org/wiki/Hypothesis_testing)
- [Linear Regression Analysis](https://en.wikipedia.org/wiki/Linear_regression)
- [Correlation and Regression](https://stattrek.com/statistics/correlation-regression.aspx)
- [Understanding Z-Scores](https://www.statisticshowto.com/probability-and-statistics/z-score/)
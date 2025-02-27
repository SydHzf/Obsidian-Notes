___
A regression line is a statistical tool used to model the relationship between two quantitative variables. It is a straight line that best fits the data points in a scatter plot, representing the predicted values of the dependent variable based on the independent variable.

### Key Concepts

1. **Dependent Variable (Y)**: The variable you are trying to predict or explain.
2. **Independent Variable (X)**: The variable you are using to make predictions.
3. **Linear Relationship**: Assumes a straight-line relationship between the dependent and independent variables.

### Formula for a Regression Line

The equation of a simple linear regression line is:

\[ Y = \beta_0 + \beta_1 X \]

Where:
- \( Y \) is the predicted value of the dependent variable.
- \( \beta_0 \) is the intercept, the predicted value of \( Y \) when \( X = 0 \).
- \( \beta_1 \) is the slope, representing the change in \( Y \) for a one-unit change in \( X \).

### How to Determine the Regression Line

1. **Calculate the Slope (\( \beta_1 \))**:
   \[
   \beta_1 = \frac{n(\sum XY) - (\sum X)(\sum Y)}{n(\sum X^2) - (\sum X)^2}
   \]
   Where \( n \) is the number of data points.

2. **Calculate the Intercept (\( \beta_0 \))**:
   \[
   \beta_0 = \bar{Y} - \beta_1 \bar{X}
   \]
   Where \( \bar{Y} \) is the mean of the dependent variable and \( \bar{X} \) is the mean of the independent variable.

3. **Form the Regression Equation**:
   Substitute the calculated values of \( \beta_0 \) and \( \beta_1 \) into the regression equation.

### Example

Suppose you have data on the number of hours studied (X) and exam scores (Y) for a group of students:

| Hours Studied (X) | Exam Score (Y) |
|-------------------|----------------|
| 2                 | 50             |
| 3                 | 55             |
| 5                 | 65             |
| 7                 | 70             |
| 8                 | 85             |

### Interpretation

- The slope (\( \beta_1 \)) of 5.19 means that for each additional hour studied, the exam score is predicted to increase by approximately 5.19 points.
- The intercept (\( \beta_0 \)) of 39.05 represents the predicted exam score when no hours are studied.

### How a Regression Line Helps

1. **Prediction**: Allows for the prediction of the dependent variable based on new values of the independent variable.
2. **Relationship Understanding**: Helps in understanding the strength and direction of the relationship between the variables.
3. **Decision Making**: Provides insights for making informed decisions based on the predicted outcomes.
4. **Trend Analysis**: Helps in identifying trends and patterns within the data.

### Conclusion

A regression line is a fundamental tool in statistical analysis that models the relationship between two variables, providing valuable insights for prediction, decision-making, and understanding trends within data. It simplifies complex data relationships into a clear and interpretable linear form.
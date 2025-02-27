Pooled variance is a method used to estimate the common variance of two or more independent samples, assuming that the samples come from populations with the same variance (homogeneity of variance). It is particularly useful in the context of two-sample t-tests when comparing the means of two groups. Pooled variance combines the variances of the samples, weighted by their degrees of freedom, to provide a more accurate estimate of the population variance.

### Formula for Pooled Variance

The pooled variance \( s_p^2 \) is calculated as follows:

\[ s_p^2 = \frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}{n_1 + n_2 - 2} \]

Where:
- \( n_1 \) and \( n_2 \) are the sample sizes of the two groups.
- \( s_1^2 \) and \( s_2^2 \) are the sample variances of the two groups.
- \( n_1 - 1 \) and \( n_2 - 1 \) are the degrees of freedom for each group.

### Steps to Calculate Pooled Variance

1. **Calculate the sample variances** (\( s_1^2 \) and \( s_2^2 \)) for each group.
2. **Multiply each sample variance by its degrees of freedom** (\( n_1 - 1 \) and \( n_2 - 1 \)).
3. **Sum these values**.
4. **Divide by the total degrees of freedom** (\( n_1 + n_2 - 2 \)) to get the pooled variance.

### How Pooled Variance Helps

1. **Two-Sample T-Test**:
   - In a two-sample t-test, pooled variance is used to calculate the standard error of the difference between two means when assuming equal variances. This allows for more precise estimation and comparison of the means.

2. **Increased Statistical Power**:
   - By combining the information from both samples, pooled variance can provide a more stable and reliable estimate of the population variance, leading to more powerful statistical tests.

3. **Simplifies Calculations**:
   - Pooled variance simplifies the process of hypothesis testing when dealing with multiple samples by reducing the need to consider each variance separately.

### Example Scenario

Suppose you are comparing the test scores of students from two different classes to see if there is a significant difference in their performance. You have the following data:

- Class 1: \( n_1 = 30 \), \( \bar{X}_1 = 75 \), \( s_1^2 = 10 \)
- Class 2: \( n_2 = 35 \), \( \bar{X}_2 = 80 \), \( s_2^2 = 15 \)

Calculate the pooled variance:

1. **Compute degrees of freedom**:
   - \( n_1 - 1 = 30 - 1 = 29 \)
   - \( n_2 - 1 = 35 - 1 = 34 \)

2. **Multiply each sample variance by its degrees of freedom**:
   - Class 1: \( 29 \times 10 = 290 \)
   - Class 2: \( 34 \times 15 = 510 \)

3. **Sum these values**:
   - \( 290 + 510 = 800 \)

4. **Divide by the total degrees of freedom**:
   - \( \frac{800}{29 + 34} = \frac{800}{63} \approx 12.70 \)

The pooled variance \( s_p^2 \) is approximately 12.70.

### Using Pooled Variance in a T-Test

With the pooled variance, you can now calculate the standard error of the difference between the two means and perform a two-sample t-test:

\[ \text{SE} = \sqrt{s_p^2 \left( \frac{1}{n_1} + \frac{1}{n_2} \right)} \]

\[ t = \frac{\bar{X}_1 - \bar{X}_2}{\text{SE}} \]

By following these steps, you can determine whether the difference in means is statistically significant.

### Conclusion

Pooled variance is a valuable tool in statistical analysis, especially in hypothesis testing involving multiple samples. It provides a more accurate estimate of the population variance, increases the power of statistical tests, and simplifies the calculations needed to compare group means.
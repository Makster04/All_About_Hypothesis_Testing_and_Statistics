# Conducting T-Tests

## Introduction  
T-tests, using the t-distribution, are used when you don't know the population standard deviation or when you have a small sample size. This method can replace z-tests for hypothesis testing in these situations.

## Objectives  
1. Understand when to use one-sample vs. two-sample t-tests.  
2. Perform a one-sample t-test and make conclusions about an experiment.

## Hypothesis Testing with t-Distribution  
In hypothesis testing, a test statistic is calculated to help decide whether to reject the null hypothesis. The t-test compares two means to determine if their difference is statistically significant.

## One-Sample t-Test  
The one-sample t-test checks if the sample mean differs from a known value (e.g., testing if the mean weight of cakes is 2 pounds). The sample mean is compared against a population mean.

## Two-Sample t-Tests  
- **Paired t-test**: Compares the same group before and after a treatment (e.g., measuring the effect of a new workout routine on weightlifting).
- **Independent t-test**: Compares two different, unrelated groups (e.g., comparing soybean yields in two counties).

## Samples vs. Tails  
- **One-Tail Test**: The alternative hypothesis is directional (e.g., μ < 3 or μ > 3).
- **Two-Tail Test**: The alternative hypothesis is non-directional. Its not equal to the mean. Site A is different than like B. Like Site E is either more or less (e.g., μ ≠ 3).

## Assumptions for T-Tests  
- Sample observations should be numeric and continuous.
- Samples should be independent and from normal distributions.
- For two-sample tests, assume equal variance in the populations (for unpaired tests), and normal distribution of differences (for paired tests).

## Steps for Performing T-Tests  
1. Set up null and alternative hypotheses.  
2. Choose a significance level.  
3. Calculate the test statistic (t-value).  
4. Determine the critical t-value (find rejection region).  
5. Compare the t-value with the critical t-value to decide whether to reject the null hypothesis.

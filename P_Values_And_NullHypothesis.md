# Statistical Hypothesis Testing

## Objectives
You will be able to:

- Describe what it means to "reject the null hypothesis" and how it is related to p-value.
- Identify examples of null and alternative hypotheses, including one-tail and two-tail tests.

## Understanding the Null Hypothesis

As stated previously, scientific experiments actually have 2 hypotheses:

### Null Hypothesis
There is no relationship between A and B.
- **Example**: "There is no relationship between this flu medication and a reduced recovery time from the flu."

The null hypothesis is usually denoted as \( H_0 \).

### Alternative Hypothesis
The hypothesis traditionally thought of when creating a hypothesis for an experiment.
- **Example**: "This flu medication reduces recovery time for the flu."

The alternative hypothesis is usually denoted as \( H_1 \) or \( H_A \).

#### Key Differences:
- The **null hypothesis** is more conservative and assumes no difference between the variables. Mathematically, it always contains an equals sign (e.g., \( = \), \( \leq \), \( \geq \)).
- The **alternative hypothesis** proposes a difference between variables and never contains an equals sign (e.g., \( \neq \), \( > \), \( < \)).

When performing a statistical test, you are determining whether there is enough evidence to reject the null hypothesis. If not, you fail to reject the null hypothesis.

## p-Values and Alpha Values

Statistical tests answer: Is your p-value less than your alpha value?

### p-value
The probability of observing a test statistic at least as large as the one observed, by random chance, assuming the null hypothesis is true.

- If you calculate a p-value of 0.03, it means there's a 3% chance of obtaining the results you're seeing when the null hypothesis is true.

A low p-value suggests that either the null hypothesis is false or that the null hypothesis is true but a highly improbable event occurred. The best practice is to set an alpha prior to the experiment to decide the level of incorrectness you are willing to tolerate.

### Alpha Value (Significance Level)
The marginal threshold where you're okay with rejecting the null hypothesis and accepting the alternative hypothesis as true.

- If you set an alpha value of 0.05, it means you are okay with rejecting the null hypothesis when there is a 5% chance that the result is due to random chance.

#### Decision Rule:
- **Reject the null hypothesis** if \( p \leq \alpha \).
- **Fail to reject the null hypothesis** if \( p > \alpha \).

### Example:
If you set an alpha of 0.05 and your p-value is 0.02, you reject the null hypothesis. If the p-value is 0.06, you fail to reject the null hypothesis.

### Choosing an Alpha Value

The alpha value is commonly set at 0.05 but can be adjusted. Here are some trade-offs:

#### Trade-offs:
- If alpha is too low, you might miss real relationships (Type II error).
- If alpha is too high, you might incorrectly reject the null hypothesis (Type I error).

For example, setting alpha to 0.50 means you would reject the null hypothesis half the time, even when it's true, which is undesirable. Therefore, an alpha of 0.05 is a common standard to avoid false positives while still detecting real effects.

## Null and Alternative Hypothesis Examples

Hypotheses are statements of equality (null hypothesis) and inequality (alternative hypothesis). In statistical tests, these hypotheses must be:

- **Mutually exclusive**: They cannot both be true at the same time.
- **Exhaustive**: They represent all possible outcomes.

### One-Tail vs. Two-Tail Tests

#### One-Tail Test
A one-tailed test looks for a relationship in one direction (greater than or less than).

- **Example**: "The treatment group given this weight loss drug will lose more weight than the control group."

#### Two-Tail Test
A two-tailed test looks for any difference, regardless of direction.

- **Example**: "The treatment group given this weight loss drug will lose a different amount of weight (either more or less) than the control group."

## What Does an Experiment Really Prove?

The null hypothesis is used because experiments cannot definitively prove a relationship between variables. Instead, an experiment argues that the null hypothesis is implausible given the evidence.

Even if you find a statistically significant result, the following could be true:

1. The null hypothesis is true, and you experienced an unlikely event.
2. A confounding variable caused the observed relationship.

Thus, a "successful" experiment is one where you reject the null hypothesis, but it doesn't prove causality.

## The Null Hypothesis Loves You and Wants You To Be Happy

For further reading, check out the article [The Null Hypothesis Loves You and Wants You To Be Happy](https://example.com).

## Summary

In this lesson, you learned about the relationship between p-values and the null hypothesis. This knowledge is foundational for hypothesis testing and understanding linear regression models in future lessons.

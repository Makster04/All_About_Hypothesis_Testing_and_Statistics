# A/B Test Design and Application

## Introduction
- **Objective**: Design and conduct your own A/B tests using statistical techniques.
- **Process**: 
  - State the null hypothesis and alternative hypothesis.
  - Use test statistics for comparison.
  - Example: Compare average purchase prices or blood pressure before and after treatment.
- **Test Design Considerations**: 
  - Multiple comparisons problem.
  - Goodheart’s Law: Measuring everything increases mistakes, and incentivizing measurements can cause unforeseen consequences.
  - This section provides practical application of statistical techniques.

## Objectives
You will be able to:
- List the steps required to design, structure, and run an A/B test.

## Choosing a Metric
- **Start with a given scenario** to determine:
  - Important metrics.
  - Realistically obtainable sample sizes.
  - Consider **Goodheart’s Law** during ongoing tests to optimize performance metrics.

## Defining the Null Hypothesis
- **Null Hypothesis**: A claim the researcher aims to refute.
  - Example: A medical researcher aims to show a new drug is more effective than an old one.
  - Common formulation: “There is no difference between the two drugs.”
- **Proper Formulation**: Use quantitative measurements.
  - Example: "$\text{drug}_a$ lowers blood pressure more than $\text{drug}_b$."
  - Leads to a paired t-test for blood pressure in two groups.
- **Alternative Approach**: 
  - If one drug is more heavily researched, compare it to a predetermined metric (e.g., average drop in blood pressure), which leads to a 1-sample t-test.

## Investigating Power, Effect Size, and Sample Size
- **Key Relationships**: 
  - Power, sample size, and effect size are intimately related.
  - Consider the **cost of sample size**:
    - In online scenarios, it’s easier to run experiments at scale.
    - In medical research, larger sample sizes are costly.
- **Investigation**: Examine these parameters and how they impact experiment design and implementation.

## Summary
- **Research Choices**: 
  - Estimate a parameter or test the validity of a claim.
  - Choose between estimating a population mean or testing a hypothesis.
- **Critical Parameters**:
  - Alpha, beta, and sample size must balance confidence level and practicality.
- **Practice**: In upcoming labs, you’ll practice the setup and workflow for designing and conducting A/B tests in various scenarios.

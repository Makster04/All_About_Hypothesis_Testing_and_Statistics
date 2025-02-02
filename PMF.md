# The Probability Mass Function (PMF)

## Introduction

In this lesson, you'll learn about the Probability Mass Function (PMF), a method used to represent discrete distributions by mapping each value to its probability.

## Objectives

By the end of this lesson, you will be able to:
- Describe how probability is represented in the probability mass function.
- Visualize the PMF and understand its relationship with histograms.

## What is a Probability Mass Function (PMF)?

A Probability Mass Function (PMF), sometimes known as a frequency function, associates probabilities with discrete random variables. Discrete distributions refer to variables with a finite number of possible outcomes. For example, the probability of rolling a specific number on a dice can be described using a PMF.

Formally, a PMF is written as:

f(x) = P(X = x)

python
Copy
Edit

Where:
- `X` is a discrete random variable.
- `R_X = {x1, x2, x3, ...}` represents the set of possible values for `X`.

If you're interested in the probability of a specific outcome `x_k`, it's defined as:

P(x_k) = 1/6

perl
Copy
Edit

## PMF Intuition

Let’s walk through an example of calculating the PMF for a discrete random variable:

1. **Count the frequency of each value**: For a dataset `x = [1,1,1,1,2,2,2,2,3,3,4,5,5]`, you can use the `collections.Counter` in Python:

```python
import collections
x = [1,1,1,1,2,2,2,2,3,3,4,5,5]
counter = collections.Counter(x)
print(counter)
Output:

Counter({1: 4, 2: 4, 3: 2, 5: 2, 4: 1})
Convert frequency to probability: Divide the frequency of each value by the total number of values (13 in this case).
python
Copy
Edit
pmf = []
for key, val in counter.items():
    pmf.append(round(val / len(x), 2))

print(counter.keys(), pmf)
Output:

scss
Copy
Edit
dict_keys([1, 2, 3, 4, 5]) [0.31, 0.31, 0.15, 0.08, 0.15]
Verify normalization: The sum of the PMF should equal 1:
python
Copy
Edit
import numpy as np
np.array(pmf).sum()
Output:

Copy
Edit
1.0
Visualizing a PMF
To visualize a PMF, you can use a bar graph. The following Python code uses matplotlib:

python
Copy
Edit
import matplotlib.pyplot as plt
%matplotlib inline
plt.style.use('ggplot')

outcomes = counter.keys()
plt.bar(outcomes, [p(x_i) for x_i in outcomes])
plt.title("A Probability Mass Function")
plt.xlabel("Outcomes")
plt.ylabel("Probabilities of Outcomes")
This results in a bar graph that shows the probabilities of each outcome. It's similar to a histogram but with normalized probabilities instead of raw frequencies.

You can adjust a histogram to show probabilities by using density=True:

python
Copy
Edit
xtick_locations = range(1, 6)
bins = np.arange(6) + 0.5
plt.hist(x, bins=bins, rwidth=0.25, density=True)
plt.xticks(ticks=xtick_locations)
plt.xlabel('Bins of Outcomes')
plt.ylabel('Probabilities of Bins of Outcomes')
plt.title("Adjusted Histogram with `density=True`")
Why Compare PMF Bar Graph vs. Histogram?
PMF Bar Graph: The PMF bar graph directly shows the probabilities of each categorical outcome, with no binning or normalization required.
Histogram: Histograms are used with continuous data but can be adapted for categorical data. To display probabilities, you need to use density=True.
Measures of Central Tendency and Spread
Expected Value
The expected value (mean) for a discrete distribution is given by:

mathematica
Copy
Edit
E(X) = μ = ∑ p(x_i) * x_i
For example, consider the dataset [2, 5, 5]. The expected value can be computed as:

swift
Copy
Edit
p(2) = 1/3, p(5) = 2/3
E(X) = (1/3 * 2) + (2/3 * 5) = 4
Variance
Variance is calculated using:

mathematica
Copy
Edit
E((X - μ)^2) = σ^2 = ∑ p(x_i) * (x_i - μ)^2
For the dataset [1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 4, 5, 5], we can compute the variance as follows:

python
Copy
Edit
mu = sum([p(x_i) * x_i for x_i in outcomes])
variance = sum([p(x_i) * ((x_i - mu) ** 2) for x_i in outcomes])
Output:

ini
Copy
Edit
mu = 2.46
variance = 1.94
This tells us the expected value is 2.46 and the variance is 1.

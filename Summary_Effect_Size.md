# Summary of "Effect Size"

## Introduction:
Effect size quantifies how large the difference is between two groups. Unlike the p-value, which tells if a difference exists, effect size emphasizes the magnitude of that difference. It’s used across various domains to determine how well an intervention works in different contexts.

## Objectives:
- Distinguish between p-value and effect size in assessing result significance.
- Interpret and identify the limitations of simple effect size.
- Calculate and explain standardized and unstandardized effect sizes.
- Visualize different effect sizes in data distributions.

## P-value vs. Effect Size:
- **P-value**: Indicates whether sample means are statistically different (focus on significance).
- **Effect size**: Shows the magnitude of difference between sample means (focus on practical significance).
  
> **Note**: A large sample can yield a significant p-value even for small differences, while a low-powered study may miss large, important differences.

## Why Data Scientists Need Effect Size
Effect size is crucial in:
- Communicating practical significance.
- Meta-analysis for combining multiple study results to estimate population effect size.
- Power analysis to determine appropriate sample size for detecting true effects.

**Example**: A study on children’s learning times found a 2.7-point difference in comprehension scores between morning and afternoon groups. Without a familiar scale, interpreting the importance of that difference becomes challenging.

## Effect Size Calculation Using Python and SciPy
SciPy provides tools for scientific computing, including calculating effect sizes and creating visualizations. For example:

### Height Difference:
- Males: Mean = 178 cm, SD = 7.7
- Females: Mean = 163 cm, SD = 7.3

Use `scipy.stats.norm()` to create normal distributions and calculate probability density functions (PDFs).

### Example Python Code:
```python

import scipy.stats
import matplotlib.pyplot as plt
import numpy as np

# Male and female height distributions
male_height = scipy.stats.norm(178, 7.7)
female_height = scipy.stats.norm(163, 7.3)

# Evaluate and plot probability density function (PDF)
def evaluate_PDF(rv, x=4):
    mean = rv.mean()
    std = rv.std()
    xs = np.linspace(mean - x*std, mean + x*std, 100)
    ys = rv.pdf(xs)
    return xs, ys

xs, ys = evaluate_PDF(male_height)
plt.plot(xs, ys, label='Male', color='#beaed4')

xs, ys = evaluate_PDF(female_height)
plt.plot(xs, ys, label='Female', color='#fdc086')
plt.xlabel('Height (cm)')
plt.legend()
plt.show()
```

# Simple Effect Size Calculation

The unstandardized effect size is the difference between group means. Use `scipy.stats.rvs()` to generate random samples and calculate their means and standard deviations.


### Example output for male and female samples:
- **Male**: Mean ≈ 177.89 cm, SD ≈ 7.22
- **Female**: Mean ≈ 162.92 cm, SD ≈ 7.26

### Example Python Code:
```python
import scipy.stats
import numpy as np

# Parameters for male and female height distributions
male_mean = 178
male_sd = 7.7
female_mean = 163
female_sd = 7.3

# Generate random samples for males and females
male_samples = scipy.stats.norm(male_mean, male_sd).rvs(1000)
female_samples = scipy.stats.norm(female_mean, female_sd).rvs(1000)

# Calculate means and standard deviations
male_mean_calculated = np.mean(male_samples)
male_sd_calculated = np.std(male_samples)
female_mean_calculated = np.mean(female_samples)
female_sd_calculated = np.std(female_samples)

# Print calculated results
print(f"Male: Mean ≈ {male_mean_calculated:.2f} cm, SD ≈ {male_sd_calculated:.2f}")
print(f"Female: Mean ≈ {female_mean_calculated:.2f} cm, SD ≈ {female_sd_calculated:.2f}")

# Calculate unstandardized effect size (difference in means)
effect_size = male_mean_calculated - female_mean_calculated
print(f"Unstandardized Effect Size (Difference in Means): {effect_size:.2f} cm")
```
### Conclusion:
Effect size provides deeper insight into the practical significance of results, helping researchers and data scientists make better-informed decisions. By combining effect size with visualizations and statistical tools like Python’s SciPy, you can better interpret and communicate your findings.

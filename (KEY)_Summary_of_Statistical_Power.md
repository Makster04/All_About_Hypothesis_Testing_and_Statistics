# Statistical Power

## Introduction

In hypothesis testing, we reject or fail to reject the null hypothesis based on the *p*-value compared to $\alpha$, the probability of a Type I error (False Positive). Power, related to Type II error (False Negative), is the probability of correctly rejecting a false null hypothesis.

## Objectives

You will be able to:

- Define power in relation to *p*-value and null hypothesis.
- Explain how sample size and effect size impact power.
- Perform power calculation using SciPy and Python.
- Simulate and demonstrate the combined effect of sample size and effect size on statistical power.

## The Power of a Statistical Test

Power is the probability of rejecting the null hypothesis when it is false. It ranges from 0 to 1, with 1 being perfect power. Mathematically, $power = 1 - \beta$ (where $\beta$ is the probability of a Type II error).

For a given $\alpha$, you can determine an optimal threshold for rejecting the null hypothesis. However, both $\alpha$ and $\beta$ can't always be minimized due to practical constraints.

## Effect Size

Effect size measures the magnitude of the difference between two groups. Cohen's *d* is commonly used and is calculated as:

$ d = \frac{m_1 - m_2}{s}$

where $m_1$ and $m_2$ are sample means, and $s$ is the standard deviation of the samples.

## Power Analysis

Power depends on three factors: $\alpha$, effect size, and sample size. Visual representations of their effects can deepen understanding. For example, detecting a large difference between two hypotheses (e.g., $H_a = 0.8$ vs $H_0 = 0.5$) increases power.

To calculate effect size, you can use the following Python code:

```python
import numpy as np
import pandas as pd

m1 = .55
m2 = .5
p = m2
rows = []
for n in [10, 20, 50, 500]:
    std = np.sqrt(n*p*(1-p))
    d = (m1*n-m2*n)/std
    rows.append({'Effect_Size': d, 'STD': std, 'Num_observations': n})
print('Hypothetical effect sizes for p(heads)=.55 vs p(heads)=.5')
pd.DataFrame(rows)
```

# Visualizing Power Curves
You can also plot power curves to understand how power changes with sample size and effect size. Use the following code with Statsmodels and Matplotlib:

```python
Copy
Edit
from statsmodels.stats.power import TTestIndPower
import matplotlib.pyplot as plt
import seaborn as sns

power_analysis = TTestIndPower()
power_analysis.plot_power(dep_var='nobs',
                          nobs = np.array(range(5,1500)),
                          effect_size=np.array([.05, .1, .2,.3,.4,.5]),
                          alpha=0.05)
plt.show()
```
As shown, detecting small differences can be difficult, and larger sample sizes can make trivial effects statistically significant.

# Conclusion
Understanding power, effect size, and sample size is essential for designing effective hypothesis tests. Power analysis helps ensure tests are capable of detecting meaningful differences when they exist.

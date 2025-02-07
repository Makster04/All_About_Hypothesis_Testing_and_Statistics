# Hypothesis Testing Guide in Python

### Introduction to Hypothesis Testing
Hypothesis testing is a statistical method used to make inferences or draw conclusions about a population based on sample data. It helps determine whether there is enough evidence to reject a null hypothesis (H₀) in favor of an alternative hypothesis (H₁).

---
## 1. Key Terms and Definitions
- **Null Hypothesis **$(H₀):$** The default assumption or status quo.
- **Alternative Hypothesis **$(H₁):$** The claim we seek evidence for.
- **Significance Level **$(α):$** The probability of rejecting the null hypothesis when it is true (commonly 0.05).
- **Test Statistic:** A standardized value used to decide whether to reject H₀.
- **p-value:** The probability of observing the test results under H₀.
- **Critical Value:** The threshold value that defines the rejection region.
- **Sample Size (n):** The number of observations in the sample.
- **Sample Mean (\( \bar{x} \)):** The average of the sample data.
- **Standard Deviation (s or \( \sigma \)):** A measure of the dispersion of data points around the mean.
- **Margin of Error **$(ME):$** The range within which the true population parameter is expected to lie with a given level of confidence.
- **Cohen's d:** A measure of effect size.
- **Probability Density Function (PDF), Cumulative Distribution Function (CDF), and Probability Mass Function (PMF):** Tools to describe the probability distributions of random variables.

---
## 2. Types of Hypothesis Tests
- **Z-test**
- **T-test** (one-sample, two-sample, paired)
- **Chi-square test**
- **ANOVA (Analysis of Variance)**

---
## 3. Equations and Python Implementation

### a. Sample Size (n)
- **Equation:**
- **$\[
n = \text{number of data points in the sample}
\]$**

**Python Implementation:**
```python
sample = [100, 102, 98, 105, 110, 95, 99, 101, 97]
n = len(sample)
print(f"Sample size: {n}")
```

### b. Sample Mean (\( \bar{x} \))
- **Equation:**
- **$\[
\bar{x} = \frac{\sum x_i}{n}
\]$**

**Python Implementation:**
```python
sample_mean = sum(sample) / n
print(f"Sample mean: {sample_mean:.2f}")
```

### c. Standard Deviation (s)
- **Equation:**
- **$\[
s = \sqrt{\frac{\sum (x_i - \bar{x})^2}{n-1}}
\]$**

**Python Implementation:**
```python
import numpy as np
sample_std = np.std(sample, ddof=1)  # ddof=1 for sample standard deviation
print(f"Sample standard deviation: {sample_std:.2f}")
```

### d. Z-Score
**Equation:**
- **$\[
z = \frac{\bar{x} - \mu}{\frac{\sigma}{\sqrt{n}}}
\]$**

**Python Implementation:**
```python
mu = 100  # Population mean
sigma = 15  # Population standard deviation
z = (sample_mean - mu) / (sigma / np.sqrt(n))
print(f"Z-score: {z:.2f}")
```

### e. Margin of Error (ME)
- **Equation:**
- **$\[
ME = z \times \frac{\sigma}{\sqrt{n}}
\]$**

**Python Implementation:**
```python
z_critical = 1.96  # for 95% confidence level
margin_of_error = z_critical * (sigma / np.sqrt(n))
print(f"Margin of Error: ±{margin_of_error:.2f}")
```

### f. Cohen's d
- **Equation:**
- **$\[
d = \frac{\bar{x}_1 - \bar{x}_2}{s_p} \quad \text{where } s_p \text{ is the pooled standard deviation.}
\]$**

**Python Implementation:**
```python
sample1 = [100, 102, 98, 105, 110]
sample2 = [110, 108, 115, 120, 117]
s1_std = np.std(sample1, ddof=1)
s2_std = np.std(sample2, ddof=1)
pooled_std = np.sqrt(((len(sample1) - 1) * s1_std**2 + (len(sample2) - 1) * s2_std**2) / (len(sample1) + len(sample2) - 2))
cohens_d = (np.mean(sample1) - np.mean(sample2)) / pooled_std
print(f"Cohen's d: {cohens_d:.2f}")
```

### g. Probability Calculations
- **Cumulative Distribution Function (CDF):**
- **$\[
P(X \leq x) = \text{CDF}(x)
\]$**
- **Probability Density Function (PDF):**
- **$\[
P(X = x) = \text{PDF}(x)
\]$**
- **Probability Mass Function (PMF) for Discrete Variables:**
- **$\[
P(X = x) = \text{PMF}(x)
\]$**

**Python Implementation:**
```python
# CDF example
p_cdf = stats.norm.cdf(1.96)  # CDF for standard normal distribution
print(f"CDF at z = 1.96: {p_cdf:.4f}")

# PDF example
p_pdf = stats.norm.pdf(0)  # PDF for standard normal distribution at z = 0
print(f"PDF at z = 0: {p_pdf:.4f}")

# PMF example (for discrete distribution)
k = 3
n = 10
p = 0.5  # Probability of success in a binomial distribution
p_pmf = stats.binom.pmf(k, n, p)
print(f"PMF for k = {k} successes in {n} trials: {p_pmf:.4f}")
```

---
## 4. Decision Rules
- If **p-value < α**, reject the null hypothesis (H₀).
- If **p-value ≥ α**, fail to reject the null hypothesis.

---
## 5. Summary Table
| Test        | Purpose                              | Test Statistic | Python Function              |
|-------------|--------------------------------------|----------------|-----------------------------|
| Z-test      | Test population mean (large samples) | z              | `stats.norm.cdf`            |
| One-sample T-test | Test sample mean (small samples) | t              | `stats.ttest_1samp`         |
| Two-sample T-test | Compare means of two samples     | t              | `stats.ttest_ind`           |
| Chi-square  | Test categorical data independence   | χ²             | `stats.chisquare`           |
| ANOVA       | Compare means across multiple groups| F              | `stats.f_oneway`            |
| CDF         | Cumulative probability               | —              | `stats.norm.cdf`            |
| PDF         | Probability density for continuous   | —              | `stats.norm.pdf`            |
| PMF         | Probability for discrete variables   | —              | `stats.binom.pmf`           |

---
## Conclusion
Hypothesis testing is an essential part of statistical analysis. Using Python’s `scipy` and `numpy` libraries, we can implement various hypothesis tests to draw meaningful conclusions from data.

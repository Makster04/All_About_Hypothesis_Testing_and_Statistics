# Hypothesis Testing: Key Concepts and Python Implementations

## Key Concepts in Hypothesis Testing

1. **Null and Alternative Hypotheses**  
   - **Null Hypothesis (H₀)**: Statement of no effect, no difference, or no relationship. It is the hypothesis that is tested.  
   - **Alternative Hypothesis (H₁ or Ha)**: Contradicts the null hypothesis, indicating there is an effect, difference, or relationship.  

2. **Test Statistic**  
   A value calculated from sample data to determine whether the null hypothesis can be rejected. The type of test statistic depends on the hypothesis test (e.g., t-test, z-test, chi-square test).  

3. **Significance Level (α)**  
   The probability threshold for rejecting the null hypothesis, commonly set at 0.05. If the p-value is less than α, you reject the null hypothesis.  

4. **P-Value**  
   The probability of observing the sample data (or more extreme) assuming that the null hypothesis is true. A p-value less than the significance level indicates strong evidence against the null hypothesis.  

5. **Type I and Type II Errors**  
   - **Type I Error (False Positive)**: Rejecting the null hypothesis when it is actually true.  
   - **Type II Error (False Negative)**: Failing to reject the null hypothesis when it is actually false.  

6. **Power of a Test**  
   The probability of correctly rejecting a false null hypothesis (i.e., detecting a true effect). Power increases with sample size and effect size.  

7. **One-Tailed vs. Two-Tailed Tests**  
   - **One-Tailed Test**: Tests for an effect in one direction (e.g., greater than or less than).  
   - **Two-Tailed Test**: Tests for an effect in both directions (e.g., not equal to).  

8. **Sample Size**  
   A larger sample size provides more reliable results, reducing standard error and increasing the power of the test.  

9. **Assumptions**  
   Each hypothesis test has certain assumptions (e.g., normality, independence, homogeneity of variance) that need to be checked. Violating these assumptions can lead to incorrect conclusions.  

10. **Confidence Intervals**  
   Confidence intervals provide a range of values within which the true population parameter is likely to fall. A 95% confidence interval corresponds to rejecting the null hypothesis if the population parameter falls outside the interval.  

11. **Effect Size**  
   Effect size measures the strength of the relationship or difference, giving practical significance to the result alongside the p-value.  

---

## Important Equations and Python Implementations

### 1. Z-Test (for Population Mean)
**Equation:**  
\[ Z = \frac{X - \mu}{\sigma / \sqrt{n}} \]  
Where:  
- \( X \) = sample mean  
- \( \mu \) = population mean  
- \( \sigma \) = population standard deviation  
- \( n \) = sample size  

**Python Code:**
```python
from scipy import stats
import numpy as np

sample_data = np.array([100, 102, 105, 98, 101])  # Sample data
population_mean = 100
population_std = 5
sample_size = len(sample_data)

sample_mean = np.mean(sample_data)
z_score = (sample_mean - population_mean) / (population_std / np.sqrt(sample_size))
p_value = 2 * (1 - stats.norm.cdf(abs(z_score)))  # Two-tailed test

print(f"Z-score: {z_score}, P-value: {p_value}")



# Statistical Tests and Python Implementations  

### 2. T-Test (for Population Mean)  

**Equation:**  
\[
t = \frac{X - \mu}{\frac{s}{\sqrt{n}}}
\]  

Where:  
- **\( X \)** = sample mean  
- **\( \mu \)** = population mean  
- **\( s \)** = sample standard deviation  
- **\( n \)** = sample size  

**Python Code:**  

```python
from scipy import stats
import numpy as np

sample_data = np.array([100, 102, 105, 98, 101])
population_mean = 100

t_stat, p_value = stats.ttest_1samp(sample_data, population_mean)
print(f"T-statistic: {t_stat}, P-value: {p_value}")
```  

---

### 3. Chi-Square Test (for Independence)  

**Equation:**  
\[
\chi^2 = \sum \frac{(O - E)^2}{E}
\]  

Where:  
- **\( O \)** = observed frequency  
- **\( E \)** = expected frequency  

**Python Code:**  

```python
from scipy.stats import chi2_contingency
import numpy as np

observed = np.array([[30, 10], [20, 40]])

chi2_stat, p_value, dof, expected = chi2_contingency(observed)
print(f"Chi-square statistic: {chi2_stat}, P-value: {p_value}")
```  

---

### 4. One-Way ANOVA (for Comparing Means)  

**Python Code:**  

```python
from scipy import stats

group1 = [23, 21, 22, 23, 24]
group2 = [30, 29, 31, 32, 30]
group3 = [18, 17, 19, 16, 20]

f_stat, p_value = stats.f_oneway(group1, group2, group3)
print(f"F-statistic: {f_stat}, P-value: {p_value}")
```  

---

### 5. Effect Size (Cohen's d)  

**Equation for Cohen's d:**  
\[
d = \frac{M_1 - M_2}{\sigma_p}
\]  
Where:  
- **\( M_1 \)** and **\( M_2 \)** = means of two groups  
- **\( \sigma_p \)** = pooled standard deviation  

**Python Code:**  

```python
import numpy as np

group1 = np.array([23, 21, 22, 23, 24])
group2 = np.array([30, 29, 31, 32, 30])

mean1, mean2 = np.mean(group1), np.mean(group2)
std1, std2 = np.std(group1, ddof=1), np.std(group2, ddof=1)
n1, n2 = len(group1), len(group2)

pooled_std = np.sqrt(((n1 - 1) * std1**2 + (n2 - 1) * std2**2) / (n1 + n2 - 2))
cohen_d = (mean1 - mean2) / pooled_std

print(f"Cohen's d: {cohen_d}")
```  

---


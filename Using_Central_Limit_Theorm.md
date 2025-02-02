# Understanding Central Limit Theorm:
### 1. Definition:
The CLT states that regardless of the original population's distribution, the distribution of sample means from repeated sampling will approach a normal distribution as the sample size increases. This holds true if the sample size is large enough (typically n ≥ 30).

### 2. Key Points of CLT:
- **- Sample Means:** Focuses on the means of samples, not the raw data.
- **- Sufficient Sample Size:** Sample size (n) needs to be large enough for the theorem to apply (n ≥ 30).
- **- Population Distribution Doesn't Matter:** Works even if the original population is not normal.
- **- Sampling Distribution Mean and Standard Deviation:** The mean of the sample means approximates the population mean, and the standard deviation (standard error) is the population’s standard deviation divided by √n.

### 3. Importance of CLT:
Simplifies Inferences: CLT allows for normal distribution approximations, enabling statistical tests and confidence intervals even when the original data isn’t normally distributed.
Facilitates Hypothesis Testing: It makes it possible to apply tests like Z-tests and T-tests, which require normality in the sampling distribution.

# THE LAB
[The Actual Lab](https://github.com/Makster04/dsc-central-limit-theorem-lab.git)

# Python Examples
``` python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import skewnorm

# Step 1: Generate a Skewed Population
np.random.seed(42)
population = skewnorm.rvs(a=10, loc=100, scale=20, size=10000)  # Right-skewed distribution

# Step 2: Define Sampling Parameters
sample_size = 50  # Sample size per iteration
num_samples = 1000  # Number of samples

# Step 3: Generate Sample Means
sample_means = [np.mean(np.random.choice(population, sample_size, replace=True)) for _ in range(num_samples)]

# Step 4: Compute Theoretical CLT Parameters
pop_mean = np.mean(population)
pop_std = np.std(population, ddof=1)
standard_error = pop_std / np.sqrt(sample_size)

# Step 5: Plot the Population Distribution
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
sns.histplot(population, bins=50, kde=True, color='red')
plt.axvline(pop_mean, color='black', linestyle='dashed', label=f"Mean: {pop_mean:.2f}")
plt.title("Original Skewed Population")
plt.xlabel("Value")
plt.ylabel("Frequency")
plt.legend()

# Step 6: Plot the Sampling Distribution of Sample Means
plt.subplot(1, 2, 2)
sns.histplot(sample_means, bins=30, kde=True, color='blue')
plt.axvline(np.mean(sample_means), color='red', linestyle='dashed', label=f"Mean: {np.mean(sample_means):.2f}")
plt.title("Sampling Distribution of Sample Means (CLT)")
plt.xlabel("Sample Mean")
plt.ylabel("Frequency")
plt.legend()

plt.tight_layout()
plt.show()

# Step 7: Print Theoretical vs. Observed Standard Error
print(f"Population Mean (μ): {pop_mean:.2f}")
print(f"Sample Mean (X̄) Mean: {np.mean(sample_means):.2f}")
print(f"Population Standard Deviation (σ): {pop_std:.2f}")
print(f"Theoretical Standard Error (σ/√n): {standard_error:.2f}")
print(f"Observed Standard Deviation of Sample Means: {np.std(sample_means, ddof=1):.2f}")

```

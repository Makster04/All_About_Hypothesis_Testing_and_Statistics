# Examples for Questions in the CLT Lab:
[The Actual Lab](https://github.com/Makster04/dsc-central-limit-theorem-lab.git)

## 1. Check if Normally Distributed
``` python
import matplotlib.pyplot as plt
import scipy.stats as stats

Distribution_Test = stats.normaltest(DF)
print(Distribution_Test)
```
## 2. Sampling With Replacment
This is when we repeatedly draw samples from a population, with each sample being independent and with the possibility of sampling the same individual more than once.
``` python
import numpy as np
import matplotlib.pyplot as plt

# Population: Normally distributed data
population = np.random.normal(loc=50, scale=15, size=10000)

# Sample size
sample_size = 100
num_samples = 1000

# Sampling with replacement
samples = [np.random.choice(population, size=sample_size, replace=True) for _ in range(num_samples)]

# Show a few sample means
sample_means = [np.mean(sample) for sample in samples]

# Plot the sample means
plt.hist(sample_means, bins=30, edgecolor='black', alpha=0.7)
plt.title('Sampling Distribution of Sample Means')
plt.xlabel('Sample Mean')
plt.ylabel('Frequency')
plt.show()
```

## Generating a Sample Mean
This involves computing the mean of a sample drawn from the population. This is done repeatedly to approximate the sample mean distribution.
``` python
# Generate a single sample
sample = np.random.choice(population, size=sample_size, replace=True)

# Compute the sample mean
sample_mean = np.mean(sample)
print(f'Sample Mean: {sample_mean}')
```

## Creating a Sampling Distribution of Sample Means
We generate multiple samples and calculate the mean of each sample. The distribution of those means will approximate a normal distribution according to the Central Limit Theorem (CLT).
``` python
# Create a sampling distribution of sample means
sample_means = [np.mean(np.random.choice(population, size=sample_size, replace=True)) for _ in range(num_samples)]

# Plot the sampling distribution
plt.hist(sample_means, bins=30, edgecolor='black', alpha=0.7)
plt.title('Sampling Distribution of Sample Means (CLT)')
plt.xlabel('Sample Mean')
plt.ylabel('Frequency')
plt.show()

# Print the overall mean and standard deviation of the sample means
print(f'Mean of sample means: {np.mean(sample_means)}')
print(f'Standard deviation of sample means: {np.std(sample_means)}')
```
### Explanation:
- **- Sampling with replacement:** We use np.random.choice to draw random samples from the population, allowing repeats (i.e., sampling with replacement).
- **- Sample mean:** For each sample, we calculate the mean using np.mean.
- **- Sampling distribution of sample means:** We collect a large number of sample means and plot their distribution. According to the CLT, this distribution should approach a normal distribution, even if the original population isn't normal, as the sample size increases.

## Furthermore
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

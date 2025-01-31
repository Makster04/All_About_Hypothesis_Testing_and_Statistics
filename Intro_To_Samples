# **Statistical Analysis and Summary of "Introduction to Sampling"**

## **Python Code for Sampling Analysis**
```python
import numpy as np

# Given population ages (Titanic dataset example, simulated)
population_ages = np.random.randint(1, 100, 1000)  # Simulating a population of 1000 ages

# Population Mean (μ) - The actual mean age of the entire dataset
population_mean = np.mean(population_ages)

# Population Standard Deviation (σ) - The actual dispersion of ages in the population
population_std = np.std(population_ages)

# Taking a sample of 50 from the population
sample_size = 50
sample = np.random.choice(population_ages, sample_size, replace=False)

# Sample Mean (x̄) - The estimated mean age from the sample
sample_mean = np.mean(sample)

# Sample Standard Deviation (s) - The estimated dispersion from the sample
sample_std = np.std(sample, ddof=1)  # ddof=1 ensures we use the sample standard deviation formula

# Percentage error in sample mean estimation
error_percentage = abs((sample_mean - population_mean) / population_mean) * 100

# Running multiple samples (5 & 10,000 trials) to see variability in estimates
num_trials = 10000
sample_means = [np.mean(np.random.choice(population_ages, sample_size, replace=False)) for _ in range(num_trials)]

# Mean and Standard Deviation of Sample Means
mean_of_sample_means = np.mean(sample_means)
std_of_sample_means = np.std(sample_means)

# Output results
population_mean, sample_mean, error_percentage, mean_of_sample_means, std_of_sample_means

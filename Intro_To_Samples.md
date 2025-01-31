# **Statistical Analysis and Summary of "Introduction to Sampling"**
# **Introduction to Sampling**

## **Introduction**
Sampling is essential for making statistical inferences about a population when collecting complete data (a census) is impractical. By analyzing samples, data scientists estimate population statistics.

## **Objectives**
- Understand how samples help in population insights.
- Differentiate between a **census** (full population data) and a **sample** (subset).
- Use statistical measures (**mean**, **standard deviation**) to infer population parameters.

## **Key Concepts**
### **Census vs. Sample**
- A **census** surveys an entire population.  
- A **sample** is a subset used to estimate population statistics.  

### **Connections to Set Theory**
- The **population** is the **universal set**.  
- A **sample** is a **subset** of the population.

### **Descriptive Statistics**
- **Mean**:  
  - **Population Mean (μ)** vs. **Sample Mean (x̄)**  
- **Standard Deviation**:  
  - **Population Standard Deviation (σ)** vs. **Sample Standard Deviation (s)**  
- **Sample Size**:  
  - **Population Size (N)** vs. **Sample Size (n)**  

---

## **Case Study: Estimating Mean Age Using Titanic Dataset**
1. **Population Mean**: Calculated directly since full data is available.  
2. **Sample Mean**: A random sample of **50** gives an estimate.  
3. **Error Calculation**: Sample mean is **~6% off** from the population mean.  
4. **Multiple Samples (5 & 10,000 trials)**: Variability in estimates shows expected deviations.  

---

## **Conclusion**
Sampling allows estimation of population characteristics despite limitations, with statistical methods helping measure **accuracy** and **reliability**.  
This analysis demonstrates the **Law of Large Numbers**, showing that as more samples are taken, the **mean of the sample means** converges to the **true population mean**.

---

# **Python Code for Sampling Analysis**
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

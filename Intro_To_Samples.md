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
1. Importing Data and Calculating Population Mean
``` python
python
Copy
Edit
import pandas as pd
import numpy as np

# Load Titanic dataset
df = pd.read_csv('titanic.csv', index_col=0)
df
```

2. Calculating the Population Mean
``` python
python
Copy
Edit
# Calculate the population mean for the age column
population_mean = df.Age.mean()
print(population_mean)
```

3. Sampling and Calculating Sample Mean
```python
# Take a sample of 50 people
sample = df.sample(n=50, random_state=22)

# Calculate the sample mean
sample_mean = sample.Age.mean()
print(sample_mean)
```

4. Calculating Percent Error
``` python
# Find the difference between the sample and population means
err = np.abs(sample_mean - population_mean)

# Calculate the percent error
per_err = err / population_mean
print(per_err)
```

5. Simulating Five Separate Data Collection Processes
``` python
# Simulate five separate samples
five_sample_means = []
for i in range(5):
    sample = df.sample(n=50, random_state=i+100)
    five_sample_means.append(sample.Age.mean())

print(five_sample_means)
```

6. Calculating Errors for Five Samples

``` python
# Calculate errors for the five samples
five_sample_errors = [np.abs(sample_mean - population_mean) / population_mean for sample_mean in five_sample_means]
print(five_sample_errors)
```

7. Visualizing Five Sample Means
   
``` python
import matplotlib.pyplot as plt
import seaborn as sns
from matplotlib.lines import Line2D

# Plotting the bar chart for five sample means
x_labels = [f"Sample {x}" for x in range(1, 6)]

fig, ax = plt.subplots(figsize=(7,6))

ax.bar(x_labels, five_sample_means)
ax.set_ylabel("Mean Age")
ax.axhline(y=population_mean, color="red", linewidth=5, linestyle="--")
ax.legend(
    handles=[Line2D([0], [0], color="red", linestyle="--")],
    labels=["True Population Mean"],
    fontsize="large"
)
plt.show()
```

8. Simulating 10,000 Samples
```python
# Simulate 10,000 samples
sample_means = []
for i in range(10**4):
    sample = df.sample(n=50, random_state=i)
    sample_means.append(sample.Age.mean())

print(len(sample_means))
```
9. Visualizing the Distribution of Sample Means

```python
# Plotting the histogram for the distribution of sample means
fig, ax = plt.subplots(figsize=(8,6))

ax.hist(sample_means, bins="auto")
ax.set_xlabel("Mean Age")
ax.set_ylabel("Count of Samples")
ax.axvline(x=population_mean, color="red", linewidth=5, linestyle="--")
ax.legend(
    handles=[Line2D([0], [0], color="white", marker="|", markersize=15, markeredgewidth=1.5, markeredgecolor="red")],
    labels=["True Population Mean"],
    fontsize="large"
)
plt.show()
```

10. Calculating the Mean of Sample Means
```python
# Calculate the mean of sample means
ten_thousand_samples_mean = np.mean(sample_means)
print(ten_thousand_samples_mean)
```

11. Calculating Accuracy of Sample Mean Estimate
```python
# Calculate the accuracy of the sample means
err = np.abs(ten_thousand_samples_mean - population_mean) / population_mean
accuracy = 1 - err
print(accuracy)
```

# OTHER Codings
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

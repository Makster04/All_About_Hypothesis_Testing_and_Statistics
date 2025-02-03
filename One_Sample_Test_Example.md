### 1. Define the Function
```python
def one_sample_ttest(sample, popmean, alpha):
    
    # Visualize sample distribution for normality 
    sns.histplot(sample, kde=True, bins=5, color='darkblue')

    # Population mean 
    mu = popmean
    
    # Sample mean (x̄) using NumPy mean()
    x_bar = np.mean(sample)

    # Sample Standard Deviation (sigma) using Numpy
    sigma = np.std(sample, ddof=1)

    # Degrees of freedom
    n = len(sample)
    df = n - 1
    
    # Calculate the critical t-value
    t_crit = stats.t.ppf(1 - alpha, df)
    
    # Calculate the t-value and p-value      
    t_value = (x_bar - mu) / (sigma / np.sqrt(n))
    
    p_value = 2 * (1 - stats.t.cdf(abs(t_value), df))
    
    # Return results
    print(t_value, p_value, t_crit)
```

### 2. Solutions 
1. Test to see if the sample mean is significantly different from 65 at the .05 level. Report the t- and p-values. Use the function you made above.
```python
Report = [84.0, 92.4, 74.3, 79.4, 86.7, 75.3, 90.9, 86.1, 81.0, 85.1, 78.7, 73.5, 86.9, 87.4, 82.7, 81.9, 69.9, 77.2, 79.3, 83.3]
one_sample_ttest(Report, popmean=65, alpha= 0.05)

# Output: 12.687592157174493 1.0053358145967195e-10 1.729132811521367
```
2. The researcher realizes that she accidentally recorded the score that should have been 80.9 as 90.9. Are these corrected scores significantly different from 65 at the .05 level?
```python
Report = [84.0, 92.4, 74.3, 79.4, 86.7, 75.3, 80.9, 86.1, 81.0, 85.1, 78.7, 73.5, 86.9, 87.4, 82.7, 81.9, 69.9, 77.2, 79.3, 83.3]
one_sample_ttest(Report, popmean=65, alpha= 0.05)

# Output: 13.202088288314906 5.083378162851204e-11 1.729132811521367
```

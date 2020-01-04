[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

### Compute the median, mean, skewness and Pearson’s skewness of the resulting sample.

```python
def mySkewness(xs):
    mean = xs.mean()
    variance = sum((x - mean)**2 for x in xs) / len(xs)
    stnd_dev = np.sqrt(variance)

    cent_moment = sum((x - mean)**3 for x in xs) / len(xs)
    return cent_moment / stnd_dev**3


def myPearsonSkewness(xs):
    mean = xs.mean()
    median = thinkstats2.Cdf(xs).Value(0.5)
    variance = sum((x - mean)**2 for x in xs) / len(xs)
    stnd_dev = np.sqrt(variance)

    return 3 * (mean - median) / stnd_dev

mean = sample.mean()
median = cdf.Value(0.5)
skewness = mySkewness(sample)
pearsons = myPearsonSkewness(sample)


print('Mean:', mean)
print('Median:', median)
print('Skewness:', skewness)
print('Pearsons:', pearsons)
```
Results:
- Mean: 74278.7075311872
- Median: 51226.45447894046
- Skewness: 4.949920244429587
- Pearsons: 0.7361258019141741

### What fraction of households report a taxable income below the mean?

```python
cdf.Prob(sample.mean())
```
2/3 of the population has an income below the mean

### How do the results depend on the assumed upper bound?

```python
new_log_sample = InterpolateSample(income_df, log_upper=7.0)
new_sample = np.power(10, new_log_sample)

new_mean = new_sample.mean()
new_cdf = thinkstats2.Cdf(new_sample)
new_median = new_cdf.Value(0.5)
new_skewness = mySkewness(new_sample)
new_pearsons = myPearsonSkewness(new_sample)


print('Mean:', new_mean)
print('Median:', new_median)
print('Skewness:', new_skewness)
print('Pearsons:', new_pearsons)
```
Results:
- Mean: 124267.39722164697
- Median: 51226.45447894046
- Skewness: 11.603690267537793
- Pearsons: 0.3915645092774215

The higher upper bound increases the mean of the distribution pretty dramatically. Now 85% of people have an income below the mean. The skewness measure also increases as expected. Counter intuitively, the Person's metric decreases. I suppose the explanation is that the deviation inreases more than the different between the mean and median.

I see how this is less affected by outliers but it also seems like a weakness of the measurement. The only thing that changed was the length of the tail which is the definition of skew. Therefore, I would expect a measurement of skew to increase.


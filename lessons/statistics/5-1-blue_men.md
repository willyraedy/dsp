[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

```python
lower_bound = ((5 * 12) + 10) * 2.54
upper_bound = ((6 * 12) + 1) * 2.54

dist.cdf(upper_bound) - dist.cdf(lower_bound)
```

34.3% of men are between 5'10" and 6'1"

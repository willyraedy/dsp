[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

```python
rand_list = np.random.random(1000)
thinkplot.Pmf(thinkstats2.Pmf(rand_list))
thinkplot.Cdf(thinkstats2.Cdf(rand_list))
```

When you plot the pmf, the graph is very difficult to read. No values repeated so every value has a probability of 1/1000th. It's not perfectly uniform because there are gaps in the range but with 1000 data points it's nearly impossible to see them. The CDF is almost linear which also indicates it's nearly uniform.

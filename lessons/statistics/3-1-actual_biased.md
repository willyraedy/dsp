[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

1) Make pmf of actual data
```python
resp = nsfg.ReadFemResp()
pmf = thinkstats2.Pmf(resp.numkdhh, label='actual')
```
2) Bias data and make pmf
```python
pmf_biased = pmf.Copy(label='biased')
for num_kids, num_of_observations in pmf_biased.Items():
    pmf_biased.Mult(num_kids, num_kids)
pmf_biased.Normalize()
```
3) Plot pmfs
```python
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, pmf_biased])
thinkplot.Config(xlabel='Number of Children', ylabel='PMF')
```
4) Calculate means
```python
actual_mean = pmf.Mean()
biased_mean = pmf_biased.Mean()
diff = actual_mean - biased_mean
```

Resulting means:

- Actual: 1.024205155043831
- Sample: 2.403679100664282
- Diff: -1.3794739456204512

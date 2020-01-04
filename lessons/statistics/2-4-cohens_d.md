[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```python
def myCohenEffectSize(group1, group2):
    weighted_var = (len(group1) * group1.var() + len(group2) * group2.var()) / (len(group1) + len(group2))
    return (group1.mean() - group2.mean()) / np.sqrt(weighted_var)

cohen_wgt = myCohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)

# Validate
cohen_wgt == CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
```

The value of Cohen's effect size for pregnancy length was 0.029. The value for total weight is roughly three times in magnitude and in the opposite direction (-0.089). So, by this measure, non-first babies are heavier than first babies. However, less than 1/10th of a deviation is still very small. In reality, in both cases this difference is likely not noticable or meaningful.

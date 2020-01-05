[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

> Using the variable `totalwgt_lb`, investigate whether first babies are lighter or heavier than others. Use Cohen's _d_ to quantufy the difference between the groups.

I started by extracting the `totalwgt_lb` attribte from each group:
```python
# Loading the data
preg = nsfg.ReadFemPreg()

# Separating the groups
live = preg[preg.outcome == 1]
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

# Getting the "totalwgt_lb" attribute from each
first_total = firsts.totalwgt_lb
other_total = others.totalwgt_lb
```
The mean for each group is as follows

| birth-order | mean |
|-------|------|
| first | 7.201094430437772| 
| not first | 7.325855614973262 |

Then I calculated Cohen's _d_...

```python
"""
cohen's d = (mean1 - mean2) / pooled_sd
"""
first_mean = first_total.mean()
other_mean = other_total.mean()
mean_diff = first_mean - other_mean

first_var = first_total.var()
other_var = other_total.var()
n1, n2 = len(first_total), len(other_total)
total_var = (first_var * n1 + other_var * n2) / (n1 + n2)

cohen_d = mean_diff / (total_var ** (1/2))

```

The resulting value is: `-0.088672927072602`

This shows that the average weight of fist babies is less than that of other babies but that the effect is very small.

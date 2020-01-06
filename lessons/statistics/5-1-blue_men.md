[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

> Height distribution is roughly normal with µ = 178 cm and σ = 7.7 cm for men, and µ = 163 cm and σ = 7.3 cm for women. In order to join Blue Man Group, you have to be a man between 5'10" and 6'1". What percentage of the US male population is in this range?


Create the distribution

```python
import scipy.stats

mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
```

Convert the height range's start and end values from ft+in to cm

```python
start = 2.54 * (5 * 12 + 10)
end = 2.54 * (6 * 12 + 1)
```

then find the percentage below the starting point and below the end point and take the difference, to find the answer...

```python
cdf_start = dist.cdf(start)
cdf_end = dist.cdf(end)

result = cdf_end - cdf_start # 0.34274683763147457
```

The answer is that about 34.27% of U.S. males are eligable to join Blue Man Group.


[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> 
import scipy.stats
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
type(dist)

dist.mean(), dist.std()

#5'10" = 177.8
#6'1"=185.42
#How many people are between 5'10" and 6'1"?
high=dist.cdf(185.42)
low=dist.cdf(177.8)
(high, low, high-low)

#ANS: 34.275% of U.S. male is in the range between 5'10" and 6'1" 

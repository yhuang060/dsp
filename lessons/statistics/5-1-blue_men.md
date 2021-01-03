[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters μ = 178 cm and σ = 7.7 cm for men, and μ = 163 cm and σ = 7.3 cm for women.
In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.


import scipy.stats<br/>
mu = 178<br/>
sigma = 7.7<br/>
dist = scipy.stats.norm(loc=mu, scale=sigma)<br/>
type(dist)<br/>

dist.mean(), dist.std()<br/>

#5'10" = 177.8<br/>
#6'1"=185.42<br/>
#How many people are between 5'10" and 6'1"?<br/>
high=dist.cdf(185.42)<br/>
low=dist.cdf(177.8)<br/>
(high, low, high-low)<br/>

#ANS: 34.275% of U.S. male is in the range between 5'10" and 6'1" 

[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> Exercise 2   The numbers generated by random.random are supposed to be uniform between 0 and 1; that is, every value in the range should have the same probability.
Generate 1000 numbers from random.random and plot their PMF and CDF. Is the distribution uniform?

t=np.random.random(1000) <br/>
pmf = thinkstats2.Pmf(t)<br/>
thinkplot.Pmf(pmf, linewidth=0.1)<br/>
thinkplot.Config(xlabel='Random variate', ylabel='PMF')<br/>

cdf = thinkstats2.Cdf(t)<br/>
thinkplot.Cdf(cdf)<br/>
thinkplot.Config(xlabel='Random variate', ylabel='CDF')<br/>

Yes, it is distribution uniform. <br/>

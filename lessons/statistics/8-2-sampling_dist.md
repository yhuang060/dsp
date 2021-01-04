[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

>>Suppose you draw a sample with size n=10 from an exponential distribution with λ=2. Simulate this experiment 1000 times and plot the sampling distribution of the estimate L. Compute the standard error of the estimate and the 90% confidence interval.
Repeat the experiment with a few different values of n and make a plot of standard error versus n.

    def sample_exp_mean(n=10, m=1000, lam=2):
        means=[]
        for _ in range(m):
            xs=np.random.exponential(1/lam, n)
            L=1/np.mean(xs)
            means.append(L)
        return means    


    means=sample_exp_mean(10,1000)
    std_error= RMSE(means, 2)
    cdf=thinkstats2.Cdf(means)
    ci=cdf.Percentile(5), cdf.Percentile(95)

    print("Standard Error: ", std_error) #Standard Error:  0.8106348190231175
    print("confidence interval: ", ci) #confidence interval:  (1.24274996792899, 3.6820216616804102)

    # plot the CDF
    thinkplot.Cdf(cdf)
    thinkplot.Config(xlabel='estimate',
                         ylabel='CDF',
                         title='Sampling distribution')
    #-----------------------------------------------------------
        means_diff_n=[]
        x=range(10,100,10)
        std_err=[]
        for n in range(10,100,10):
            m=sample_exp_mean(n, 1000)
            means_diff_n.append(m)
            std_err.append(RMSE(m, 2))


        thinkplot.Plot(x, std_err) 
        thinkplot.Config(xlabel='n',ylabel='STD Error')

#Conclusions
1) with sample size 10:
Standard Error:  0.8106348190231175
confidence interval:  (1.24274996792899, 3.6820216616804102)
2) As sample size increases, standard error and the width of the CI decrease.

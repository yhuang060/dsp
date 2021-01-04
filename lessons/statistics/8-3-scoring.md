[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

---

>> Exercise 8.3 In games like hockey and soccer, the time between goals is roughly exponential. So you could estimate a team’s goal-scoring rate by observing the number of goals they score in a game. This estimation process is a little different from sampling the time between goals, so let’s see how it works.
Write a function that takes a goal-scoring rate, lam, in goals per game, and simulates a game by generating the time between goals until the total time exceeds 1 game, then returns the number of goals scored.
Write another function that simulates many games, stores the estimates of lam, then computes their mean error and RMSE.
Is this way of making an estimate biased? Plot the sampling distribution of the estimates and the 90% confidence interval. What is the standard error? What happens to sampling error for increasing values of lam?
---
    def SimulateGame(lam):
        """Simulates a game and returns the estimated goal-scoring rate.

        lam: actual goal scoring rate in goals per game
        """
        goals = 0
        t = 0
        while True:
            time_between_goals = random.expovariate(lam)
            t += time_between_goals
            if t > 1:
                break
            goals += 1

        # estimated goal-scoring rate is the actual number of goals scored
        L = goals
        return L

    def SimulateManyGames(lam=2,n=1000000):
        """Simulates a game and returns the estimated goal-scoring rate.

        lam: actual goal scoring rate in goals per game
        """
        estimate=[]
        for _ in range(n):
            L=SimulateGame(lam)
            estimate.append(L)

        print("RMSE L: ", RMSE(estimate, lam))
        print('mean error L: ', MeanError(estimate, lam))

        pmf = thinkstats2.Pmf(estimate)
        thinkplot.Hist(pmf)
        thinkplot.Config(xlabel='Goals scored', ylabel='PMF')


    SimulateManyGames(2,1000000)
    #RMSE L:  1.4145030929623308
    #mean error L:  0.001939
    
    #Conclusions:
    # 1) RMSE for this way of estimating lambda is 1.4

    # 2) The mean error is small and decreases with n, so this estimator
    #    appears to be unbiased.

    # One note: If the time between goals is exponential, the distribution
    # of goals scored in a game is Poisson.

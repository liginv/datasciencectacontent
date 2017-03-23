# Poisson Confidence Interval Explained

In February 2017 a student in the Johns Hopkins University *Statistical Inference* course requested a more verbose explanation of the content on calculating a confidence interval for the mean of a Poisson random variable. Specifically he wanted more detail regarding the content on slides 26 - 27 of the *Asymptopia* lecture.

## Explaining the Formulas

<img src="./images/statinf-poissonInterval01.png">

## Key difference: how wide is the interval?

Here is the R code from slide 27 of the lecture.

      > x <- 5
      > t <- 94.32
      > lambda <- x / t
      >
      > # manually calculated confidence interval
      > round(lambda + c(-1,1) * qnorm(.975) * sqrt(lambda/t),3)
      [1] 0.007 0.099
      >
      > # Poisson test version of confidence interval
      > poisson.test(x,t)$conf.int
      [1] 0.01721254 0.12371005
      attr(,"conf.level")
      [1] 0.95
      >

Notice that the manually calculated interval is more aggressive (narrower) than the `poisson.test()` version.

      > # manual
      > manualInterval <- round(lambda + c(-1,1) * qnorm(.975) * sqrt(lambda/t),5)
      > manualInterval[2] - manualInterval[1]
      [1] 0.09293
      > # poisson test
      > poissonInterval <- poisson.test(x,t)$conf.int
      > poissonInterval[2] - poissonInterval[1]
      [1] 0.1064975
      >

for additional background on the Poisson distribution and calculating confidence intervals for it, see also [Introduction to the Poisson Distribution](http://bit.ly/2kJH86C), [Computing Confidence Interval for Poisson Mean](http://bit.ly/2lVyPdj), and [Comparison of Confidence Levels for the Poisson Mean: Some New Aspects](http://bit.ly/2lhIZlg) by Patil and Kulkarni.

### One Tailed T-test - Exploratory Data Analyses

EDA is very important to determine whether to reject or fail to reject hypothesis. EDA can include anything from t-tests, to data cleaning to regression models.

Using Scipy, I was able to use logarithmic reaction time data to identify the t-value and p-value to test certain conditions/hypothesis by a one-tailed t-test. While coding this I had difficulties determine whether this test was two-tailed or one tailed. Once I knew it was one-tailed I analyzed which alternative kwarg I would have had to use. Because its reaction time 'greater' was the right choice based on the hypothesis (one condition was slower than another) since the higher the number the slower the reaction time.


```
t, p = stats.ttest_rel(fi_si, fc_si, alternative='greater')
print('Incongruent-Incompatible vs. Congruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

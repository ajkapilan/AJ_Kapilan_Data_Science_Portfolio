# Exploratory Data Analyses

EDA is very important to determine whether to reject or fail to reject hypothesis. EDA can include anything from t-tests, to data cleaning to regression models, to statsitical indentification. Scipy is a very powerful python tool to do all these things. 

Using Scipy, I was able to use logarithmic reaction time data to identify the t-value and p-value to test certain conditions/hypothesis by a one-tailed t-test. While coding this I had difficulties determine whether this test was two-tailed or one tailed. Once I knew it was one-tailed I analyzed which alternative kwarg I would have had to use. Because its reaction time 'greater' was the right choice based on the hypothesis (one condition was slower than another) since the higher the number the slower the reaction time.

### Example 1
```
t, p = stats.ttest_rel(fi_si, fc_si, alternative='greater')
print('Incongruent-Incompatible vs. Congruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

```
t, p = stats.ttest_rel(fi_si, fi_sc, alternative='greater')
print('Incongruent-Incompatible vs. Incongruent-Compatible t =', str(round(t, 2)), 
      ' p = ', str(round(p, 4)))
```

![Screenshot 2021-11-18 163535](https://user-images.githubusercontent.com/94637743/142492595-f4668a35-65a2-4fd4-acf4-db53ba7582fe.jpg)


In this next example below I used Scipy to remove outliers (+ or - 3 standard deviations) from reaction time data. The data was transformed into z-data by using the 'stats.zscore' function from Scipy. 

### Example 2
```
df['rt_z'] = df.groupby('id')['rt_ms'].transform(stats.zscore)
```

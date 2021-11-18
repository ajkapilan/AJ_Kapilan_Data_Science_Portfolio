### Data Visualization of Reaction Time of Participants

Data visualization is a key concept in coding that allows us to make our DataFrames and specific parts of the data look very nice and easy to understand. 

This histogram plot I used Seaborn to visualize reaction time data of 3 different conditions. Three plots were made to fully visualize the reaction time depending on the specific condition. This allowed me to interpret the results visually! 

I tried changing the 'palette' color to 'flare' but felt bright was the best option visually. 


```
sns.displot(data=df, x='rt_clean', stat='probability', hue='flankers', col='simon', alpha = .4, kind='hist', palette='bright')
plt.show()
```

output:

![Screenshot 2021-11-18 160407](https://user-images.githubusercontent.com/94637743/142490055-f369ccff-f443-4db2-94c9-12e65b58eefd.jpg)

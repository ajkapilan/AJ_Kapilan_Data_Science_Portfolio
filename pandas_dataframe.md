# Working with Pandas Dataframes 
Pandas is a structure to can combine data into tables and structure them so they can be used to look at and evaluate for further investigation. There are an abundant of tools you can use to style, describe, locate specific values etc. in pandas dataframes. 

Before working with the dataframes you have to read it into python. Reading in dataframes can be simple since it has a csv function that allows us to quickly read in csv files, but sometimes data files are in other formats like txt (text files). Text files contain backslashes seperating each line so using csv read function you can seperated the data coloumns using the powerful '\' escape key. 
Below is code to read in different dataframes.

```
df = pd.read_csv('s01/s01.txt')
```
![image](https://user-images.githubusercontent.com/94637743/146218124-d9cb82b1-3948-453e-9281-2c41b6bfa044.png)

```
df = pd.read_csv('s01/s01.txt', sep='\t')
df.head()
```
![image](https://user-images.githubusercontent.com/94637743/146218248-aa7a90cb-ef8d-47d9-97cd-0dc869d3d2a3.png)

Now that the dataframe is read into python properly now you can do some Dataframe styling :sunglasses:

Here is a [link](https://web.microsoftstream.com/video/770329bd-68a1-42ea-8ffd-caedae72e2fd) to a demonstration I did on pandas dataframe styling. Styling is a fun tool in which you can visualize data easier in dataframes and shade in values in the dataframe columns to see which values are higher or lower.  

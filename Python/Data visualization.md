# Data visualization

## Seaborn

```python
import seaborn as sns
```



### Line Charts

```python
# Line chart showing daily global streams of each song 
sns.lineplot(data=spotify_data)
```

- *Every command that you learn about in this course will start with `sns`, which indicates that the command comes from the [seaborn](https://seaborn.pydata.org/) package. For instance, we use `sns.lineplot` to make line charts. Soon, you'll learn that we use `sns.barplot` and `sns.heatmap` to make bar charts and heatmaps, respectively.*

- `data=spotify_data` selects the data that will be used to create the chart.

  

Sometimes there are additional details we'd like to modify, like the size of the figure and the title of the chart. Each of these options can easily be set with a single line of code.

```python
# Set the width and height of the figure
plt.figure(figsize=(14,6))

# Add title
plt.title("Daily Global Streams of Popular Songs in 2017-2018")

# Line chart showing daily global streams of each song 
sns.lineplot(data=spotify_data)
```

### Plot a subset of the data

So far, you've learned how to plot a line for *every* column in the dataset. In this section, you'll learn how to plot a *subset* of the columns.

We'll begin by printing the names of all columns. This is done with one line of code and can be adapted for any dataset by just swapping out the name of the dataset (in this case, `spotify_data`).

```python
list(spotify_data.columns)

output[0]:
  ['Shape of You',
 'Despacito',
 'Something Just Like This',
 'HUMBLE.',
 'Unforgettable']
```



```python
# Set the width and height of the figure
plt.figure(figsize=(14,6))

# Add title
plt.title("Daily Global Streams of Popular Songs in 2017-2018")

# Line chart showing daily global streams of 'Shape of You'
sns.lineplot(data=spotify_data['Shape of You'], label="Shape of You")

# Line chart showing daily global streams of 'Despacito'
sns.lineplot(data=spotify_data['Despacito'], label="Despacito")

# Add label for horizontal axis
plt.xlabel("Date")
```

- Instead of setting `data=spotify_data`, we set `data=spotify_data['Shape of You']`. In general, to plot only a single column, we use this format with putting the name of the column in single quotes and enclosing it in square brackets. (*To make sure that you correctly specify the name of the column, you can print the list of all column names using the command you learned above.*)
- We also add `label="Shape of You"` to make the line appear in the legend and set its corresponding label.



### Bar Charts and Heatmaps
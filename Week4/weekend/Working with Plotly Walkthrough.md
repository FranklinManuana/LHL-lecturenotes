In this hands-on activity, we will create interactive plots with `Plotly`. We will focus on the most commonly used plots such as scatter plots, line plots, bar charts, and histograms.

Let’s begin by importing graph objects from `Plotly`.

```python
# import graph objects from plotly 
import plotly.graph_objs as go
```

### Scatter Plot

```python
# 100 random integers from <1,100>
random_x = np.random.randint(1,101,100)
random_y = np.random.randint(1,101,100)

# create the data
data = [go.Scatter(
    x = random_x,
    y = random_y,
    mode = 'markers',
)]

# create the layout 
layout = go.Layout(
    title = 'Random Data Scatterplot', # Graph title
    xaxis = dict(title = 'Some random x-values'), # x-axis label
    yaxis = dict(title = 'Some random y-values'), # y-axis label
    hovermode ='closest' # handles multiple points landing on the same vertical
)

# create the figure
fig = go.Figure(data=data, layout=layout)
fig.show()
```

In the example above, we can see that the figure is made up of two components. The first component is a list with traces (only one trace in our case). The second component is a layout that includes all customizations of the figure such as the title, the axis names, and so on. If we don't want to customize our figure, this component is not compulsory.

### Line Plot

Another useful type of plot we need to learn to create is a line plot. In this example, we will also explore how to create a figure with multiple traces.

```python
# 1000 values from the interval <0,1>, equidistantly divided
x_values = np.linspace(0, 1, 100)

# 100 sample from a standard normal distribution
y_values = np.random.randn(100)   

# create traces
trace0 = go.Scatter(
    x = x_values,
    y = y_values+5,
    mode = 'markers',
    name = 'markers'
)
trace1 = go.Scatter(
    x = x_values,
    y = y_values,
    mode = 'lines+markers',
    name = 'lines+markers'
)
trace2 = go.Scatter(
    x = x_values,
    y = y_values-5,
    mode = 'lines',
    name = 'lines'
)

# create the data
data = [trace0, trace1, trace2]  # assign traces to data

# create the layout
layout = go.Layout(
    title = 'Line chart showing three different modes'
)

# crate the fig
fig = go.Figure(data=data,layout=layout)
fig.show()
```

In the example above, we created three traces from generated data. In the first trace, data are shifted up along the y-axis by 5. In the second trace, data are without change, and in the third trace, data are shifted down along the y-axis by 5. We also set a different marking mode for each trace.

### Bar Chart

For this type of plot, we will load the Winter Olympics 2018 data.

```python
# load the Olympic data
df_olympic = pd.read_csv('https://raw.githubusercontent.com/Pierian-Data/Plotly-Dashboards-with-Dash/master/Data/2018WinterOlympics.csv',sep =',')
```

Explore the data:

```python
df_olympic.head()
```

Let's plot Olympic medals by country:

```python
# create the data
data = [go.Bar(
    x=df_olympic['NOC'],  # NOC stands for the National Olympic Committee
    y=df_olympic['Total']
)]

# create the layout
layout = go.Layout(
    title='2018 Winter Olympic Medals by Country'
)

# create the figure
fig = go.Figure(data=data, layout=layout)
fig.show()
```

In the chart above, we have the total number of medals for each country. We can also plot how many gold, silver and bronze medals each country had.

```python
# trace1 - gold medals
trace1 = go.Bar(
    x=df_olympic['NOC'],  # NOC stands for the National Olympic Committee
    y=df_olympic['Gold'],
    name = 'Gold',
    marker=dict(color='#FFD700') # set the marker color to gold
)

# trace2 - silver medals
trace2 = go.Bar(
    x=df_olympic['NOC'],
    y=df_olympic['Silver'],
    name='Silver',
    marker=dict(color='#9EA0A1') # set the marker color to silver
)

# trace3 - bronze medals
trace3 = go.Bar(
    x=df_olympic['NOC'],
    y=df_olympic['Bronze'],
    name='Bronze',
    marker=dict(color='#CD7F32') # set the marker color to bronze
)

# create the data
data = [trace1, trace2, trace3]

# create the layout
layout = go.Layout(
    title='2018 Winter Olympic Medals by Country'
)

# create the figure
fig = go.Figure(data=data, layout=layout)
fig.show()
```

We can also create a stacked bar chart, where we are still plotting by medal type, but the bronze, silver and gold traces are stacked to better show each country's total.

To do this, we can use the traces we already created, all we need to do is change the layout mode and re-plot:

```python
# create the layout
layout = go.Layout(
    title='2018 Winter Olympic Medals by Country',
    barmode='stack'  # stack the bars
)

# create the figure
fig = go.Figure(data=data, layout=layout)
fig.show()
```

### Histogram

For the purpose of creating a histogram, we will use data containing the heights of women and men:

```python
# load the heights data
df = pd.read_csv('https://raw.githubusercontent.com/Pierian-Data/Plotly-Dashboards-with-Dash/master/Data/arrhythmia.csv',sep=',')
```

Explore the features:

```python
df.head()
```

Let's create a histogram, which will compare the distribution of men's heights and women's heights:

```python
# create the data 
data = [
    # men
    go.Histogram(
    x=df[df['Sex']==0]['Height'],
    opacity=0.75,
    name='Male'
),  
    # women
    go.Histogram(
    x=df[df['Sex']==1]['Height'],
    opacity=0.75,
    name='Female'
)]

# create the layout
layout = go.Layout(
    barmode='overlay',
    title="Height comparison by gender"
)

# create the figure 
fig = go.Figure(data=data, layout=layout)
fig.show()
```

Note

`Bar charts` and `Histograms` might look similar but there is one significant difference between them. A histogram represents the frequency distribution of **continuous variables**. Conversely, a bar graph is a visual comparison of **discrete variables**. Histograms present numerical data whereas bar graphs show categorical data. Therefore the histogram is drawn in such a way that there is no gap between the bars.
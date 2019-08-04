---
layout: post
title:  "A quick guide to Plotly"
date:   2019-07-31
categories: [tutorial]
---
Python has a good selection of visualisation packages to work with. I have worked with and tried out a few, namely seaborn, ggplot and matplotlib. While I like the simplicity of how easy it is to plot graph with those libraries, I always wished there was more interactivity.

Then I discovered plotly!

As with any library, it has its limitations. It's quite heavy and slow to load compared to other non-interactive libs and there are several ways to plot one graph so getting started can seem a bit confusing. I want to go through 2 different methods of plotting: plotly graph objects and a cufflinks.

If like me, you want to make pretty, interactive plots without having to make an account or worry about JS, HTML or CSS, here's a short tutorial for you.
<!--more-->

First things first, import the relevant libs and start the notebook mode which allows you to show plots in jupyter.:

{% highlight python%}
import plotly.offline as py
import plotly.graph_objs as go
import pandas as pd
py.init_notebook_mode()
{% endhighlight %}

Next, I will make a pandas dataframe for my data. This isn't  necessary in all the three separate libraries but for the purpose of this tutorial, it allows for good comparison of code length.

{% highlight python%}
x = ['SQL', 'Python', 'Excel']
y = [80, 50, 30]
df = pd.DataFrame({'Topics': x, '% usage at work': y})
df.head()
{% endhighlight %}

Now you're ready to plot! First, plotting with **plotly graph objects**:

{% highlight python%}
    # load the data
data = [go.Bar(
    x=df['Topics'], # assign x axis as Topics column
    y=df['% usage at work'] # assign y axis as % usage at work column 
)]
    # define the layout
layout = go.Layout(
    title='Languages used at work'
)
fig = go.Figure(data=data, layout=layout)
     #plot the figure
py.iplot(fig, filename='pandas-bar-chart')
{% endhighlight%}

{% include pandas-bar-chart.html %}

Now, let's try **cufflinks**

{%highlight python%}
import cufflinks as cf
cf.go_offline()

df.iplot(kind='bar', x='Topics', y='% usage at work', title = 'Languages used at work')
{% endhighlight %}

{% include cufflinks_example.html %}


The plotting has been reduced to a single line! This is because cufflinks is a *wrapper* for the plotly API that has been specifically crafted to simplify plotting pandas dataframes with plotly.

However, at the time of writing, cufflinks doesn't support all of the graph objects in plotly (the list of supported graph types is growing, check it out [here]('However, at the time of writing, cufflinks doesn't support all of the graph objects in plotly (the list of supported graph types is growing, check it out [here](https://github.com/santosjorge/cufflinks)) 
)) so it's best to use a mix of the two depending on your visualisation requirements. 

For example, here's a  scatter polar graph that is currently not available in cufflinks.

{% include skills_radar_graph.html %}

Code:
{% highlight python%}
data = [go.Scatterpolar(
  r = [80, 55, 20, 40, 50, 21, 30, 45, 50],
  theta = ['pandas','numpy','nltk', 'sklearn', 'plotly', 'matplotlib', 'bs4','dash', 'seaborn'],
  fill = 'toself',
    line_color='#abd5ed'
)]

layout = go.Layout(
    title='Confidence in commonly used Python libraries',
  polar = dict(
    radialaxis = dict(
      visible = True,
      range = [0, 100]
    )
  ),
  showlegend = False
)

fig = go.Figure(data=data, layout=layout)
py.iplot(fig, filename = "radar/basic")
{% endhighlight %}

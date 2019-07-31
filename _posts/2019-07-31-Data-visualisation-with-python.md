---
layout: post
title:  "A quick guide to Plotly"
date:   2019-07-31
categories: [tutorial]
---
Python has a good selection of visualisation packages to work with. I have worked with and tried out a few, namely seaborn, ggplot and matplotlib.
While I like the simplicity of how easy it is to plot graph with those libraries, I always wished there was more interactivity. I had a go at bokeh but found the transitions to be a but clunky and felt I wanted something sleeker.
Then I discovered plotly! I think it actually required an account when I first heard of it bit I revisited earlier this year and to my surprise, it was available offline and free! I have been playing with it ever since and everyone who has seen it has also been impressed!

That being said it also has its limitations. It's quite heavy and slow to load compared to other non-interactive libs and sometimes plotting can seem quite a lengthy process so it definitely isn't a library I would use for every occasion.

If like me, you want to make pretty, interactive plots without having to worry about JS, HTML or CSS *and* don't like trawling through docs, I have written a brief guide to getting started with plotly without an account in Jupyter Notebooks.
<!--more-->
First things first, import the relevant libs and start the notebook mode which allows you to show plots in jupyter.:

{% highlight python%}
import plotly.offline as py
import plotly.graph_objs as go
py.init_notebook_mode()
{% endhighlight %}

There are several options when graphing with plotly. When working with a small amount of data, I like taking the following approach as it allows the most customisation:
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

{% include skills_radar_graph.html %}

However, a great addition to plotly is cufflinks! Cufflinks allows you to plot pandas dataframes with much fewer lines but you are limited to specific types of graphs.

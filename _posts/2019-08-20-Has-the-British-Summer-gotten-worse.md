---
layout: post
title:  "Has the London Summer gotten worse?"
date:   2019-08-20
categories: [blogpost]
---
A friend and I were hanging out on his balcony and suddenly it started raining. Experiencing rain in the UK in the summer season was no surprise to me, however, as we hurried back inside, my friend remarked that he thinks that our Summers have gotten 'worse'. I asked him to elaborate and he replied: 'London Summers have gotten shorter and it's raining a lot more than it used to'. From my memory, I feel that the London Summer have gotten a lot more pleasant, with warmer days and less rain. So, I decided to do some analysis rather so I could see which of us had the right idea.

The MetOffice kindly provides yearly weather data measured at Heathrow from 1984 to 2019. If you too are wondering how London Summers have progressed, read on to see the answers.
<!--more-->

#### Are Summers getting shorter in London?

Firstly, how is Summer actually defined? Apparently the Summer seasons are June-Aug. A heatmap of the maximum monthly temperatures recorded confirms this.

{% include temp_heatmap.html %}

As expected, the heatmap doesn't show a huge amount of variation between the summer temperatures and there is no obvious cut off for the temperatures, mainly due to this only showing the max temperatures recorded.

In order to get a better idea, I have taken a 3 month rolling mean for the max temperatures recorded. As the years progress, it is clear that the temperatures have changed since 1948 and sometimes summers seem longer, as seen by the increase in the area under the peak. However, as we scroll through the years, the 3 monthly rolling mean show a big variation os the data is inconclusive.

{% include mean_monthly_temp_slider.html %}


#### Has it been getting colder in the Summer?

Taking an average of the temperature recorded each year in the summer months, a clearer trend can be seen, especially when looking at the 5 and 10 year rolling means.

{% include 5_year_summer_temp.html %}

Both the maximum temperature and minimum temperature show a general increase from 1984. However, if you zoom into the data from the past 20 years, the temperatures have not varied largely and the rolling means are pretty much a straight line.

#### Are we getting more rain in the Summer?

{% include rain_heatmap.html %}

Unsurprisingly, there seems to be a similar level rain each month and there is no specific period where there is significantly less rain, Summertime included. 

{% include summer_rain_avg.html %}

There seems to be a lot of fluctuation in the rainfall each summer. My friend was right in saying that last Summer we had little rain, lowest average rainfall in Jun-Aug compared to many years before. If we zoom in to the last 20 years, the 10 year rolling mean shows a slight increase in the average Summer rainfall, however judging by the level of fluctuation in the raw data it's difficult to justify the trend as being significant.


In conclusion, although there are some trends in the data to suggest that there is a change in the Summer, the question of if the summer has been been getting worse seems to have an answer of 'no'. The average of Summer if you will seems to have stayed around the same temp and rainfall seems to vary so greatly each year, it's harder to derive a trend.


datasource: https://www.metoffice.gov.uk/pub/data/weather/uk/climate/stationdata/heathrowdata.txt

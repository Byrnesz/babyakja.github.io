---
layout: post
title: Data Viz : A Journey through Time and Space!
featured-img: nasa
mathjax: true
categories: [EDA,Visualization]
---

Now that the holiday season is here and I had some extra time on my hands, I wanted to try to do challenge myself with a quick and interesting visualization projects.

To do so, I took ion this month's DataViz Battle put on by the subreddit r/dataisbeautiful. In DataViz Battle challenges, a dataset is supplied and it is up to the individual to come up with and create interesting and informative data visualizations.

This month, the dataset contained NASA astronaut data, both current and former, along with stats about them for things such as _selection year into the program, time spent in space, and military or civilian background._

This year, NASA will mark the 60th anniversary of its establishment as a U.S. government agency. Let's see what we can uncover about the past 60 years through data visualization!

## Data Cleaning

I loaded the csv into a __Jupyter Notebook__, and an initial inspection of the datatypes returned the following:

```
Astronaut                                object
Selection Year                            int64
 Group                                    int64
 # Flights                               object
Status                                   object
Military or civilian                     object
Gender                                   object
If military include details              object
Date of birth                            object
Job                                      object
Missions flown                           object
Cumulative hours of space flight time    object
```
My first impressions is that there will at least have to be some clean up to the column names to make them functional by trimming extra spaces, and shorting some of the names.

After that, what I expected to be numeric values for _Number of Flights_ and _Hours in Space_ needed to be converted to integers from string and account for some of the null values present.

Finally, I cleaned up categorial columns I wanted to use by removing extra spaces and filling in null values based on research to make the data useful for grouping and finding trends.

### Feature Creation

I used the year from _Date of birth_ along with _Selection Year_ to make a new data column called _Age_, which refers to the age of the Astronaut at the time of their selection into the program.

## Layout

When I think of space and charts, my first visual is the control panel of the Space Shuttle or any electronic device. This gave me the idea to use a dark background along with crisp colors that stand out on a black background.

![Space Shuttle Controls](https://raw.githubusercontent.com/babyakja/babyakja.github.io/master/assets/img/posts/nasa_space_shuttle_controls.png)

![Wing Commander](https://raw.githubusercontent.com/babyakja/babyakja.github.io/master/assets/img/posts/Wing_Commander_20.gif)

My default charting is usually __Seaborn__ when doing quick plots with styling but I also wanted to try out the new __Chartify__ library released by Spotify to test it's functionality.

```Python
plt.style.use("dark_background")
```


## Explore Data



_### Gender Selection across Space program_

![Gender across Space Program](https://raw.githubusercontent.com/babyakja/babyakja.github.io/master/assets/img/posts/nasa_gender_year_sns.png)

> Women were not selected as part of the astronaut program until 1978
> The 1978 group included notable astronauts Sally Ride (first American woman in space), Shannon Lucid (held longest duration stay in space by an American), Anna Lee Fisher (first mother in space), and Judith Resnik (aboard _Challenger_ mission).
> Women have never exceed or meet 50% of a selection groups total. Come on NASA!

_### Age Distribution_


#### By Status

![Age Distribution by Status](https://raw.githubusercontent.com/babyakja/babyakja.github.io/master/assets/img/posts/nasa_age_boxplot_sns.png)

- WHO IS THE OUTLIER THAT BECAME AN ASTRONAUT AT 47?!
> Barbara Morgan was the backup to Christa McAuliffe as part of the Teachers in Space Project back in 1985. McAuliffe was part of the crew for the ill-fated Space Shuttle Challenger mission in 1986.
> Morgan was finally selected in 1998 and flew on the STS-118 Mission.

#### By Service

![Age Distribution by Service](https://raw.githubusercontent.com/babyakja/babyakja.github.io/master/assets/img/posts/nasa_time_service_sns.png)

#### By Selection Year

![Age Distribution by Year](https://raw.githubusercontent.com/babyakja/babyakja.github.io/master/assets/img/posts/nasa_age_year_sns.png)

_### Astronaut Selection_

{% include nasa_sankey.html %}

_### Time in Space_

![](https://raw.githubusercontent.com/babyakja/babyakja.github.io/master/assets/img/posts/nasa_time_year_sns.png)

#### By Selection Year






## Conclusion

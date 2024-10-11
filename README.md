# NFL Passing Statistics Data Visualization Project

## Data
The dataset(s) that I propose to use for my project are the NFL passing statistics data from [Pro Football Reference](https://www.pro-football-reference.com/), particularly the statistics from the past 10 seasons (2014 to 2023). They are linked as follows
* https://www.pro-football-reference.com/years/2023/passing.htm
* https://www.pro-football-reference.com/years/2022/passing.htm
* https://www.pro-football-reference.com/years/2021/passing.htm
* https://www.pro-football-reference.com/years/2020/passing.htm
* https://www.pro-football-reference.com/years/2019/passing.htm
* https://www.pro-football-reference.com/years/2018/passing.htm
* https://www.pro-football-reference.com/years/2017/passing.htm
* https://www.pro-football-reference.com/years/2016/passing.htm
* https://www.pro-football-reference.com/years/2015/passing.htm
* https://www.pro-football-reference.com/years/2014/passing.htm

Since the datasets are on a per-season basis, the same player may be listed multiple times. To distinguish players, an attribute named 'year' will need to be added when merging the three datasets. In doing so, the same player's statistics in different seasons can be distinguished. Further data preprocessing will need to be done on the awards column as well to properly encode it. An important thing to note is that the implementation will only consider players who play the quarterback position. Players who do not play quarterback attempt passing plays are credited with passing statistics in certain situations. These players will be filtered out in the visualization.

## Questions & Tasks

The main idea behind this visualization is a scatter plot with two axes. These axes are configurable and can correspond to a passing statistic in the dataset. The points on the scatter plot will represent a specific player and will encode the awards that they won for that season. With this concept in mind, the following tasks and questions will drive the visualization and interaction decisions for this project:

* What statistic(s) are most strongly correlated to winning an award
* What player(s) are outliers with respect to winning a postseason award (i.e. were there players who _should_ have won an award or _should not_ have?)
* Is there any significant difference with respect to winning an award in different seasons (i.e. Was it easier or harder to win an award in, for example, 2014 vs. 2023?).
* What statistics do not affect a player's award chances (i.e. there is a low correlation)

## Sketches

(insert one or more hand-drawn sketches of interactive visualizations that you imagine)
(describe each sketch - how is the data visualized, what are the interactions, and how do these relate to the questions/tasks)


## Prototypes

I’ve created a proof of concept visualization of this data. It's a ... and it shows ...

[![image](https://user-images.githubusercontent.com/68416/65240758-9ef6c980-daff-11e9-9ffa-e35fc62683d2.png)](https://vizhub.com/curran/eab039ad1765433cb51aad167d9deae4)

(please put a screenshot of one or more visualizations of this dataset you already made, for previous assignments, and link to them)

You can put images into here by pasting them into issues.

You can make images into links like this:

```
[![image](https://user-images.githubusercontent.com/68416/65240758-9ef6c980-daff-11e9-9ffa-e35fc62683d2.png)](https://vizhub.com/curran/eab039ad1765433cb51aad167d9deae4)
```


Also, you can study the [source](https://raw.githubusercontent.com/curran/dataviz-project-template-proposal/master/README.md) to figure out Markdown formatting. You can use the GitHub built-in editor to edit the document.

## Open Questions

(describe any fear, uncertainty, or doubt you’re having about the feasibility of implementing the sketched system. For example, “I’m not sure where to get the geographic shapes to build a map from this data” or “I don’t know how to resolve the codes to meaningful names” … Feel free to delete this section if you’re confident.)

## Milestones

(for each week, estimate what would be accomplised)

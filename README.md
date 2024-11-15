# NFL Passing Statistics Data Visualization Project

## Work so Far
Below are links to VizHub that show the projects progression 
* **10/24/2024:** https://vizhub.com/SamKarkache/nfl-passing-course-project <br>
I made great progress on my project so far. The biggest thing that I was able to accomplish was making the x and y axes configurable. This is one of the biggest features for my project so I am glad I was able to implement it. A slight bug that I noticed while I was working was that my legend for the scatterplot partially disappears when changing the axes. I have a feeling that this is due to it not updating properly. I made one slight change to the proposal. Since there will be a lot of data points I want to give the option to filter by year. 
* **10/31/2024:** https://vizhub.com/SamKarkache/nfl-passing-yards-visualization-10-31-2024 <br>
I made even more progress in the project. The main things that I implemented this week are importing the rest of the data (passing data from 2013 to 2022), fixing the legend, and allowing the data to be filtered by year and by the players award. Looking at the current revision we can see the two new dropdown menus to the right of the scatter plot. I also laid the foundation for clicking individual points. As of right now, clicking a point will simply trigger a JavaScript alert containing the player's data. In the future, a better visualization for this information will be implemented. Another thing I hope to do in the future is tune the opacity of the data points and implement more robust filtering/querying features.
* **11/07/2024:** https://vizhub.com/SamKarkache/nfl-passing-yards-visualization-11-08-2024 <br>
This week I made progress on enhancing the legend. Clicking on the legend squares highlights the selected award type be decreasing the opacity of the other colors. I also took time to improve the the drop down menus so that filtering by both year and award works with less bugs. However, when used with the interactive legends, the dropdown menus reset. This will most likely need to be fixed by changing how I set up the drop downs along with more robust usage of setState.
* **11/15/2024:** https://vizhub.com/SamKarkache/nfl-passing-visualization-11-15-2024
Two major changes were implemented this week. The first major thing was a project refactoring change that transitioned to tracking values with the state/setState design paradigm. This included tracking the current filters on the data, the current choices for the x and y axes, and the hovered value using a state object. This solved some issues that were present in the previous revision. For example, this allowed for the dropdown menus to display the correct value when using the interactive legend (previously the state of the dropdown menus were not tracked so when the interactive legend was used the page re-rendered and set the dropdowns to the default value). The next thing implemented this week relates to this week's lectures on interaction. Clicking a datapoint now displays the player's name, the year the stats were recorded, and the x and y values. Clicking on the same point again (or another point) closes that menu. Future work includes fixing the dropdown menu position and styling along with adding more complex filters.

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
Below is a sketch of what the visualization should look like when finished.

![sketch](https://github.com/user-attachments/assets/c8cae5da-71ea-411b-aad0-c27bc6f5f8eb)

As you can see there are two areas in which the user can interact with the visualization. The user can select the statistic encoded on the x and y axes. The user can also click the data point and display the relevant information about the player and their statistic during the particular season. Furthermore, the visualization shows how the player awards are encoded via color and shape. 

## Prototypes
Below is a very simple proof-of-concept visualization that I created and represents my work so far.

![image](https://github.com/user-attachments/assets/6f7001cf-53aa-42a3-9934-246472e9b36c)

This visualization uses passing data from 2023 and plots players in terms of touchdowns on the x-axis and quarterback rating on the y-axis. The data points are players at the quarterback position who started more than one game. We then use color to encode the award that the player won. As shown in the prototype, we can derive a correlation between these statistics and winning an award as all the award winners had high values of each statistic. This is the general idea behind what I want to do with the visualization and the full visualization can be built off of this prototype. 

## Milestones
* Week 8: Data fully cleaned and imported. Axes set up.
* Week 9: Have two static statistics showing up on the axes with the awards encoded.
* Week 10 and Week 11: Implement the dynamic axes
* Week 12: Implement clicking on data points
* Week 13 and Week 14: Finishing touches.

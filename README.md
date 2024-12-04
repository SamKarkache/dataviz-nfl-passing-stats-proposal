# NFL Passing Statistics Data Visualization Project Report
Samuel Karkache <br>
CS 573: Data Visualization <br>
December 3rd, 2024 <br>
Final Project VizHub Link: https://vizhub.com/SamKarkache/nfl-passing-yards-visualization-final-revision
## Introduction
This project involves making an interactive scatter plot that visualizes different passing statistics recorded by quarterbacks in the NFL concerning the award(s) won by that player. The goal was to make a visualization that would let users uncover interesting features about the data that may not be immediately apparent when looking at the raw data. Robust filters will also allow for enhanced analysis of the different passing statistics.

## Data
The dataset(s) that I utilized for this visualization is the NFL passing statistics data from [Pro Football Reference](https://www.pro-football-reference.com/), particularly the statistics from the past 11 seasons (2013 to 2023). They are linked as follows:
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
* https://www.pro-football-reference.com/years/2013/passing.htm

Since the datasets are on a per-season basis, the same player may be listed multiple times. An attribute named 'year' was added when merging the three datasets to distinguish players. In doing so, the same player's statistics in different seasons can be distinguished. Further data preprocessing was implemented to encode the awards won by each player into one of "No Award", "Pro Bowl", "All-Pro", or "MVP". An important thing to note is that the implementation only considers players who play the quarterback position and started at least one game during a given season. Players who do not play quarterback attempt passing plays are credited with passing statistics in certain situations. These players will be filtered out in the visualization as they may have won awards at a different position that is unrelated to passing.

## Questions & Tasks

The main idea behind this visualization is a scatter plot with two axes. These axes are configurable and can correspond to a passing statistic in the dataset. The points on the scatter plot will represent a specific player and will encode the award that they won for that season. With this concept in mind, the following tasks and questions will drive the visualization and interaction decisions for this project:

* What statistic(s) are most strongly correlated to winning an award
* What player(s) are outliers concerning winning a postseason award (i.e. were there players who _should_ have won an award or _should not_ have?)
* What statistics do not affect a player's award chances (i.e. there is a low correlation)
* Is there any significant difference concerning winning an award in different seasons (i.e. Was it easier or harder to win an award in, for example, 2013 vs. 2023?)?

## Sketches
Below is an initial sketch that I made early on in the development process that outlines how the visualization will look like and what kind of interactions it will have. <br> <br>
![sketch](https://github.com/user-attachments/assets/c8cae5da-71ea-411b-aad0-c27bc6f5f8eb) <br> <br>
As you can see there are two areas in which the user can interact with the visualization. The user can select the statistic encoded on the x and y axes. The user can also click the data point and display the relevant information about the player and their statistic during the particular season. Furthermore, the visualization shows how the player awards are encoded via color. 

## Prototyping and Implementation Timeline
### Initial Prototype
Below is a very simple proof-of-concept visualization that implements the above sketch. Interactions have not been developed in the initial prototype but the idea was to transfer the concept from a sketch into D3. <br> <br>
![image](https://github.com/user-attachments/assets/6f7001cf-53aa-42a3-9934-246472e9b36c) <br> <br>
This visualization uses passing data from 2023 and plots players in terms of touchdowns on the x-axis and quarterback rating on the y-axis. The data points are players at the quarterback position who started more than one game. We then use color to encode the award that the player won. As shown in the prototype, we can derive a correlation between these statistics and winning an award as all the award winners had high values of each statistic.

### 10/24/2024 Revision https://vizhub.com/SamKarkache/nfl-passing-course-project
The first major revision to the initial prototype was making the x and y axes configurable via a drop-down menu so that they can be changed dynamically. This required that the calls to render the scatter plot are dynamically passed data that that each numeric statistic is pre-processed and parsed from the CSV.  
All numeric columns in the datasets above are selectable. <br> <br>
![image](https://github.com/user-attachments/assets/c6b4a3d4-9373-42f0-a96e-8ae58db362dc) <br> <br>

### 10/31/2024 Revision https://vizhub.com/SamKarkache/nfl-passing-yards-visualization-10-31-2024
This revision imported the rest of the data (from the years 2013 to 2022) as the prototype and the previous revision just used data from 2023. As alluded to previously, some additional data pre-processing had to be implemented. In particular, I had to create a new year column for the data to be able to distinguish the same player's statistics that occurred during different seasons. Furthermore, two data filters were added. The user can filter the data points by year or award to see a smaller subset of data. Finally, clicking on a point now opens a JavaScript alert with that player's information. This was implemented as a placeholder for future revisions. <br> <br>
![image](https://github.com/user-attachments/assets/6805d806-7289-4e14-9ecc-04ff9698dd13) <br> <br>

### 11/07/2024 Revision https://vizhub.com/SamKarkache/nfl-passing-yards-visualization-11-08-2024 
This revision implements a dynamic legend that decreases the opacity of non-highlighted points to provide more visual clarity in location on the scatterplot. The screenshot below shows a situation where this may be useful. There is a high concentration of data points that correspond to having "No Award" to the left of the scatterplot. By clicking the green square on the legend we can decrease the opacity of other data points and be able to distinguish data relating to, for example, Pro Bowl-winning players. <br> <br>
![image](https://github.com/user-attachments/assets/f1676b80-c1d7-4181-ade8-c591b66c0cbc) <br> <br>

### 11/15/2024 Revision https://vizhub.com/SamKarkache/nfl-passing-visualization-11-15-2024
Two major changes were implemented for this revision. The first major thing was a project refactoring change that transitioned to tracking values with the state/setState design paradigm. This included tracking the current filters on the data, the current choices for the x and y axes, and the hovered value using a state object. This solved all the issues that were present in the previous revisions relating to tracking the state of the data and filters. For example, this allowed for the dropdown menus to display the correct value when using the interactive legend (previously the state of the dropdown menus was not tracked so when the interactive legend was used the page re-rendered and set the dropdowns to the default value). The next thing implemented in this revision relates to this week's lectures on interaction. Clicking a datapoint now displays the player's name, the year the stats were recorded, and the x and y values. Clicking on the same point again (or another point) closes that menu. If the dynamic legend selects a certain award type, then data points of the other award type are not selectable meaning that the user can essentially "click through them".  <br>  <br>
![image](https://github.com/user-attachments/assets/4db62707-5beb-449b-a33a-5b4803e9e408) <br> <br>

### 11/22/2024 Revision https://vizhub.com/SamKarkache/nfl-passing-yards-visualization-11222024-revision
This revision increases the visual appeal of the project. The dropdown menus were styled, the canvas size was increased, and a new dynamic scatter plot title was implemented. Furthermore, the location of the award and year dropdown menus were moved to the bottom of the canvas. Some visual bugs were also fixed by improving the state logic. A new feature that was implemented was the player name search text box. A user can now search for players by name by typing it in the textbox. If a search results in no matching entries (i.e. the player name does not exist or is already filtered out), the user will be alerted. A reset filter button is also present to set the filters back to their default values. <br> <br>
![image](https://github.com/user-attachments/assets/a8f5179b-1d43-4b76-b9f5-323eef2356bf) <br> <br>

### 11/29/2024 Revision https://vizhub.com/SamKarkache/nfl-passing-yards-visualization-11292024-revision
This revision added some slight visual enhancements with spacing and positioning. The primary thing that was implemented was the addition of a help button that explains some of the visualization's features. The question mark button will toggle the tool tip that explains how the filters and interactions on the data visualization work. 
<br> <br>
![image](https://github.com/user-attachments/assets/9f4fd63d-e657-457f-985c-710272890223) <br> <br>

### Final Revision https://vizhub.com/SamKarkache/nfl-passing-yards-visualization-final-revision
For the final revision, a few visual enhancements were added. The current value of the year filter is now displayed on the scatter plot title. Also, hovering over a data point will now make the circle radius increase and give the data point a black border so it is clear what data point is being selected. This is particularly helpful when there are a large number of highly concentrated data points. <br> <br>
![image](https://github.com/user-attachments/assets/ed9970b5-44c0-4ae6-8820-fa22dcf12515) <br> <br>

## Example Tasks Using Full Implementation
### What statistic(s) are most strongly correlated to winning an award
Looking through many of the statistics we can see that high values for passing yards and touchdowns correlate to receiving an award. There are large clusters of red "No Award" Datapoints in the bottom left of the scatter plot with all the award winners being concentrated to the upper left. <br> <br>
![image](https://github.com/user-attachments/assets/bf304334-62ab-410b-8f04-6a112ce1662b) <br> <br>

## What player(s) are outliers concerning winning a postseason award (i.e. were there players who _should_ have won an award or _should not_ have?) <br>
The image below shows an outlier that I identified with respect to winning an award. As established above, the yards and touchdown statistics had a high positive correlation with respect to winning an award. Using the dynamic legend we can see a clear outlier for the Pro Bowl award. In 2022 a player named "Tyler Huntley" seems to have made the Pro Bowl despite underwhelming passing yard and touchdown statistics. <br> <br>
![image](https://github.com/user-attachments/assets/12736474-e491-4e27-9645-a4619d2718d2) <br> <br>

## What statistics do not affect a player's award chances (i.e. there is a low correlation)
Below are two less correlated statistics with respect to getting an award. Firstly, across the x-axis, the number of sacks taken by the quarterback a relatively distributed for award winners. the same can be said for the player's age. This tells us that these statistics are not good predictors of a player's award chances. <br> <br>
![image](https://github.com/user-attachments/assets/251df4e9-708c-4176-a1eb-e76c24453fde) <br> <br>

## Is there any significant difference concerning winning an award in different seasons (i.e. Was it easier or harder to win an award in, for example, 2013 vs. 2023?)?
Below are two scatter plots for Yds versus TDs in the 2020 season and the 2021 season. It was a bit easier to win an award in 2021 as more players did so with fewer yards when compared to the 2020 season. 
![image](https://github.com/user-attachments/assets/631379f3-8abb-4a50-a8e9-8b9a01d9a3c8) <br> <br>  
![image](https://github.com/user-attachments/assets/2f25d37c-f02b-4ddc-b769-48242fdcc648) <br> <br>

## Conclusion and Future Work
This concept can be easily extrapolated to include different types of NFL statistics. For example, Running Back's rushing statistics could be a new view for this visualization. Furthermore, additional years can be added as well, pro football reference has statistics going back to the 1920 NFL season. Different types of visualizations could be added too. For example, a box plot can be implemented to view a particular player's (or group of players) statistics over many different seasons. I did not end up implementing the shape encoding for the awards shown in the sketch. It ended up not looking visually appealing. Future work could find a way to implement the shape encoding while maintaining the visual appeal. Finally, a cool idea could be to implement some sort of proprietary querying language that would allow for quick access to relevant statistics (i.e. something like "PLAYERS WHERE YDS > 3000 AND TD < 40). Overall, the project was a very good tool to help me learn all about the principles of data visualization.

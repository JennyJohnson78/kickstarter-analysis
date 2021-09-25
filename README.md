# Kickstarter Analysis
## Overview of the Project
Louise is interested in starting a fundraising campaign for a theater project and is seeking information on various kickstarter campaigns. She wouldlike more information on the statistics of campaigns based on category and subcategory, outcomes based on launch date and end time, as well as more specific information on theater outcomes by launch date and outcomes based on goals. The purpose of this analysis is to help Louise determine how well her theater campaign would fare if she were to launch one by looking at the success and failure of similar fundraisers, as well as when she should launch her campaign and what the goal should be.

## Analysis
For the analysis of theater outcomes by launch date, the first thing to do is create a column in the spreadsheet of Kickstarter data in order to separate the years from the dates in column Date Created Conversion column. The Date Created Conversion column takes the Unix timestamp data in column launched_at and converts it to a readable format, using the equation
```
=(((J2/60)/60)/24)+DATE(1970, 1, 1)
```
Using the YEAR() function, the year is extracted from the date. 
![image](https://user-images.githubusercontent.com/67409852/134751026-51b1b341-ee73-447d-9f07-a47394100963.png)

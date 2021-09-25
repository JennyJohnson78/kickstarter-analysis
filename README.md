# Kickstarter Analysis
## Overview of the Project
Louise is interested in starting a fundraising campaign for a theater project and is seeking information on various kickstarter campaigns. She wouldlike more information on the statistics of campaigns based on category and subcategory, outcomes based on launch date and end time, as well as more specific information on theater outcomes by launch date and outcomes based on goals. The purpose of this analysis is to help Louise determine how well her theater campaign would fare if she were to launch one by looking at the success and failure of similar fundraisers, as well as when she should launch her campaign and what the goal should be.

## Analysis of Theater Outcomes by Launch Date
For the analysis of Theater Outcomes by Launch Date, the first thing to do is create a column in the spreadsheet of Kickstarter data in order to separate the years from the dates in column Date Created Conversion column. The Date Created Conversion column takes the Unix timestamp data in column launched_at and converts it to a readable format, using the equation
```
=(((J2/60)/60)/24)+DATE(1970, 1, 1)
```
Using the YEAR() function, the year is extracted from the date. 

![image](https://user-images.githubusercontent.com/67409852/134751026-51b1b341-ee73-447d-9f07-a47394100963.png)

#### Creating the Pivot Table
From here, a pivot table is created utilizing the data from the entire spreadsheet. This data is filtered by Parent Category (the main category that states what the genre of the kickstarter campaign is), and by year. In order to help Louise, the Parent Category will filter out all categories other than "theater" and years will be set to all.

![image](https://user-images.githubusercontent.com/67409852/134751214-3e9c15dc-5ccd-4061-8e54-b5c184b43e35.png)

Then, outcomes is placed in the columns field, date ended conversion is placed in the rows field, and count of outcomes is placed in the values field.

![image](https://user-images.githubusercontent.com/67409852/134751344-bbafb7d5-e4bb-4630-986b-7d8d8b363c99.png)

Next, the column labels are filtered to only show successful, failed, and canceled campaigns in descending order so successful campaigns are displayed first, then the row column is filtered to show months.

![image](https://user-images.githubusercontent.com/67409852/134751488-85aa8ba5-2b03-49c1-a77c-13a2098d6195.png)

From this table, our line graph can be constructed.

## Analysis of Outcomes Based on Goals
For the analysis of Outcomes Based on Goals, a new worksheet is created and the following columns are created : goal, number successful, number failed, number canceled, total projects, percentage successful, percentage failed, and percentage canceled. In the "goals" column, a range of dollar amounts is added to aid in this analysis:

![image](https://user-images.githubusercontent.com/67409852/134752034-69fa5dfe-40e4-4c7d-880f-721fa3fad139.png)

From here, the anaysis starts by using the COUNTSIF() function to fill in the "number successful", "number failed", and "number canceled" columns. In this analysis the outcomes column (F), the goals column (D), and the subcategory column (R) from the Kickstarter worksheet is used to fill in the table.
```
COUNTSIF(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, "<1000", Kickstarter!$R:$R, "plays")
```
For the entire successful column, the word "successful" is used, for the failed column, the word "failed" replaces the word "successful", and for the canceled column the word is replaced by the word "canceled". The subcategory will stay as "plays" for all calculations. When a range is used for the goal, the function is changed:
```
COUNTSIF(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, ">1000", Kickstarter!$R:$R, "plays", Kickstarter!$D:$D,"<=4999")
```
#### Calculating the Sum and Percentages
At the end of the function, there is now the condition that the goal has to be equal or lesser to 4999, so the range is now 1000 to 4999. The SUM() function is then used to calculate the number of total projects for the goal. 
 
 ![image](https://user-images.githubusercontent.com/67409852/134752425-1a22165f-8c4b-4468-86da-9ce8ace41a46.png)
 
 After plugging in all the functions, the table should be populated:

![image](https://user-images.githubusercontent.com/67409852/134752453-75c9f24f-ec56-4a13-ae81-1d4875a986f3.png)

The last thing to do to prepare for the creation of the line graph is to calculate the percentages of the successful, failed, and canceled campaigns for every goal range off of the total number of campaigns.

![image](https://user-images.githubusercontent.com/67409852/134752602-639e59a6-4842-4fd7-a876-5a9f7e46e57d.png)

Now our table is complete and ready for the creation of the line graph.

![image](https://user-images.githubusercontent.com/67409852/134752640-fc783f5d-6f5e-4365-8243-dc3ac2c22b30.png)

## Challenges
A challenge of analyzing this data was making sure all the values in the table for the Outcomes Based on Goals analysis was correct. A lot of zeroes appeared in the table, so to make sure this was accurately reflecting the data, filters had to be applied to the outcomes and subcategory columns in the Kickstarter worksheet to make certain there were no canceled plays. After manually checking this, it was revealed the table was indeed correct. Filters were then removed.

## Results
![image](https://user-images.githubusercontent.com/67409852/134755395-d300128b-3da7-407c-964c-384649c66d0d.png)

Some conclusions that can be drawn about the Theater Outcomes by Launch Date analysis is that successful theater campaigns are launched in the summertime, with the most successful months being June, July, and August. While more theater campaigns also fail during this time, the amount of successful campaigns to failed campaigns is almost 2:1. I would suggest to Louise that she begin her kickstarter campaign during the summer months.

![image](https://user-images.githubusercontent.com/67409852/134755505-cf458e29-cc57-4b4e-b778-007e1ae158a3.png)

Some conclusions that can be drawn about the Outcomes Based on Goals analysis is that the most successful theater campaigns are those with a more modest goal. The overall trend shows that campaigns between less than $1000.00 to around $10,000 fare the best. Almost all fundraisers from $35,000 to over $50,000 fail to meet their goals. With this information, I would suggest that Louise keep her goal to under $10,000 or risk the possibility of not having her campaign fully funded.

#### Limitations
A limitation this dataset has is that it doesn't take into consideration how certain titles might do better in specific cities. For instance, while category, subcategory, and country are analyzed, it would be interesting to see how a play with the same title would do in two different cities that are in two different locations within the same couuntry. Do bigger cities attract more big name plays? Do smaller cities garner less contributions, thus making the ability to reach a goal more difficult. More detailed data could answer more questions for Louise, thus making it a limitation.

#### Other Possibilities
Another possibility to provide more insight to Louise would be to make a visualization that would show the success, failure, and cancelation rates of theater kickstater campaigns by deadline. We have the data, so this is more data we could analyze to help Louise determine how long her campaign should run for. Do shorter campaigns that are successful have more momentum in the beginning, middle, or end of their deadline? Do canceled or failed campaigns never really get "off the ground" and are thus cut short? These are more questions we could find answers to for Louise. 

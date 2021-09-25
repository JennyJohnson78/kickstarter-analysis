# Kickstarter Analysis
## Overview of the Project
Louise is interested in starting a fundraising campaign for a theater project and is seeking information on various kickstarter campaigns. She wouldlike more information on the statistics of campaigns based on category and subcategory, outcomes based on launch date and end time, as well as more specific information on theater outcomes by launch date and outcomes based on goals. The purpose of this analysis is to help Louise determine how well her theater campaign would fare if she were to launch one by looking at the success and failure of similar fundraisers, as well as when she should launch her campaign and what the goal should be.

## Analysis of Theater Outcomes by Launch Date
For the analysis of theater outcomes by launch date, the first thing to do is create a column in the spreadsheet of Kickstarter data in order to separate the years from the dates in column Date Created Conversion column. The Date Created Conversion column takes the Unix timestamp data in column launched_at and converts it to a readable format, using the equation
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
For the analysis of theater outcomes based on goals, a new worksheet is created and the following columns are created : goal, number successful, number failed, number canceled, total projects, percentage successful, percentage failed, and percentage canceled. In the "goals" column, a range of dollar amounts is added to aid in this analysis:

![image](https://user-images.githubusercontent.com/67409852/134752034-69fa5dfe-40e4-4c7d-880f-721fa3fad139.png)

From here, the anaysis starts by using the COUNTSIF() function to fill in the "number successful", "number failed", and "number canceled" columns. In this analysis the outcomes column (F), the goals column (D), and the subcategory column (R) from the Kickstarter worksheet is used to fill in the table.
```
COUNTSIF(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, "<1000", Kickstarter!$R:$R, "plays")
```
For the entire successful column, the word "successful" is used, for the failed column, the word "failed" replaces the word "successful", and for the canceled column the word is replaced by the word "canceled". The subcategory will stay as "plays" for all calculations. When a range is used for the goal, the function is changed:
```
COUNTSIF(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, ">1000", Kickstarter!$R:$R, "plays", Kickstarter!$D:$D,"<=4999")
```
### Calculating the Sum and Percentages
At the end of the function, there is now the condition that the goal has to be equal or lesser to 4999, so the range is now 1000 to 4999. The SUM() function is then used to calculate the number of total projects for the goal. 
 
 ![image](https://user-images.githubusercontent.com/67409852/134752425-1a22165f-8c4b-4468-86da-9ce8ace41a46.png)
 
 After plugging in all the functions, the table should be populated:

![image](https://user-images.githubusercontent.com/67409852/134752453-75c9f24f-ec56-4a13-ae81-1d4875a986f3.png)

The last thing to do to prepare for the creation of the line graph is to calculate the percentages of the successful, failed, and canceled campaigns for every goal range off of the total number of campaigns.

![image](https://user-images.githubusercontent.com/67409852/134752602-639e59a6-4842-4fd7-a876-5a9f7e46e57d.png)

Now our table is complete and ready for the creation of the line graph.

![image](https://user-images.githubusercontent.com/67409852/134752640-fc783f5d-6f5e-4365-8243-dc3ac2c22b30.png)

## Challenges

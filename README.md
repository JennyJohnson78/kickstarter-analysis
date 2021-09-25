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

### Creating the Pivot Table
From here, a pivot table is created utilizing the data from the entire spreadsheet. This data is filtered by Parent Category (the main category that states what the genre of the kickstarter campaign is), and by year. In order to help Louise, the Parent Category will filter out all categories other than "theater" and years will be set to all.

![image](https://user-images.githubusercontent.com/67409852/134751214-3e9c15dc-5ccd-4061-8e54-b5c184b43e35.png)

Then, outcomes is placed in the columns field, date ended conversion is placed in the rows field, and count of outcomes is placed in the values field.

![image](https://user-images.githubusercontent.com/67409852/134751344-bbafb7d5-e4bb-4630-986b-7d8d8b363c99.png)

Next, the column labels are filtered to only show successful, failed, and canceled campaigns in descending order so successful campaigns are displayed first, then the row column is filtered to show months.

![image](https://user-images.githubusercontent.com/67409852/134751488-85aa8ba5-2b03-49c1-a77c-13a2098d6195.png)

From this table, our line graph can be constructed.



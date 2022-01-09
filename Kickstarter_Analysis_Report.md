<!-- Strong-->

# Kickstarter Analysis
<!-- Horizontal Rule-->

## Overview and Purpose of Project

### Purpose
The purpose of this Data Analytic exercise is to assist Louise with a detailed review of a large excel Kickstarter dataset comprising a series of fundraising campaigns; to determine the Theater outcomes from the perspective of launch dates and funding goals.

## Analysis and Challenges
In reviewing and ultimately analyzing Louise's Kickstarter dataset, a process approach was taken thus:

### Initial Review of Dataset:
<!--UL-->
* First, a high-level review was done to get a sense of the data regarding the dataset's number of columns and rows. This was done to understand the data types and determine whether the data was readable or would need to be converted before progressing further with the analysis.

<!--Links-->
<!--UL-->
* Because the Kickstarter dataset was so large, an investigation was done to precisely establish the number of columns and rows. This was done by utilizing various keyboard shortcuts, combining keyboard keys such as CTRL/right or down arrow keys to get a quick idea of the dataset's number of rows and columns. It was established that Louise's data is stored in rows 1 through 4115 and in columns A through N. 
  
* Next, it was necessary to determine what type of data was present in Louise's dataset. Upon closer examination of the dataset, it was found that some of the columns contained text while other columns contained numbers. Furthermore, the numbers were not in the same format; there were dates and monetary units. But more importantly, the data types were set to General; as the default format for column data in excel. Thus, the data format was changed to reflect the correct format more accurately.
  
* Lastly, checks were made to determine if the data was in a readable format. This is a common challenge in data analytics, where data would sometimes need to be converted to make it readable to Humans. Such was the case with Louise's Kickstarter dataset, where the Deadline and Launched_at columns (I&J) contained Unix timestamps rather than dates in a standard format. Hence, the [timestamp converter](https://www.epochconverter.com
"timestamp converter") tool was used to convert these dates into a standard Human readable format and stored them in two newly created columns, "Date Created Conversion" and "Date Ended Conversion," before progressing further analysis. A third column "Year" was then created to extract the year only.

<!--UL-->
### Organization of the Data to generate insights:

* This was achieved by utilizing filters, formatting, and freezing specific columns and rows; thus, filters were applied to column headers, particularly for the Goal, Pledge, and Outcomes columns, where the Outcomes column was sorted in descending order. In addition,  the top Row (header) of the Kickstarter sheet tab was frozen to allow portions of the spreadsheet (header) to be locked in place and displayed regardless of the part of the sheet being examined at any point in time.
  
* Next, conditional formatting was applied to the Outcomes column to customize the appearance of the cells based on the four categories; Successful, Failed, Canceled, and Live. This allowed each cell to be filled with a different colour, which enabled the user to obtain information quickly, for example, whether a Campaign Failed or was Successful. This was achieved by highlighting the Outcome Column and clicking the "Conditional Formatting" button on the toolbar ribbon and navigating to "Highlight Cells Rules" through "Equal to," and setting the colour parameters for the four outcomes categories. 
   
* Furthermore, additional columns were added to the Kickstarter worksheet to assist with greater visibility of the outcomes. Thus, the Percentage Funded column was added, wherein the "ROUND" formula "=ROUND (E2/D2*100,0" was applied to determine how much of the campaign's Goal was achieved. Data from the Goal column (D2:D4115) and the Pledge column (E2:E4115) was used to find the Percentage funded. As done before, conditioning formatting was again applied using a new set of rules to change the colour of the cells based on minimum or maximum values, which resulted in a colour-shaded reference for the Percentage Funded column.
   
* An additional column was added to determine the "Average Donations" per campaign and to help Louise understand how much money was donated by people historically. The "ROUND" formula was again deployed, albeit a modified version of accounting for errors, thus "=IFERROR(ROUND(E2/L2,2),0)", to act on the variables contained in columns E (Pledge) and column L (backers_count).
<!--UL-->
### Splitting Category and Subcategory into two distinct columns: 
* Before diving into Pivot tables, first, the column "Category and Subcategory" was split into distinct columns and named "Parent Category" and "Subcategory" to generate more details and additional data to use in the analysis. This was achieved by copying (CTRL+C) the "Category and Subcategory" column pasting (CTRL+V) into a new column, followed by clicking the Data tab, then the "Text to Columns" button and selecting the "Delimited" option, then the "Tab" followed by a backslash (/) and then selecting "Text" for the "Column data format."  
  
### Analysis of Outcomes Based on Launch Date
<!--UL-->
#### Parent Category Analysis - USA: 
* In addition, further analysis using a pivot table was introduced as a separate workbook titled "Category Statistics" to assist in uncovering trends or links based on country outcomes. This was achieved by adding a stacked bar chart with the Parent Category Outcome. This allowed further analysis of the outcomes based on the Theater Campaign, filtered by country only. For example, it was noted that the US had recorded 525 successful theater Kickstarters. Refer to the bar chart titled "Parent Category Outcome."  

#### Subcategory Analysis – Great Britain:
* Similarly, another chart was created, in this instant for Subcategories. This was done by focusing the analysis on the theatrical productions, where a pivot table and chart were made simultaneously using the Stacked Column option to display the results. When filtered by country, the results show that for the US, over 3000 Kickstarter campaigns were done, while just over 600 Kickstarter Campaigns were done in Great Britain (GB). Further, the "Theater" category was the most successful in GB of the Campaign categories assessed. 

#### Parent Category - Time Analysis:
* Having analyzed different categories and subcategories of data, comparing countries of origin to provide additional insight into the Kickstart Dataset, the time dimension was also considered to determine whether the length of a campaign makes a difference in determining success. Another pivot table was created, filtering by parent category and years, with the "outcome" as the column value, the Row with the "Date Created Conversion," and the Values also with the "outcome." A pivot chart was then created to display the result of the pivot table graphically. It was noted that May and June both had a great success rate, while January, June, July, and October had primarily the same number of failed campaigns. 

#### Use of VLOOKUP to pull specific information from the primary dataset:
* As a continuation of the robust dataset analysis, VLOOKUP, another powerful data analytics tool, was deployed to pull specific information from the Kickstarter sheet for examination. In this regard, five plays from the Edinburgh Festival Fringe: Be Prepared, Checkpoint 22, Cutting Off Kate Bush, Jestia and Raedon, and The Hitchhiker's Guide to the Family were analyzed to determine whether Kickstarter funded them. Thus, to perform this analysis, all the titles of interest were included in a new sheet called "Edinburgh Research" and listed under the heading "Name" in column A of the "Edinburgh Research" sheet. While columns B, C, D, E, and F were titled "Blurb," "Goal," "Pledge," "Average Donation," and Number of Backers," respectively. In cell B2 the VLOOKUP formula "=VLOOKUP (A2, Kickstarter! B: C, 2, FALSE" was used to populate column B (Blurb). Similarly, the VLOOKUP formula was again used in all the other columns, with the relevant modification to pull data from the Kickstarter sheet to populate the Goal (=VLOOKUP (A2, Kickstarter!B:E, 3, FALSE), Pledge (=VLOOKUP(A2, Kickstarter!B:E, 4, FALSE), Average Donation (=VLOOKUP(A2, Kickstarter!B:P, 15, FALSE) and the Number of Backers (=VLOOKUP(A2, Kickstarter! B:L, 11, FALSE) columns, respectively. The results are included in tab "Edinburgh Research" as part of the excel file accompanying the report.
   
#### Measures of Central Tendency of the Dataset:
* To further enhance the findings for the report, a descriptive statistical study was done on the Kickstarter dataset to deepen the analysis further and get a better understanding of the dataset by checking the distribution of the data, measures of spread, and measures of central tendency. Thus, the Mean, Median, Standard Deviation, Upper Quartile, Lower Quartile, and the IQR of the "Failed" versus "Successful" Goal and Pledge amounts were calculated and analyzed. This was achieved by comparing the statistics of the Kickstarter Campaigns that succeeded versus those that failed. Thus, all previous filters were cleared from the primary dataset, and new filters were introduced on the subcategory column for "plays," on the country column for "US," and on the outcome column for "Successful" and "Failed," respectively. Based on the statistical analysis, significant values are skewing the distribution. The standard deviations (refer to the table..) for both the Pledge and Goal are all roughly twice as much as the IQR values, except for the failed Kickstarter, where the standard deviation is almost three times as much as the IQR. This indicates that there are "Failed" Kickstarter data with high values. The mean of each distribution is around the 3rd quartile, and the standard deviations are larger than the mean, which indicates the values below the mean are considered close to the center. 
 <!--Strong--> 
 <!--Images-->
### Theater Outcome vs. Launch Date:
* Diving deeper into the analysis of the Kickstarter dataset, Pivot Tables and Pivot charts were used to condense the data into a summary to interrogate the data further, but more specifically, to satisfy deliverable #1 of this exercise, based on the Theater category filter, i.e., Theater Outcomes vs. Launch. This was achieved by creating a pivot table to be able to filter by "Parent Category" and "Year," with Rows set to "Date Created Conversion," Columns set to "Outcomes," and Values set to "Count of Outcomes." See Pivot table showing Theater Outcomes by Launch Date. In fulfillment of Delivery #1 of this exercise, filters were used to summarize the data in the pivot table to display the Theater category only, which was used to produce a pivot chart to show the Theater Outcomes vs. Launch. Refer to line chart below: 

![Theater Outcomes Base on Launch Date](https://github.com/Brentnol/Kickstarter-Challenge/blob/main/Resources/Theater_Outcomes_vs_Launch.png)

 <!--Strong-->   
### Analysis of Outcomes Based on Goals:
* For this analysis, the following COUNTIFS command was used for "Successful" Kickstarter campaigns: (= COUNTIFS (Kickstarter! $R$2: $R$4115,"=plays," Kickstarter! $F$2: $F$4115, "Successful," Kickstarter! $D$2: $D$4115,"<1000"), and was modified accordingly for the "Failed" and "Canceled" campaigns respectively, over a predetermined range of data. Thus, the command was used to determine the "Outcomes" based on "Goals." This was achieved by creating a new sheet within the Kickstarter workbook and renaming the tab "Outcomes Based on Goals" as shown in the workbook accompanying this report, with a Goal ranging from values less than 1000, to values greater than and equal to 50,000. The SUM command (=SUM(B2:D2) was then used to calculate the total outcome for "Successful," "Failed," and "Canceled" campaigns over the same range as mentioned earlier. The outcome values for "Successful," "Failed," and "Canceled" were then expressed as a percentage of the total amount for "Plays" and displayed in a line chart below:

![Outcomes Based on Goals](https://github.com/Brentnol/Kickstarter-Challenge/blob/main/Resources/Outcomes_vs_Goals.png)
 <!--OL--> 
### Challenges and Difficulties Encountered

1.	Initially, learning the COUNTIFS command and getting it right to ensure the resulting chart was as expected was a challenge. However, over time, I was able to master this command to produce the desired results.

2.	Getting the PIVOT Table right was at first a bit of a challenge. But after redoes and tweaks, I got the PIVOT table and subsequent chart to work perfectly.

3.	The Unix timestamps, which speaks to the readability of data, was a new concept for me going into this exercise and thus an initial challenge. This concept was later explained in module one and during the virtual class. 

4.	My first exposure to VLOOKUP, another power analytic tool, was through module 1. However, I applied this new knowledge of excel in challenge 1.

## Results/ Conclusions:
<!--OL-->
### Outcomes based on Launch Date:
1.	The month of May was, by comparison, the most successful month for the launch of the Kickstarter campaign.

2.	The peak periods for failed Kickstarter campaign results were noticeably constant for January, June, July, and October.  
### Outcomes based on Goals:
1.	Kickstarter campaigns for values less than 1,000 had an almost 80% success rate compared to values greater than 45,000, which had a 100% chance of failure. 

### What are some limitations of this dataset?
* Potential Outliers can inaccurately skew the dataset: Some large values within this dataset are potentially skewing the distribution.
  
* The standard deviations are all approximately twice the size of the IQR in each distribution
   
* The failed Kickstarters standard deviation is closer to three times the IQR
  
* Dates (Launch at and Deadline) were not in standard readable time. 
  
* Category and Subcategory should be listed in separate columns for ease of analysis
  
* The data format should be consistent with the type of data being stored in each cell
  
### What are some other possible tables and/or graphs that we could create?
* Table showing the various Category Statistics and charting the Outcomes with respect Successful, Live, Failed and Canceled campaigns.
  
* Box and Whisker Plot define potential Outliers in the dataset, including performing other relevant analyses.
  
* Table and chart of subcategory statistics
   
* Table of descriptive statistics

# VBA-Challenge

## Overview of Project

-The purpose of this project was to analyze information on group of stocks from the years 2017 and 2018. This was completed by coding VBA to automate tasks and quickly provide information on which stocks to potentially invest in. The second purpose was to use refactoring to make the code more efficient and improve the time it takes to run the analysis. The data that was output contains two sets of data over two years (2017 and 2018). The results were pulled from two worksheets that contained stock information for twelve companies. The information was the ticker of the company, the date of exchange with the price at open, the highest and lowest price for the day, the price at close, the adjusted close and the volume traded. From there, the macro provided the results for the year for the company including the ticker, total daily volume exchanged and the rate of return for the given year the user inputs.

## Results

My analysis began with a collection of available Kickstarter data which was combed through for errors, dates converted to be legible and additional columns made for easier categorization. When looking at campaign statuses and the time of year they started, a pivot table was used. The pivot table was filtered looking at only theater projects from the data and then separated in the table by months and successful, failed, and canceled campaigns as the results. Based on this analysis the best time to start a Kickstarter campaign for a theater project is in May. A campaign should not be started during the months at the beginning or end of the year.
![Outcomes Based on Launch Date Analysis](Resources/Theater_Outcomes_vs_Launch.png)


### Analysis of Outcomes Based on Goals
The second analysis looked at the goal of a project ranging from less than $1,000 to greater than $50,000 using increments of $5,000 as the scale. The scale populated with data that fit the parameters defined COUNTIF function into successful, failed, and canceled then the percentage rate for those statuses were considered.  This analysis tells us the most successful theater Kickstarter campaigns running a goal amount of less than $14,999 have a greater than 50% chance of succeeding with. Higher campaigns are more likely to fail.
![Outcomes Based on Goals Analysis](Resources/Outcomes_vs_Goals.png)

### Challenges and Difficulties Encountered
No challenges were, presented during the analysis. Some possible challenges that could be present are incorrect categorization from faulty data entry by the analyst or whom initiated the campaign, outliers (i.e. unrealistic goals) within the funding received or needed, incomplete data, the information of those who donated, and if the campaigns were shared or advertised over the internet or different mediums. 

## Summary

-Refactoring our existing code shows these advantages and disadvantages. Luckily, no new bugs or errors are introduced. However, the time difference was slightly better under the original code where it doesn’t make a difference. A larger project may show a significant advantage to either the original or refactored code. Refactoring does have the benefit of making the coding more organized and easier to read. I had a slight issue with getting the button to work and within the loop and the organization on the coding and highlighting problem areas made it easy to resolve.


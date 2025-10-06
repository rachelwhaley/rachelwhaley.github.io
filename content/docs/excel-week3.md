---
weight: 300
title: "Week 3: Charts and Tables"
description: "Visualize data in Excel"
icon: "article"
date: "2025-10-01T16:30:12-07:00"
lastmod: "2025-10-06T16:30:12-07:00"
draft: false 
toc: true
---

---

For this week's tutorial, we'll review formulas including XLOOKUP, and then learn about creating tables and charts using data about a fictional podcast network.

## Review from last week

So far, we've covered formulas, including row-based formulas, summary formulas, XLOOKUP, and cumulative formulas. Let's refresh with a few examples:

1. On the Campaign Participation sheet, add a column to bring in each show’s monthly downloads number, using XLOOKUP​
2. Then, use a row-based formula to calculate the monthly revenue for each row in campaign_participation​
    * Hint: Revenue = CPM*(downloads/1000)​
3. Add a Cumulative Revenue column to the Campaign Participation sheet

### To download the data

*This is the same dataset we used in last week's tutorial!*

1. Click [here](https://uscedu-my.sharepoint.com/:x:/g/personal/whaleyr_usc_edu/EcsFaucTgFhBvQAqEk14tY8BsmYRKyGB5pY60GszZQMKBA?e=dt2dyB) to download this week's data source, which is data from a fictional podcast network.
2. You'll need to sign in with your USC Microsoft account to access the file
3. Once open, click **File**
4. Choose **Create a copy** or **Download** so that you can add your formulas to your own copy during the rest of the session!

## Static Summary Tables
These are tables that use formulas to summarize a larger dataset. We actually created a few very simple summary tables in Week 1! This week we'll add more formulas to them. Some best practices for summary tables:

* Clear header for every column​
* Format numbers​ thoughtfully
    * Dispay currency or units as needed​
    * Display comma separators if the values are large
    * If it’s not fractional, don’t display decimals​
* Use Format as Table on your final product

**Let's try it out:** Create a summary table by category with these steps:​
1. Select all the categories and paste them into the Summary tab​
2. Use the Remove Duplicates tool from the Data ribbon to create a list of categories​
3. Add a column called `# of Shows` and display how many shows are in each category using COUNTIF​
4. Add a column called `Average Monthly Downloads` and display the average monthly downloads for each category using AVERAGEIF​
5. Sort by the average downloads, descending ​
6. Format as table, update number formatting, and make sure all columns have clear headers

## Charts

Charts help visualize the data from your summary table. There are many customization options for charts in Excel.

**Let's try it out:** Create a chart to visualize data from our table.
1. Select all data in your table
2. Insert > choose the Bar Chart
3. A new section of your ribbon will pop up called `Chart Design`. Click `Select Data`
4. In the pop-up, under series, click Average Downloads and click `-` at the bottom, then click `OK`
5. From the ribbon, click `Add Chart Element` > `Data Labels` > `Inside End`
6. Double-click the show title to make it more descriptive, something like `Network Shows by Category`

You can also change the chart type once it's created from the Chart Design ribbon -- try clicking `Change Chart Type` and switching to a line or pie chart! 

## Pivot Tables
Pivot tables are a spreadsheet tool that accomplishes the same thing we just did, but way more easily and faster! ​
* The formulas we just did are conceptually the same thing that the pivot table will do​
* AND, pivot tables add a lot of helpful other features! ​
    * Quickly change summary without re-writing a formula​
    * Change display format​

**Let's try it out:** Create a PivotTable to show the same result we got in our static table (for each category, average number of downloads, and total number of shows)​
1. Create your Pivot Table
    1. Select all your data​
    2. Click one cell of your data, then Cmd-A / Ctrl-A​
    3. Insert -> PivotTable​
    4. Double-check your range makes sense​
    5. Choose PivotTable location (usually new worksheet)​
2. Select your fields
    1. Drag and drop `Category` under Rows 
    2. Drag and drop `Monthly Downloads` under Values. Click the `i` next to it and swap from Sum to Average
    3. Drag and drop `Podcast Title` under Values
3. Change the count of shows column to display the percent of total
    1. Right-click any value in that column in your pivot table
    2. Choose `Show Values As` > `% of Grand Total` ​
4. Sort the categories in order of the most downloads
    1. Click the dropdown next to `Row Labels` in your pivot table
    2. Change `Sort by` to `Average Monthly Downloads`
    3. Choose `Descending` to get the largest values at the top

## Pivot Charts

A pivot chart is dynamically connected to a pivot table, making them more flexible and easier to use for data that's changing or being updated over time.

**Let's try it out:** Create a pivot chart from your pivot table​
1. Select any cell in your pivot table, then go to the Insert ribbon and choose `PivotChart`
2. From the Field List on the right, remove `Average Monthly Downloads`. Notice what happens to your pivot table! 
3. Sort your pivot table by number of shows descending. Notice what happens to your pivot chart! 
4. Click into your chart, then click `PivotChart Design` in the ribbon. Here you can edit all the same design elements as a static chart, like the Chart Type, Layout, and Colors. Tweak these options until you have a chart you like​
3. Double click on the chart's title and give it a descriptive title​

## Adding or editing data in a pivot table

If you add or edit any data in the source sheet of your pivot table, the chart will not automatically update until you refresh .

If you add rows to your source data, use Change Data Source in the ribbon to update the range​. Once the pivot table is refreshed, the pivot chart will auto-update!​

**Let's try it out:** 
1. On the shows source sheet, use Edit > Find > Replace to change the cells “Technology” to “Tech”​
2. Refresh your pivot table to reflect the change​
    * Click the Refresh button in the Analyze ribbon *(Excel only! GSheets automatically updates)​*
3. Add a row to your dataset with a fake podcast and change the data source so that it’s included in your pivot table​
4. Go back to your static table from part 1 – notice the error?​

### Level up! 

* Find another dataset to practice with (see suggestions in [Week 1](../docs/excel-week1.md))
* Resources to learn more [here](https://digital-lounge-excel.carrd.co/#learn-more)

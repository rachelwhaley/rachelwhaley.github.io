---
weight: 200
title: "Excel Part 2: Combine & Visualize Data"
description: "Build your data analysis toolkit"
icon: "article"
date: "2025-09-26T16:30:12-07:00"
lastmod: "2025-09-29T16:30:12-07:00"
draft: false 
toc: true
---

---

For this week's tutorial, we'll review what we learned last week (using data on the most popular content on Netflix) and then learn some new, more advanced formulas using data about a fictional podcast network.

**Reminder from last week!** Whenever you start typing in a function name, Excel will provide a helpful pop-up to show you how many inputs you'll need and what they are. For a more detailed description, go to the View menu (not the ribbon) and click Formula Builder, which will give you a sidebar with more info on what each argument is.

## Advanced Formulas

Moving on to today's topic, advanced formulas!

### To download the data
1. Click [here](https://uscedu-my.sharepoint.com/:x:/g/personal/whaleyr_usc_edu/IQBy5Z6QY8OPTJ8Wz0ZfgqlVAT-7czOb-_WdfHB7DH3UzkQ?e=nq9B3r) to download this week's data source, which is data from a fictional podcast network.
2. You'll need to sign in with your USC Microsoft account to access the file
3. Once open, click **File**
4. Choose **Create a copy** or **Download** so that you can add your formulas to your own copy during the rest of the session!

## XLOOKUP

Imagine you have a list of all the coffee orders at a cafe (order number and items ordered, but no price info). On the menu, you have each item and its price. You want to find out the total revenue of the cafe. 

To solve this problem by hand, you'd look at each item in each order, find that item on the menu, find its corresponding price, and jot it down. Then you'd repeat that for each item all the way down the list.

This type of question is an excellent use case for the powerful formula `XLOOKUP`.

Given a value to search for, XLOOKUP searches for that value (your "key") in another range​. It returns any value from the range that corresponds to that key (e.g., is in the same row where it found the key). 

This function takes 4 arguments in this order:
* Lookup Value​ (what's your "key" to go find in the other dataset)
* Lookup Array​ (what column should you look for the key in)
* Return Array​ (what column should you look for your result in)
* Optional: If not found​ (in some cases it's helpful to include text like "Not found")

### Ordering values
XLOOKUP will return the first value it finds in the list​. In cases with multiple values, it's a good idea to sort the lookup range!​

Recommended method:​
1. Click `Sort & Filter​` from the Home ribbon
2. Click `Custom Sort…` ​
3. Add a second level of sorting​

**Let's try it out:** Add a column to the `shows` sheet in your workbook called “Upload Date”:​
* Use XLOOKUP​ to populate that column with the date of that show's most recent episode upload
* Be sure to get the earliest date, in the case of multiple uploads​
* Hint: sort the data you are looking up to!​

**More practice:** Add two columns to the Campaign Participation table using XLOOKUP:​
* Show title, from the shows sheet​
* Personal endorsement, from the campaigns sheet​
    * Add another nested formula: If this is true, replace the value with “Personal endorsement is required”​ (hint: use the `IF` formula)

### Best practices for lookup formulas
* The lookup array should ideally be a unique identifier, like a case-sensitive ID, or an email address, to avoid incorrect matches​
* If you’re not sure if an ID is unique, use conditional formatting -> Highlight Duplicates in that column to check​
* Make sure your data is sorted based on your use case, if you are going to be returning the first of multiple values​

## Cumulative formulas
* These formulas allow you to keep "running total" style calculations
* For each row, apply a formula to all of the rows preceding and including that row​
* To "glue" the top of your formula range in place, you'll use an absolute cell reference on the first cell in your range, but not on the second cell
    * An absolute cell reference looks like `$B$2` (compared to the reference `B2`)

**Let's try it out:** 
1. On the Campaign Participation sheet, add a column with each show’s monthly downloads number, using XLOOKUP​
2. Then, use a row-based formula to calculate the monthly revenue for each row in campaign_participation​
    * Hint: Revenue = CPM*(downloads/1000)​
3. Add a Cumulative Revenue column to the Campaign Participation sheet

## Static Summary Tables
These are tables that use formulas to summarize a larger dataset. We actually created a few very simple summary tables in Part 1! This week we'll add more formulas to them. Some best practices for summary tables:

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

* Find another dataset to practice with (see suggestions in [Week 1](../docs/excel-part1.md))
* Try asking an AI assistant to create some practice exercises for you! You can try a prompt like this: `Create some exercises and sample datasets for me to learn the xlookup formula in excel. Don't tell me the solution! Create a practice workbook (.xlsx) that I can download to practice writing formulas.`
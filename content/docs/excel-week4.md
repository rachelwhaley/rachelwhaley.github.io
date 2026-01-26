---
weight: 400
title: "Week 4: Dashboards"
description: "Visualize data in Excel"
icon: "article"
date: "2025-10-20T06:30:12-07:00"
lastmod: "2025-10-20T16:30:12-07:00"
draft: true 
toc: true
---

---

For this week's tutorial, we'll combine all the knowledge we've gained so far to create a dashboard to meet client requirements.

So far, we've covered formulas, including row-based formulas, summary formulas, XLOOKUP, cumulative formulas, pivot tables, and pivot charts.
Cumulative Revenue column to the Campaign Participation sheet

### To download the data

*This is a **different dataset**, please download a fresh copy!*

1. Click [here](https://uscedu-my.sharepoint.com/:x:/g/personal/whaleyr_usc_edu/EVU5p7X-WypCslwUe4W7-q4BRxqS27aY8cQVg-s0JEctLQ?e=i3WmVx) to download this week's data source, which is new data from our fictional podcast network.
2. You'll need to sign in with your USC Microsoft account to access the file
3. Once open, click **File**
4. Choose **Create a copy** or **Download** so that you can add your formulas to your own copy during the rest of the session!

## Our project this week

The COO of the podcast network has asked you to create a dashboard to track the company’s top key metrics related to revenue. The dashboard should include these metrics:
1. Monthly downloads by podcast content category
2. The top 5 advertisers in 2025 by revenue
3. Cumulative revenue so far this year, compared to last year
4. One more stat or chart you think the COO might like to see

## Creating components for your dashboard
* Each chart or table in your dashboard is called a component
    * Work on one component at a time
* Sometimes easiest to work on each in its own sheet
* To create a chart, create a pivot table first, to make sure data is grouped correctly 
* To create a single stat (e.g. overall total, average, etc.) you can type a formula directly into a cell
* Add enough labels/titles that you know what each component is
* Don’t worry about colors or specific formatting until all your components are drafted 

**Let's try it out:** This guide won't include specific instructions for each component -- you'll need to work through it yourself! If you need a refresher, take a look through the notes from previous weeks, and ask if you need help. 

Here are a few hints for each component to help you get started! 

### Component #1: Downloads by Category
* Create a Pivot Table
* Option to visualize this as a pivot table or a pivot chart (pie chart)! 

### Component #2: Top 5 Advertisers in 2024 
* Use an `XLOOKUP` formula to bring show downloads
* Use a math formula to get spend 
    * Hint: `Revenue = CPM*(downloads/1000)`
* Create a Pivot Table
* Filter your pivot table by Value > `Top 10` > type in 5 items
* Add a Pivot Chart (horizontal bars)
* Add a Timeline to your pivot chart on campaign month

### Component #3: Cumulative Revenue YoY
* In the 2025 sheet, use DATE formula to convert months to dates (year = 2025)
* In your pivot table, display the revenue sum as a `Running Total of` the campaign month
* Sort both by date
* Create 2 charts (one for each year) and consider adding a slicer by advertiser

### Component #4: Dealer's Choice

Create your own component! Try to use a different kind of table or chart type than the first three components. Some ideas to help you brainstorm:
* What information would you want to know about the network's revenue if you were the COO?
* Which podcasts bring in the most revenue? 

## Learn more

Check out the [resources site here](https://digital-lounge-excel.carrd.co/#learn-more)!

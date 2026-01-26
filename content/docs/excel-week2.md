---
weight: 200
title: "Week 2: Advanced Formulas"
description: "Learn to harness the power of formulas"
icon: "article"
date: "2025-09-26T16:30:12-07:00"
lastmod: "2025-09-29T16:30:12-07:00"
draft: true 
toc: true
---

---

For this week's tutorial, we'll review what we learned last week (using data on the most popular content on Netflix) and then learn some new, more advanced formulas using data about a fictional podcast network.

**Reminder from last week!** Whenever you start typing in a function name, Excel will provide a helpful pop-up to show you how many inputs you'll need and what they are. For a more detailed description, go to the View menu (not the ribbon) and click Formula Builder, which will give you a sidebar with more info on what each argument is.

## Review from last week

This review section refers to the same dataset used in [Week 1](../docs/excel-week1.md). 

### Combining row-based formulas

We'll try this out by creating a (fake) URL for each show, using formulas, written all in a single column, formatted as​: www.netflix.com​ Slash, the name of the show in all lower case, with no spaces​.

**Example:** For the title *Love Is Blind*, we'd want the result to be `www.netflix.com/loveisblind` ​

We'll use 3 formulas for this:
* `LOWER` which makes text all lowercase
* `SUBSTITUTE` which we used earlier to swap Films for Movies; here, we'll use it to swap spaces for an "empty string" (a set of quotes with nothing in between)
* `CONCATENATE​` which "adds" two pieces of text together (to add on the first part of the URL)
​
Hint: start with each formula in a separate column first! ​This way, you can make sure each one creates the desired result, before you combine them all in one cell.

### Combining summary formulas

Next we'll combine some summary formulas to figure out what percentage of these top titles you've seen. The formulas we'll use are:
* `COUNTIF` to count the number of titles you've seen (this works similarly to `SUMIF` from above)
* `COUNTA` to count the total number of titles
* `/` for regular ol' division, to divide our first result by our second result to find our percentage

Be sure to format the cell as %! 

That's it for our review - next up, more formulas.

---

## Advanced Formulas

Moving on to today's topic, advanced formulas!

### To download the data
1. Click [here](https://uscedu-my.sharepoint.com/:x:/g/personal/whaleyr_usc_edu/EcsFaucTgFhBvQAqEk14tY8BsmYRKyGB5pY60GszZQMKBA?e=dt2dyB) to download this week's data source, which is data from a fictional podcast network.
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

### Level up! 

* Find another dataset to practice with (see suggestions in [Week 1](../docs/excel-part1.md))
* Try asking an AI assistant to create some practice exercises for you! You can try a prompt like this: `Create some exercises and sample datasets for me to learn the xlookup formula in excel. Don't tell me the solution! Create a practice workbook (.xlsx) that I can download to practice writing formulas.`
---
weight: 500
title: "Data App with Python Part 1"
description: "Learn how to manipulate data, use functions, and create a basic web app."
icon: "article"
date: "2026-02-07T16:30:12-07:00"
lastmod: "2026-02-09T10:30:12-07:00"
draft: false 
toc: true
---

---

In this tutorial, you'll learn how to leverage Python to perform data analysis and create data visualizations. 

You'll be creating a web app to explore the results of the 2024 Paris Olympics! 

---
## Start using Hex
* Follow the invite link found at [digital-lounge-python.carrd.co](https://digital-lounge-python.carrd.co), if you haven't already
* Click Projects on the left
* Find **Spring 2026 Python Part 1**. Hit the `...` icon on the right side, then hit `Duplicate`
* Add your name to the project title, like `Rachel's Spring 2026 Python Part 1`. This is your personal copy of the workbook to use in today's workshop. 
* Hit `Run all` in the top right to load our dataset into your workspace 

---

## Create an interactive filter

To create the dropdown menu that will allow our audience to filter the results by country:
1. Create a new python cell 
2. Take a look at the countries column in our medallists_data dataset by running: `medallists_data["country"]`
3. Make sure the data is clean by checking for and removing any blank values in this column: `medallists_data["country"].dropna()`
4. Remove duplicate values so that each country is only listed once: `medallists_data["country"].dropna().unique()`
5. Check how many countries we have now that duplicates are removed: `len(medallists_data["country"].dropna().unique())`
6. Put this list in alphabetical order: `sorted(medallists_data["country"].dropna().unique())`
7. Save this list to a variable so that we can access it from another cell: `distinct_countries = sorted(medallists_data["country"].dropna().unique())`
8. Create a new Python cell and type in your variable name to check that your list appears correctly
9. Add an Inputs cell of type **Dropdown**. 
    * Set the Label to "Select a country"
    * Set the Name to `selected_country` 
    * Under Values, Choose an input and select your variable name from the list. 
10. Click the "Add to App Builder" option on this cell
11. Toggle to the App Builder view at the top of your screen and check out your dropdown!  

---

## Add dynamic text 

We'll create several dynamic components on our app that will update automatically based on the selected country. We'll start with the most simple component, a text-based one:
1. Create a new cell of type = Markdown
2. Enter the text: `The selected country is {{ selected_country }}`
3. Run this cell
4. Add this cell to the app builder
5. Toggle to the App Builder view at the top of your screen and test out whether it changes when you toggle the dropdown!

---

## Add summary metrics

We'll add our first few metrics to the app, to answer the question: how many athletes from this country won medals? We'll display this as a number and a percentage.
1. Create a python cell 
2. Find the total number of medallists in all countries using the `len()` formula we used earlier. Save this to a variable called `total_medallists`
3. Next, we're going to filter down the medallists to only those from the selected country. To see how this works, create a new python cell and run `medallists_data[medallists_data['country'] == selected_country]` 
4. Find the total number in this filtered list using the `len()` formula, and save this to a variable called `country_medallists`
5. Next we'll find the percentage. Create a new python cell and run `country_medallists / total_medallists * 100` 
6. This has a lot of decimal points, probably more than we need. Use the `round()` formula to round the result to one decimal place, like this: `round(country_medallists / total_medallists * 100,1)`
7. Save the result to a variable called `country_medallists_percent`
8. Create a new Markdown cell and paste in some text to display our new variables: `**{{ country_medallists }}** athletes from **{{selected_country}}** won medals, out of **{{ total_medallists }}** medallists total — that's **{{ country_medallists_percent }}%** of all medallists.` 
9. Add this cell to the app builder, toggle over to that view and test out the results when you change the dropdown! 

Next we'll display the total number of athletes from the selected country:
1. Create a new python cell
2. Filter the `athletes_data` dataframe by the selected country (**Hint**: This will be very similar to step 3 in the previous section)
3. Save this result to a variable called `country_athlete_count`
4. Create a cell of type **Single Value** 
    * Set Value = your variable name
    * Set Title = `Athletes from {{ selected_country }}` 
    * Set Format = Number
5. Add this cell to the app builder, toggle over to that view and test out the results when you change the dropdown! 

---

## Calculations for more metrics

Next, we'll add a metric to this app that's not directly given in our dataset: the average age of the medallists from the selected country. In order to figure this out, we'll need to do some calculations from the data we have (athletes' birthdates):
1. First, save the date of the 2024 Olympics to a variable by running this in a python cell:
```
import pandas as pd
olympics_date = pd.Timestamp('2024-07-26') # date of Paris Olympics 
```
2. Filter `medallists_data` by the selected country as we've done before, then filter out anyone with a blank birthdate by adding `.dropna(subset=['birth_date'])` to the end 
3. Save this to a variable called `filtered`
4. Format the data in the `birth_date` column as dates by running: `filtered['birth_date'] = pd.to_datetime(filtered['birth_date'])`
5. Add a column called `age` that calculates the age of each medallist at the time of the Paris Olympics: `filtered['age'] = (olympics_date - filtered['birth_date']).dt.days / 365` 
6. Find the average age by running: `filtered['age'].mean()`
7. Use the `round()` function to round this to one decimal place (**Hint**: Look back at how we did this for our percentage metric earlier!)
8. Save the result to a variable called `avg_age_of_medallists`
9. Create a cell of type **Single Value** 
    * Set Value = your variable name
    * Set Title = `Average Age of Medallists` 
    * Set Format = Number
10. Add this cell to the app builder, toggle over to that view and test out the results when you change the dropdown! 

---
## Create your own function

So far, the functions we've used have been built-in to python. We can also create our own functions, to take inputs and return our desired outputs! Let's create our first function, which will return
1. Create a python cell and run:
```
def medal_color(medal_type):
    if medal_type == 'Gold Medal':
        return '🥇'
    if medal_type == 'Silver Medal':
        return '🥈'
    return '🥉'
```
2. In a new python cell, test out your function by running: `medal_color('Gold Medal')`
3. What happens when you run `medal_color('Not a winner')`?
4. How would you adjust the function to only return the bronze medal emoji for the input 'Bronze Medal', and return a sad-face emoji for any other input? 

Now that we have our function, we can apply it to our `medallists_data` dataframe, to add a column containing the correct emoji for each row:
1. Create a python cell and run: `medallists_data['medal_emoji'] = medallists_data['medal_type'].apply(medal_color)`
2. Run `medallists_data.head()` to see a sample of the dataset with your new column added. 


---

## Display a dynamic list

Finally, we'll add a section at the bottom of our web app that lists out each medallist from the selected country: 
1. Create a new python cell that selects just the athlete's name, event, and medal emoji: `medallists_data[['name', 'event', 'medal_emoji']]`
2. Add in the `discipline` column after the name column  
3. Filter this view by the selected country: `medallists_data[medallists_data['country'] == selected_country][['name', 'event', 'medal_emoji']]` 
4. Sort the list by the athlete name by adding `.sort_values('name')` 
5. Save this to a variable called `medallists_display_view`
6. Create a cell of type = Table, and set it to display the `medallists_display_view`
7. Add this cell to the app builder, toggle over to that view and test out the results when you change the dropdown! 

---
## Finalize and publish your app
In the app builder, you can drag-and-drop and re-size each component, then publish it for sharing:
1. Create a layout you like by dragging and dropping components to your preferred layout 
2. Add a header: create a Markdown cell and paste in `## 2024 Olympics Results for {{ selected_country }}`. Add this to the app builder and drag it to the top. 
3. In the upper right, hit `Publish App`
4. Once your app runs and displays a preview, hit the green `Publish App` button 
5. A new icon will appear in the upper right labeled `Go to live published app`. Click this to see your published version! 
6. Back in the App Builder, hit the `Share` button, then change 'Invite Only' to 'Anyone with link'. Then you can share the public app link, add it to your portfolio, etc. 

---

## Up next

In Part 2 of this workshop, we'll add more visualization components to our data app! 

For more learning resources, check out the recommended resources at [digital-lounge-python.carrd.co](https://digital-lounge-python.carrd.co)
---
weight: 700
title: "Prep Data for Analysis with AI Tools"
description: "Use AI tools to collect, organize, and prepare data for analysis"
icon: "article"
date: "2026-03-07T10:30:12-07:00"
lastmod: "2026-03-08T11:30:12-07:00"
draft: false 
toc: true
---

---

In this tutorial, you'll learn how to use AI tools to collect, organize, and prepare data for analysis. 

During this workshop, I'll be demonstrating the use of ChatGPT and Copilot, which are available to the USC community. If you haven't already, follow the instructions from IT Services to access these tools: https://itservices.usc.edu/ai/ 

It's also helpful to have Microsoft Excel downloaded for this workshop. USC provides up-to-date Microsoft applications for students – information about how to download your copy is here: https://software.usc.edu/microsoft-office/

---
## When should I use AI to help prepare data?

Let AI do what it's best at:
* Formatting
* Extracting and aggregating data
* Pattern spotting

So that you can focus on the many steps in data preparation and analysis that still require human judgment: 
* **Validity**: Does this data make sense to use for this situation? Is it from a trusted source?
* **Bias Detection**: What biases may be present in this data (societal, systemic, situational)? 
* **Domain Context**: What questions should be asked? What are the underlying assumptions?

---
## Collecting data

Typically for analysis, data needs to be in either a **tabular** format (e.g., formatted as a spreadsheet or CSV) or in some other machine-readable format (JSON, HTML, etc.). Many data sources are already available in these formats.

When the data you wish to analyze is not in one of those formats (images, audio, etc.) or is spread across multiple files or locations, AI tools can be very useful for collecting and organizing that data to prepare it for analysis. 

#### Combining multiple data sources
Let's start by using AI to help us combine some data on attitudes towards the internet that's published as separate files by country, into a single file that combines data from all countries:
1. Visit the USC Libraries Data Guide: https://libguides.usc.edu/data and click on **Statista** (near the bottom). You should be automatically logged in, or prompted for your USC SSO login.
2. Once logged in, navigate to https://www.statista.com/topics/1145/internet-usage-worldwide/#topicOverview 
3. Scroll down to the section **Attitudes towards the internet**. You'll see data for several different countries listed below.  
4. Select the US dataset and then choose Download As -> XLS (this is Microsoft Excel format)
5. Repeat steps 3-4 for datasets for two additional countries (Japan, UK, China, Mexico, etc. -- you choose!) 
6. Open up those files. You'll notice that they're very similarly formatted, with one sheet of some overview info and one sheet with a single column of statistics.
7. Open up [Copilot](https://m365.cloud.microsoft/chat) and give it a simple prompt to combine these files, something like `combine the data tabs of these spreadsheets into one spreadsheet with a column for each country`. Click the **+** icon and upload the 3 datasets you downloaded.
8. Open up the combined file that it returns, and check it against one of the original files to make sure it's correct. 

#### Unstructured or hard-to-find data
In many cases, data is not published or shared in an aggregated form. AI can help locate various sources and reports to help access this kind of information. For example: 
1. Try `what are the most common themes of the top 100 youtube videos published in the past month?`. Notice that while this specific information is not publicly available, AI can aggregate a few similar sources and provide answers to similar questions.

#### Data stored in non-tabular formats
If the data you want to use is published in a non-tabular format, you can use AI tools to help translate it into a spreadsheet or CSV. For example, let's say we wanted to look at [data from the city of Chicago's municipal recycling program](https://www.chicago.gov/city/en/depts/streets/supp_info/recycling1/Landfill_Diversion_Rates.html). 

Unfortunately, this data is stored as screenshots of data tables, rather than the data tables themselves. If you wanted to graph or compare this data across years, you'll need to get it into a tabular format. Let's try using AI to format it into a usable spreadsheet form to compare across years:
1. Try giving Copilot a prompt like this: `Combine the data tables on this webpages from 2020-2022 into a single spreadsheet: https://www.chicago.gov/city/en/depts/streets/supp_info/recycling1/Landfill_Diversion_Rates.html` 
2. You'll likely run into a few possible limitations here, depending on the tool you're using:
    * The website might block AI tools from scraping content
    * The AI might not be able to process low-quality images 
3. For your next step, try following one of the suggestions from Copilot, which might be something like:
    * Download the images from the site and upload those images directly to Copilot
    * Download the HTML of the site and upload that to Copilot
    * Take a screenshot of the site and upload that to Copilot
4. What limitations do you run into?

--- 

## Cleaning & contextualizing data

Sometimes this step is called "cleaning data", but to do this step most effectively, you need to identify what needs to be "cleaned" vs. what needs to be contextualized. 

Data that may need **cleaning**:
* Data in one field that may need to be divided into multiple fields (e.g., blocks of text that can be divided into discrete pieces)
* Data where formatting is inconsistent or that wasn't validated on collection (e.g., a "State" field that sometimes says "CA" and sometimes says "California")

Data that may need **contextualizing**:
* Lots of blank values in some fields or rows. In these cases, consider why these values might be blank -- were they optional or not applicable? Is there a default that is appropriate to apply to missing values or not?
* Values that are "other"
* Data is missing or unavailable for date or time ranges: is this a random sampling, or there an explanation for this? For example, was data not collected or available due to seasonal weather, a religious holiday, a natural disaster impacting the relevant area, etc.? 

Understanding the "why" behind missing or incomplete data helps determine how to best handle these cases in your analysis. Are there outliers that you should remove before calculating any averages or trends? Is there a missing piece of context you should provide in the narrative accompanying your analysis? Would the analysis be strengthened by collecting additional data or bringing in an additional data source? 

AI is excellent at helping with the **cleaning** category here, but you should avoid cleaning data that instead needs to be contextualized. Instead, use it as a tool to help you identify what needs to be cleaned vs. contextualized: 
1. Open the chat from our Chicago recycling data above, and try some of the following:
    * Ask about missing data: `where does this dataset have missing or unexpected values?`  
    * Ask about some of the zero-values in the data, for example: `why is the yard waste value zero for July-October 2021 and January-May 2022?` 
2. Based on your review of the data and the responses to your prompts, do you think any of this data needs to be cleaned or contextualized? If so, how would you address them? 

Now let's try a deeper dive into actually cleaning a (fictionalized) dataset.
1. Start a new chat in Copilot
2. Download a copy of [this sample dataset](https://uscedu-my.sharepoint.com/:f:/g/personal/whaleyr_usc_edu/IgBC4QdRVPTARrmSdbv0Ep43AfZh5wNRXpybiMUYTOYmv2c?e=x9VG0B) (accessible when logged in with your USC credentials) and open it up in Excel. Do you notice any data quality or context issues that need to be addressed?
3. Upload the file to Copilot and prompt: `Scan this CSV and list all data‑quality issues (types, ranges, invalid values, duplicates, inconsistent categories, likely swaps, units, and formatting). Don’t make any changes—just report and prioritize which issues to fix vs. contextualize.` 
4. Run a column profile by asking: `Profile each column—data type, % missing, unique count, top categories, min/max, suspected outliers—and suggest the minimal set of transformations to make the dataset analysis‑ready.` 
5. Based on the responses to steps **3** and **4**, prompt Copilot to resolve data quality problems by via cleaning, contextualizing, or ignoring the issue. 

---

## Documenting & augmenting data

In data projects, documentation of data sources and how the data should be used is often lacking or left to the last minute. AI tools can help create and maintain this documentation, which will make the results of your project more understandable and trustworthy. A common form of documentation for data projects or pipelines is called a **data dictionary**.  
1. Try a prompt such as `generate a data dictionary for this dataset` and read through the response. Try the same prompt in the Chicago recycling chat from earlier and compare the responses.
2. Try a prompt like `Which fields in this dataset are unclear or lack enough description to be understood?`. Compare this to the data dictionary response and check for any misalignment or overly-confident sections.

You may find that bringing in additional data sources can help contextualize your data (for example, bringing in weather or temperature data could strengthen your analysis of why data is missing or has outliers at certain times of year). AI tools can be a useful brainstorming partner here: 
1. Try a prompt like `what other data sources might be interesting to combine with this dataset for analysis?` and review the results
2. Choose an additional type of data and prompt for steps to find and join that data to your existing dataset, e.g. `help me join seasonal weather data to this dataset`
3. Follow Copilot's steps and add any additional prompts until you get to a dataset with at least 1-2 columns added (for example, temperature and preciptation data from a weather data source)

---

## Analyzing data 

As you move into the analysis phase of your data project, here are some [tips for using AI in data analysis](../docs/ai-and-spreadsheets.md).

---

## Keep learning

Many agents and agentic tools are becoming available. For example, in Copilot, you can try out a variety of agents that are designed for specific use cases -- there are even agents to help you provide more effective prompts to the AI. 

Once your data is ready for analysis, you can use a variety of AI-assisted tools to conduct analysis and visualization of your data. I recommend Hex as a useful tool for integrating AI into your analysis workflow -- check it out via this tutorial to [create a data app with Python](../docs/python-part1.md).
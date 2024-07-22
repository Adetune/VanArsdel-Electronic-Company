# VanArsdel-Electronic-Company

# VanArsdel Electronic Company
# Sales and Market Share Analysis for Year 2017.
## Excel to Power BI Project using ETL Process

![excel-to-powerbi-animated-diagram](assets/images/excel_pbi.png)

#### This is an ETL process as simple as possible where dataset provided which focuses on Sales and Market Share Analysis get extracted, transformed and imported to a Power BI environment.

# Table of contents 

- [Objective](#objective)
- [Data Source](#data-source)
- [Stages](#stages)
- [Design](#design)
  - [Mockup](#mockup)
  - [Tools](#tools)
- [Development](#development)
  - [Pseudocode](#pseudocode)
  - [Data Exploration](#data-exploration)
  - [Data Cleaning](#data-cleaning)
  - [Transform the Data](#transform-the-data)
  - [Create the SQL View](#create-the-sql-view)
- [Testing](#testing)
  - [Data Quality Tests](#data-quality-tests)
- [Visualization](#visualization)
  - [Results](#results)
  - [DAX Measures](#dax-measures)
- [Analysis](#analysis)
  - [Findings](#findings)
  - [Validation](#validation)
  - [Discovery](#discovery)
- [Recommendations](#recommendations)
  - [Potential ROI](#potential-roi)
  - [Potential Courses of Actions](#potential-courses-of-actions)
- [Conclusion](#conclusion)

# Objective 

- What is the crucial pain fact?
  
- Chief Marketing Officer (CMO) wants to know how well VanArsdel product sells within the industry for the year 2017.
- Also, how well VanArsdel electronics doing against their competing product (Natura, Aliqui, Pirum, and Currus) in the industry for the year 2017.
-  What is the ultimate key? 

To create a dashboard that provides insights into the VanArsdel and its competitors market share analysis for year 2017 that includes their 
- Sales by month 
- Sales by manufacturer
- Sales by Segment
- Sales by Manufacturer (groups)
-  Sales by State
- Revenue by category and state

The dashboard sales and marketing analysis allows Chief Marketing Officer (CMO) to gain insight of how well VanArsdel electronic company is doing against its Competitors in the year 2017. Also, identify VanArsdel strength and weakness within the industry.  

## User story 

As the Chief Marketing Officer (CMO) of VanArsdel electronic Company, This dashboard should allow me to gain insight and analyse:
 revenue and unit by month.
-	 revenue by manufacturer
-	-sum of revenue by segment
-	compare VanArsdel sales and revenue with other competitors.
-	show the market shares analysis.
-	sales by State
-	compare revenue by category and state in tabular view.

With this information, I can gain insight and analyse sales revenue across all manufacturers for the year 2017
# Data source 

- What data is needed to achieve our objective?

The dataset provided focuses on sales and market share analysis
in 2017 that includes 
- sales
- product
- geography
- date

   Where is the data coming from? 
Sales data along with details of Product, Date and Geography are available in an Excel workbook provided by VanArsdel Electronic Company. Data from these sources need to be brought together to analyse and report on.

# Stages (ETL)
- Design
- Development
- Testing
- Analysis 



  
# Design 
- What should the dashboard contain based on the requirements provided?
 To understand what it should contain, we need to figure out what questions we need the dashboard to answer:
1.	What is the revenue and unit by month?
2.	What is the revenue by manufacturer?
3.	What is the sum of revenue by segment?
4.	What is the sum of revenue by MonthName and Manufacturer (groups)?
5.	What is the sum of revenue by State and Segment?
6.	 What are the sales by State?

For now, these are some of the questions we need to answers; this may change as we progress down our analysis. 

- What should it look like? 

Some of the data visuals that may be appropriate in answering our questions include:

1. Line and Clustered Column chart
2. Tree map chart
3. Donut chart
4. Stacked area chart
5. Map visual 
6. Matrix visual 


## Tools 


| Tool | Purpose |
| --- | --- |
| Excel | Exploring the data |
| Query Editor | Cleaning, Validation, and analysing the data |
| Manage Relationship | Manage table and Validation |
| Power BI | Visualizing the data via interactive dashboards |
| Github | Hosting the project documentation and version control |


# Development

- Import Data
- Clean Data
- Manage relationship

##  Import Data
- Get Data

## Transform Data
- Clean Data

## Manage relationship
- We need to load data from 4 tables
- We need to ensure the model identifies relationship between these tables.
# Development
## Pseudocode

- What's the general approach in creating this solution from start to finish?

1. Get the data
2. Explore the data in Excel
3. Transform the data in Query Editor
5. Clean the data with Query Editor
6. Load the data into Power BI
7. Manage Relationship in Model View
8. Validation
8. Visualize the data in Power BI
9. Generate the findings based on the insights
10. Write the documentation + Report
11. Publish the data to Github Pages




## Data exploration notes

This is the stage where you have a scan of what's in the data, errors, inconsistencies, repetitions, weird and corrupted characters etc.  
- What are your initial observations with this dataset? What's caught your attention so far?

1. There are 4 tables – (sales, product, geo, date) that contain the data, that is  need for to be brought together to analyse and report on, which signals we have everything needed from the file without requiring to contact the VanArsdel electronic company and Competitors (Natura, Aliqui, Pirum, and Currus) for any more data. 
2. The date table contains the Month column, this is a repetition we do not need Month column - we need to remove Month column from the Date column.
3. The product table contains the Product Name and Product ID is concatenated in Product column, we need to split it to have just the Product Name. -  we need to use Split Column by Delimiter, Enter “-“ in the text area. Product column is split into two columns Product.1 and Product.2. We do not need Product.2 since we already have a ProductID column. Remove Product.2 and Rename Product.1 to Product.
4. We have now transformed all the data in the query editor and then we close and apply to load all the tables into Power BI 

- What do we expect the clean data to look like? (What should it contain? What constraints should we apply to it?)

The aim is to refine our dataset to ensure it is structured, ready for analysis and start to build report. 
- What steps are needed to clean and shape the data into the desired format? 
-Remove unnecessary columns by only selecting the ones needed.
- Only relevant columns should be retained.
- All data types should be appropriate for the contents of each column.
- No column should contain null values, indicating complete data for all records.  
   
## Manage relationship
The model view in Power BI shows how the fact connects with dimension. 
Now that we have loaded data from 4 tables, something is wrong, we have 2 relationships. Notice model view in Power BI is able to identify and create relations between some of the tables we loaded
-	Relation is created between Sales and Product
-	Relation is created between Sales and Geo
However, there is no relationship between Sales and Date
We need to ensure the model identifies relationship between these tables

Image

## Create relationship
We have to ensure that we create relationship successfully before we build a report. In the manner of ensuring that this is right, we found out that there is one more relationship missing that is sales to date. We have to manually create the relationship using the Create Relationship dialogue. Notice now a relationship is created between Sales and Date.

Image

## Validation 
### First Validation
Before building the report, they must have been some form of testing, to validate that the data is correct. That is, the product ID present in the sales table is the similar as the product ID presents in the product table. 
### Second Validation
When we have to manage relationship not that we have date from sales connected to product ID from product but we have validated the cardinalities as seen the process of even reviewing the data. 

## Grouping VanArsdel and its competitors
To compare VanArsdel with the rest of the competitors it is required that we make VanArsdel company a group and for every other group.
Image

 A new field called Manufacturer (groups) is created in Product table.
This simple means from sum of revenue by manufacture chart clearly VanArsdel contributing if not half maybe or slightly the above half or below half of the whole revenue of the entire industry. 
# Visualization 


## Results

- What does the dashboard look like?

![GIF of Power BI Dashboard](assets/images/top_uk_youtubers_2024.gif)

This shows the VanArsdel and its competitors market share analysis for year 2017 so far. 

## DAX Measures

### 1. Total Revenue 
```
    Total Revenue = Sum(Sales[Revenue])

RETURN Total Revenue

```

### 2. Revenue less charge = Sales[Revenue]-1
```
    Revenue less charge = Sales[Revenue]-1

RETURN Revenue less charge

```

### 3.  Total Tax 
```
    Total Tax = SUM(Sales[Revenue]) *0.18

RETURN Revenue less charge

```

### 4.  Total Unit
```
   Total Unit = SUM(Sales[Units])

RETURN Revenue less charge

```

### 5.  Competitors Tax
```
  Competitors Tax = CALCULATE ([Total Tax],'Product'[Manufacturer (groups)] = "Competitors")

RETURN Competitors Tax

```

To see tax paid across califonia 

### 6.   CA Tax 
```
   CA Tax = CALCULATE([Total Tax], Geo[State] = "CA")

RETURN  CA Tax 

```
### 7.  % Comp Tax
```
   % Comp Tax = [Competitors Tax] / [Total Tax]

RETURN  % Comp Tax

```
### 8.   % VA Tax
```
  % VA Tax = 1 - [% Comp Tax]

RETURN  % VA Tax

```
### 9.  SPLY (Same peroiod last year)
```
SPLY = CALCULATE([Total Revenue],SAMEPERIODLASTYEAR('Date'[Date]))

RETURN SPLY

```
### 10.   % Growth
```
% Growth = [SPLY] / [Total Revenue]

RETURN % Growth

```

### Predictive

### Forecasting
It says look at the way this thread is going if nothing chnages VanAsdrel will continue to have an Upper Band statitical of this level
in 2016 --- 4.5
  2017 --- 2.2
  All things been equally we want to see what will happen in 2011
  If nothing changes VanAsdrel will continue to be going down if not carefull. 10 years down the line VanAsdrel willbemaking --Negative.
  Noted the basic rule of machine learing statistis you need more than enought dataset to be able to accurate predition.
  



### Comparing VanArsdel Sales and Revenue with other competitors.
The insight on the sales revenue across all manufacturers dashboard for the year 2017
-	As conclusion the stack areas shows different manufactures revenues in different month and years but we only have a data for about six month 2017. Based on everything on the report in March, they generated and extra highest revenues of 4,80900, April 4.6 and the lowest month of January and it increase gradually up to March.

-	Based on the revenue VanArsdel has the highest revenue compared to the other competitors. Also the second is Natura, following by Aliqui which was around 3.06 million and Pirum.

-	Also VanArsdel have the highest amount of market share compare to the other markets in California, New York, and Texas.

-	Also, there was a great increase from February to March which we do not understand why it happened, do they spend more money on advertisement, Workshop or more marketing activities we need to have a meeting with Chief Marketing Officer (CMO) VanArsdel electronic Company just to understand why happened.

-	 Also in March VanArsdel Company accounted for 4.8 million the highest revenue for the month. The closest rival is Natura, Aliqui they have more diverse market compare to VanArsdel.

-	VanArsdel Company was dealing with Urban only. Nature and Aliqui was dealing with Rural, Youth which is mixed. They have more diverse market then VanArsdel.

-	(Recommendation)Understand why VanArsdel focus on Urban, they can actually maximise their profit by going to other market and invest on youth segment.

-	Talking of competitors looking at Natura and Aliqui on the map, they have more segment than VanArsdel. VanArsdel is more under moderation and convenience and the other one account for nothing. 

-	But Natura and Aliqui they have more pretty much diverse market but as time goes on VanArsdel has the highest market score their performance, increased from March as well as in other countries such as California, Texas and New York  nevertheless they decline as the month towards June.

### Recommendation
VanArsdel should look at the segment (Areas)
VanArsdel should look at how they can increase sale.
The areas VanArsdel are performing strongly should be investigated into to continue doing what they are doing.

## Report 
VanArsdel is manufacturing company 
The goal of this report is to compare VanArsdel manufacturing company and four other company (Natura, Aliqui, Pirum, and Currus) , also we want to know the performance for the year 2017 to be able to improve profitability and increase our revenue on daily, weekly monthly bases.

### 1. The Revenue and sum of unit by MonthName chart.
The revenue is the amount of money that we had and the number of items that is being sold during that particular period of time so the question here is that we can noticed that Jan and Feb was within the range. March their was a spike that went up above 4 millon. 
So the question is that what have we done differently that make give us the increase in other to apply it , this could be advertisement those things. So that monthly basis our revenue and unit setting will go higher. Also i April , May and June the unit and revenue went down. so, the question is what could have happened to course the reduction in revenue. What have we done wrong or what is needed to do.

### 2. Revenue by Segment chart donot chart
Moderate has the highest and select as the lowest

### 3. Sum of Revenue by Manufacturer Chart (prediction)
At this point we can see that VanAsrdel has the highest revenues 
As i said earlier it is good for us VanAsrdel to have the highest revenue having gotten 11.3 million for the year
if we want to make a prediction for the future sales, what can we do to have more higher revenue in the nearest future- 
so with this chart we can say a particular month we need to do this or if their a peak peroid or an activites is going on. 
So with the help of his data wa can make prediction for 1- 3 years may be VanAsrdel will continue be the head of the market.

### 4. Reveue by Monthname and Manufature chart
The Competitors and VanAsrdel our goal is to be known we are going well and to be able to do more.
What can we do not to go down and what to put in place.

#### 5. Under Category 
We can see the growth is the lowest.
### Recommendation
in all about the report
We need to focus on the perfomance
We are we doing to achive more revenue and What are not doing to achive lower revenue.
Also to have more revenue.

## Overview
Total sales & units for all Companies in this year comparing by last year sales calculates sales variance between this year and last year sales . total sales for every country by population over the years i want to compare between vanarsdel and another company by pressing here it will change information in all graphs.
## Process
i calculated total sales and units for all companies in this year comparing two last year sales in this section calculating the sales variance between this year and the last year's sales if positive it will be green negative it will be read in this section
calculating two teslas for every country by population over the years it will change from year to another in this section i calculating two tell sales by manufacturers
if i choose one other company it will change total sales and total units sells the market share unit market share if i wanted to compare between one other and another company i would choose a best company it will change all information in this
graph and in these boxes tutorials total units everything will change okay that's it


## Discovery

## Analysis
Findings
- What did we learn?

We discovered that 
1. NoCopyrightSOunds, Dan Rhodes and DanTDM are the channnels with the most subscribers in the UK
2. GRM Daily, Man City and Yogscast are the channels with the most videos uploaded
3. DanTDM, Dan RHodes and Mister Max are the channels with the most views
4. Entertainment channels are useful for broader reach, as the channels posting consistently on their platforms and generating the most engagement are focus on entertainment and music 




## Recommendations 

- What do you recommend based on the insights gathered? 
  
1. Dan Rhodes is the best YouTube channel to collaborate with if we want to maximize visbility because this channel has the most YouTube subscribers in the UK
2. Although GRM Daily, Man City and Yogcasts are regular publishers on YouTube, it may be worth considering whether collaborating with them with the current budget caps are worth the effort, as the potential return on investments is significantly lower compared to the other channels.
3. Mister Max is the best YouTuber to collaborate with if we're interested in maximizing reach, but collaborating with DanTDM and Dan Rhodes may be better long-term options considering the fact that they both have large subscriber bases and are averaging significantly high number of views.
4. The top 3 channels to form collaborations with are NoCopyrightSounds, DanTDM and Dan Rhodes based on this analysis, because they attract the most engagement on their channels consistently.


### Potential ROI 
- What ROI do we expect if we take this course of action?

1. Setting up a collaboration deal with Dan Rhodes would make the client a net profit of $1,065,000 per video
2. An influencer marketing contract with Mister Max can see the client generate a net profit of $1,276,000
3. If we go with a product placement campaign with DanTDM, this could  generate the client approximately $484,000 per video. If we advance with an influencer marketing campaign deal instead, this would make the client a one-off net profit of $404,000.
4. NoCopyrightSounds could profit the client $642,000 per video too (which is worth considering) 




### Action plan
- What course of action should we take and why?

Based on our analysis, we beieve the best channel to advance a long-term partnership deal with to promote the client's products is the Dan Rhodes channel. 

We'll have conversations with the marketing client to forecast what they also expect from this collaboration. Once we observe we're hitting the expected milestones, we'll advance with potential partnerships with DanTDM, Mister Max and NoCopyrightSounds channels in the future.   

- What steps do we take to implement the recommended decisions effectively?


1. Reach out to the teams behind each of these channels, starting with Dan Rhodes
2. Negotiate contracts within the budgets allocated to each marketing campaign
3. Kick off the campaigns and track each of their performances against the KPIs
4. Review how the campaigns have gone, gather insights and optimize based on feedback from converted customers and each channel's audiences



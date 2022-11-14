# Final-Project-Tableau

## Project/Goals
The goal of this project is to:
- Turn data into easily consumable visual insights using Tableau;
- Create impactful dashboards that help stakeholders make decisions, based on business questions; and
- Communicate insights with the correct visualizations.

For this project, we were given two options, I chose Option 1, which provided me with the following questions:
1. Show the trend of house prices across Canada in the last 40 years.

2. Compare the trend after 2005 with actual benchmark prices in table real_estate_prices to see if there are any differences.

3. Compare this trend with the trend of office prices. Which one is getting more expensive, faster?

4. Create a heatmap of Canada with current house prices for each available district.

5. Are the price differences between different districts increasing?

6. Compare the trend of house prices with earnings. 

7. Did people spend more of their earnings in 2014 than they did in 2001?

8. There were several economic crises in the world in the last 40 years, show the effect of these crises on: Earnings; House prices; Office prices; House constructions; and Consumer index.

9. Plot consumer_index together with housing_price_index and fit the regression line between them. Can we predict consumer_index from the housing_price_index?

10. Find an interesting pattern, trend, outlier, etc. from the data used in the above questions.

## Process
I divided my process into three steps. 

### Orientation
This step consisted mostly of reviewing the assignement and the provided business questions.

I've also downloaded the provided datasets and right away noticed that housing_price_index.csv was missing. Informed a mentor who provided me with a replacement.

### Preparation
This step consisted of cleaning the data, using Jupyter Lab.

I've detailed my cleaning steps into a notebook (provided -> dataCleaning), but the key steps are as follow:
- consumer_index: 70x null index_value (dropped)

- housing_price_index (pivot table)

- office_realestate_index: 587x duplicate values (dropped)

- real_estate_numbers : Dropped & renamed columns

- real_estates_prices: NSTR

- weekly_earnings: parsed json & dropped columns

I saved each clean datasets as a csv file and then moved to Tableau to import and join them. I initially had an issue joining the multiple datasets as they didn't have any common Id field or commonly formatted key value. So I had to do it. 

I decided to use Year, Month and province (created a Canada province for those canada-wide rows). So I went back into my dataCleaning notebook and added those value fields. 

### Visualization
This step consisted of creating a Tableau sheet for each business question. 

I also created a dashboard for each to help format for the screenshots (to be used in the presentation).

## Results
Went with Option 1.

### 1. Show the trend of house prices across Canada in the last 40 years.
I decided to go with a simple line chart with a trend line as this is what was requested. 

The key takeaway for this question is the average price of single-family properties across Canada increased by ~257% from 1981 to 2020.

### 2. Compare the trend after 2005 with benchmark prices in real_estate_prices to see if there are any differences.
I went with a dual-axis line chart to show the difference in trend between the two values. 

The key takeaway for this question is there seem to be a difference in trend and I think it's because they are using a difference reference data for their index. I unfortunately can't explain why this is the case however.

### 3. Compare this trend with the trend of office prices. Which one is getting more expensive, faster?
I went with another dual-axis line chart, but this time I used a highlight colour for the Office Price Index to help people quickly see the difference between the two trends.

Key takeaway is data is indicative that office price are getting more expensive, faster across Canada. I added a caveat however that this data ends in 2017. It is possible COVID and the increased trend of working from home had a significant impact on this conclusion.

### 4. Create a heatmap of Canada with current house prices for each available district.
A heatmap was requested for this question. I wanted to put emphasize on the larger values so I set a dark red to the higher values. 

Key takeaway is British Columbia is the province with the highest average house price (~760,000$). Other provinces are ranked as:
1. Ontario (~500,000$);
2. Alberta (~360,000$);
3. Quebec (~320,000$);
4. Manitoba & Saskatchewan (~270,000$);
5. Newfoundland & Labrador (~265,000$); and
6. New Brunswick (~200,000$).

I also added a caveat that there was no data available for the other provinces/territories.

### 5. Are the price differences between different districts increasing?
I went with a simple line chart for this one with a line for every province. I added a trend line to each to help visualize the trend of each line. This is a very busy graphic, so to help I used highlight colour for the three provinces I wanted to highlight. In a presentation I would also orient the client to the graphic and talk him thru my conclusion, saying that:
- each line represents a province and its average house price per year;
- as you can see in the background, most provinces follow a similar trend in price increase, with the exception alberta, Quebec and New Brunswick who you can see in the foreground; and
- All three provinces’ trends are lower than the other provinces, which is indicative of an increase in price difference between these three provinces and the others.

### 6. Compare the trend of house prices with earnings. 
I chose to go with another dual axis chart.

Key takeaway for this question is the average house price is increasing at a faster rate than the average weekly earnings.

### 7. Did people spend more of their earnings in 2014 than they did in 2001 2005?
I created two vertical bullet graphs for this question, which I merged into a dashboard to have the desired view in the presentation. For simplicity, I got rid of the label names and added custom reference distribution for every blocks of 20%, which I added a label for. I kept the colours very simple, using grey and blue as it matches the theme of my powerpoint presentation. 

For the data itself, I did an estimated weekly capital calculated field by taking the avg price of a home and dividing it by 25 (average mortgage length) and then 52 (to get a weekly value). The result provides me with an estimated amount of capital paid by the average canadian, in comparison to their weekly earning.

A consideration is this calculation is not taking into account the interest portion of the mortgage payments. As interest rates decreased from 2005 to 2014, it is possible Canadians did not spend more of their earnings as represented here.

### 8. There were several economic crises in the world in the last 40 years, show the effect of these crises on: earnings; house prices; office prices; house constructions; and consumer index.

Because of the different scales and the amount of values that had to be compared, I felt it was more appropriate to have a line graph with each value and that they all shared the same X axis. To highlight the economic crisis periods, I used an area notation with a light red. I also added red circle once in powerpoint to help highlight the areas to look at.

The key takeaway is we can observe a disruption in trend with all values, but particularly house construction, which of note we can also observe a slight decrease prior to a crisis, which of note is why I chose this as my question 10.

### 9. Plot consumer_index together with housing_price_index and fit the regression line between them. Can we predict consumer_index from the housing_price_index?
I kept this one at what the question was asking. I added an annotation to have the r-squared values and the p-value.

Key takeaway is consumer index can likely be predicted by housing price index.

### 10. Find an interesting pattern, trend, outlier, etc. from the data used in the above questions.

Decided to further investigate why the number of house built started to decrease a year prior (1989) an economic crisis. 

I decided to keep the same graphical format that I used for question 8, but I changed the values to:
1. The number of construction that started;
2. The number of projects that were under construction; and
3. The number of construction project that were completed.

For reference, the last one is the one I used in question 8. 

I also broke down the total number by province, so although in dark blue you have the value for Canada as a whole, you can see how each provinces are affected. You can see there's fours main provinces so I gave them highlight colours to help them pop. 

The key takeaway for this question is the number of ‘housing started’ began to decrease in 1987, particularly in the province of Ontario and Quebec for almost ten years. 

Quick open source research revealed that there was indeed a Toronto housing market crash, in 1989. But the trend reversal for 'housing started' began in 1987.

In fact, if we look before the other economic crisis, we can also observe a trend reversal of 'housing started', but we can also observe other trend reversals that were not followed by an economic crisis. I believe the takeaway is a trend reversal from positive to negative of ‘housing started’ could be used as an early indicator of economic crisis.


## Challenges 
### Parsing the json file
Made it work, but it was a messy process. See dataCleaning

### Creating relations in Tableau
Had to go back and create join fields. I should have plan better for this.

### Understanding the different type of indexes
Percent, 201610=100, 200511=100, etc.

I am not sure how or if this can affect the trend of the index value. I understand the values are different for each, but why would one increase at a higher rate than the other?

### Field names were not properly renamed during data cleaning

I sometime got lost in my field names. I should have been more agressive in the renaming of the columns I kept while data cleaning.

Probably would be disoriented if going back to this workbook in a few weeks.

Had to use a lot of aliases for dashboard views.

## Future Goals
- Get the interest rate data and attempt to fully answer question 7.

- Further investigate the end of question 10 to see if other factors could be combined to predict if there will be or not an economic crisis.


# Sales Reporting - Data Analysis and Visualization Project - How do Tableau, Python, and R measure up?

## Description
This project explores data analysis and visualization using Tableau, Python, and R. The aim is to compare the effectiveness of each platform in terms of their analytical and visualization capabilities. Currently, the Tableau portion is completed, and future work will include analysis using Python (with `sklearn` and potentially TensorFlow) and R.

## Problems to solve using each platform
1. What locations are most profitable, and what locations could have opportunities for improvement?
2. What product types are most profitable?
3. Can locations and or products be grouped into clusters according to profitability?

## Assessment criteria for platforms
1. Required background knowledge: what knowledge/skills are needed to create answers to our problems in each platform?
2. Ease of completion/ time invested: How difficult and time consuming are solutions with each platform?
3. Presentation: Are concepts and ideas communicated simply, effectively, and in an aesthetically pleasing way?

### Current Status
- **Tableau Analysis**: Completed
- **Python Analysis**: In Progress
- **R Analysis**: Planned

## Table of Contents
1. [Installation](#installation)
2. [Usage](#usage)
3. [Tableau Visualizations](#tableau-visualizations)
4. [Python Visualizations](#python-visualizations)
5. [Future Work](#future-work)
6. [Contributing](#contributing)
7. [License](#license)
8. [Contact](#contact)

## Installation
To get started, ensure you have the following installed:

- **Tableau**: Tableau Desktop or Tableau Public.
- **Python**: Python 3.x. Most required libraries have optional install cells in the notebook.
- **R**: R (and required packages) will be added later.

## Usage
### Tableau
- Open the Tableau workbook file `Market Analysis- Clustered Cities (1).twbx` in Tableau to explore the visualizations.

### Python
- Run the Python scripts located in the `Python_Analysis_ANV.ipynb` notebook for analysis.

### R
- R analysis will be included in future updates.

## Tableau Visualizations
Direct link to Tableau workbook:

(https://public.tableau.com/views/MarketAnalysis-ClusteredCities/ProfitAnalysis?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

Initially, the dataset (sourced from: https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) contains various geographical and financial data
such as sales, order quantity, discounts, city/state, product category, etc.

--

Tableau is a powerful enterprise data analysis and visualization tool, user friendly and relatively easy to learn.

Profit Ratio can quickly be added to the dataset by creating a calculated field:

Formula

sum(Profit)/sum(Sales)

Then, using this new field, we can visualize profit ratio by state to generate a map:

![Profit Ratio by State](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/Summary.png)

Where color indicates profit ratio values, with an added filter of date for further usability. Quite useful for creating a simple view of profitable states.

--

Product categories can be analyzed for profitability using chart features in Tableau. Here is a quick view to show not only profit by product category,
but to add greater context, the order volume:

![Profit Ratio by Lead Time (States)](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/catesum.jpg)

So, although tables seem to be consistently negative in terms of profit, overall volume for these items is low.

--

Shipping information is also included in the dataset, and another quick calculated field can be created:

Formula

[Ship Date] - [Order Date]

Which creates the field for "Lead Time" - the time between order date and ship date. The time it takes for an order to be fulfilled 

may have an impact on profit ratio if certain locations experience higher lead times.

![Profit Ratio by Lead Time (States)](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/LT_PR.jpg)

Each point represents a state (hover to show) and size represents sales quantity. We can conclude that average lead time does not seem
to have much impact on the profit ratio in a given state, although there are some outliers.

--

For a more detailed look at gegraphic markets, individual cities could have a higher impact on a state's overall profitability

![Profitable Cities](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/Summary(2).png)

As shown, cities like Chicago and Round Rock contribute heavily to the negative profitability of their respective states,

while sales in New York City and Los Angeles make those markets highly profitable.

--

Diving further into the city-level analysis, Tableau has clustering capability. Based on profit and sales quantity, we could group cities into categories.

![Grouped Profit (Cities)](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/CityClusters.png)

Adding marker symbols for negative and positive profit, Tableau can visually present cluster data in an easily digested format. 

--
Tableau Summary:
--

## Overall Rating:

⭐⭐⭐⭐☆

## Problems to solve
1. What locations are most profitable, and what locations could have opportunities for improvement?
   - As seen with our maps, and city clusters, New York, Seattle, and California are highly profitable markets. Illinois, Texas, and Pennsylvania are areas that could be improved.
2. What product types are most profitable?
   - Paper, Binders and Phone sales are some key profitable products.
3. Can locations and or products be grouped into clusters according to profitability?
   - Yes, we can group cities into clusters based on sales and profit data.

## Recommendations
Relatively high sales quantities in key low profit markets like Chicago, Texas in general, and some of Pennsylvania may require investigation. Lead time does not seem to be a valid KPI for Superstore-
A potential improvement could involve discounts, which Tableau can easily analyze:

![Disc and PR States](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/DISC_Tab.jpg)

--
Here it becomes apparent that the three identified problem areas do indeed seem to have the greatest discount values. A potential recommendation to improve profitability in these areas would be
keeping the discount value at 150 or lower.
--

## Assessment 
1. Required background knowledge: what knowledge/skills are needed to create answers to our problems?
   - Basic understanding of creating simple calculated fields, and slightly more advanced knowledge of clustering capabilities in Tableau.
2. Ease of completion/ time invested: How difficult and time consuming are solutions with each platform?
   - With basic knowledge of Tableau, visualizations are quickly created and modified. The recommendation visualization was created in less than 5 minutes after postulating the question.
3. Presentation: Are concepts and ideas communicated simply, effectively, and in an aesthetically pleasing way?
   - Yes, complexity is relatively low, information is easily communicated and largely interactive, with many choices for aesthetic options.

---

## Python Visualizations

Python is a versitile programming language that can be used for data analysis and visualization with standard reporting capabilities and fairly robust statistical and ML libraries. 

Python requires scripting and syntax knowledge, as well as background knowledge of libraries, parameters and logic.

Similarly to Tableau, the data is loaded using pandas to read the csv file to construct a DataFrame, and our two calculated fields can be recreated as new columns:

```python
# 'Profit' and 'Sales' columns to numeric
superstore_df['Profit'] = pd.to_numeric(superstore_df['Profit'], errors='coerce')
superstore_df['Sales'] = pd.to_numeric(superstore_df['Sales'], errors='coerce')

# Calculate the Profit Ratio:
# Divide profit by sales
superstore_df['Profit Ratio'] = superstore_df['Profit'] / superstore_df['Sales']

# Handle NaNs & nulls (division by zero errors) 
superstore_df['Profit Ratio'].replace([float('inf'), -float('inf')], pd.NA, inplace=True)

# 'Order Date' and 'Ship Date' to datetime
superstore_df['Order Date'] = pd.to_datetime(superstore_df['Order Date'], format='%m/%d/%Y')
superstore_df['Ship Date'] = pd.to_datetime(superstore_df['Ship Date'], format='%m/%d/%Y')

# Calculate Lead Time as the difference between 'Ship Date' and 'Order Date'
superstore_df['Lead Time'] = (superstore_df['Ship Date'] - superstore_df['Order Date']).dt.days
```
Using Dash, plotly and geojson (for map data) we can create our python version of an interactive profit ratio by state map

![Py Profit Ratio by State](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/py_statemap.jpg)

This comes close to the Tableau view, but reporting details are less appealing. The Dash date-range slider added along the bottom is less user friendly in comparison to Tableau,
with relatively more complexity and higher time investment to achieve a slightly less appealing result.

--

With our the two new columns, a bubble chart can be created to compare profit ratio, lead time, and order quantity.

This plotly visualization is on par with Tableau for reporting, however requires some data aggregation to achieve the desired result:

```python
# Aggregate data by state for plotting
state_agg = superstore_df.groupby('State').agg({
    'Lead Time': 'mean',
    'Profit Ratio': 'mean',
    'Quantity': 'sum'  
}).reset_index()

# Rename 'Quantity' column to 'Total Quantity'
state_agg.rename(columns={'Quantity': 'Total Quantity'}, inplace=True)


# Create scatter/bubble plot with hover info
fig = px.scatter(
    state_agg,
    x='Lead Time',
    y='Profit Ratio',
    size='Total Quantity',  
    color='State',          
    hover_name='State',     
    hover_data={
        'Lead Time': True,
        'Profit Ratio': True,
        'Total Quantity': True  
    },
    title='Profit Ratio vs. Lead Time by State'
)

# Update layout for better appearance
fig.update_layout(
    xaxis_title='Lead Time (days)',
    yaxis_title='Profit Ratio',
    showlegend=True
)

```
Where as Tableau has a more user friendly built-in aggregation tool when selecting fields to generate SUM or AVG.

The python generated bubble chart is effective and appealing.

![Py Profit Ratio by State](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/py_LTPR_state.jpg)


## Future Work
- **Python Analysis**: Implement and test data analysis and machine learning models using `sklearn` and potentially TensorFlow.
- **R Analysis**: Conduct analysis and visualizations using R to complete the comparative study.

## Contact
- **Your Name** - [tristanperry17@gmail.com](mailto:tristanperry17@gmail.com)
- **Project Link**: [https://github.com/tristanperry17/Sales_Reporting](https://github.com/tristanperry17/Sales_Reporting)





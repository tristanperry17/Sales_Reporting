
# Sales Reporting - Data Analysis and Visualization Project - How do Tableau, Python, and R measure up?

## Description
This project explores data analysis and visualization using Tableau, Python, and R. The aim is to compare the effectiveness of each platform in terms of their analytical and visualization capabilities. Currently, the Tableau portion is completed, and future work will include analysis using Python (with `sklearn` and potentially TensorFlow) and R.

## Problems to solve using each platform
1. What locations are most profitable, and what locations could have opportunities for improvement?
2. What product types are most profitable?
3. Can locations and or products be grouped into clusters according to profitability?

### Current Status
- **Tableau Analysis**: Completed
- **Python Analysis**: In Progress
- **R Analysis**: Planned

## Table of Contents
1. [Installation](#installation)
2. [Usage](#usage)
3. [Tableau Visualizations](#tableau-visualizations)
4. [Future Work](#future-work)
5. [Contributing](#contributing)
6. [License](#license)
7. [Contact](#contact)

## Installation
To get started, ensure you have the following installed:

- **Tableau**: Tableau Desktop or Tableau Public.
- **Python**: Python 3.x. Install required libraries using:

    ```bash
    pip install -r requirements.txt
    ```

  The `requirements.txt` file includes dependencies like `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, and potentially `tensorflow`.

- **R**: R (and required packages) will be added later.

## Usage
### Tableau
- Open the Tableau workbook file `Market Analysis- Clustered Cities (1).twbx` in Tableau to explore the visualizations.

### Python
- Run the Python scripts located in the `python` directory for analysis.
- Example command:

    ```bash
    python analysis_script.py
    ```

### R
- R analysis will be included in future updates.

## Tableau Visualizations
Here are some screenshots of the Tableau visualizations created so far:

(https://public.tableau.com/views/MarketAnalysis-ClusteredCities/ProfitAnalysis?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

Initially, the dataset (sourced from: https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) contains various geographical and financial date

such as sales, order quantity, discounts, city/state, product category, etc.

--

Tableau is a powerful enterprise data analysis and visualization tool, user friendly and relatively easy to learn.

--

Profit Ratio can quickly be added to the dataset by creating a calculated field:

Formula

sum(Profit)/sum(Sales)

Then, using this new field, we can visualize profit ratio by state to generate a map:

![Profit Ratio by State](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/Summary.png)

Where color indicates profit ratio values, with an added filter of date for further usability. Quite useful for creating a simple view of profitable states.

--

Shipping information is also included in the dataset, and another quick calculated field can be created:

Formula

[Ship Date] - [Order Date]

Which creates the field for "Lead Time" - the time between order date and ship date. The time it takes for an order to be fulfilled 

may have an impact on profit ratio if certain locations experience higher lead times.

![Profit Ratio by Lead Time (States)](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/Summary(4).png)

--

For a more detailed look at gegraphic markets, individual cities could have a higher impact on a state's overall profitability

![Profitable Cities](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/Summary(2).png)

As shown, cities like Chicago and Round Rock contribute heavily to the negative profitability of their respective states,

while sales in New York City and Los Angeles make those markets highly profitable.

--

Diving further into the city-level analysis, Tableau has clustering capability. Based on profit and sales quantity, we could group cities into categories.

![Grouped Profit (Cities)](https://raw.githubusercontent.com/tristanperry17/Sales_Reporting/main/Images/CityClusters.png))

Adding marker symbols for negative and positive profit, Tableau can visually present cluster data in an easily digested format. 

--


--
## Future Work
- **Python Analysis**: Implement and test data analysis and machine learning models using `sklearn` and potentially TensorFlow.
- **R Analysis**: Conduct analysis and visualizations using R to complete the comparative study.

## Contact
- **Your Name** - [tristanperry17@gmail.com](mailto:tristanperry17@gmail.com)
- **Project Link**: [https://github.com/tristanperry17/Sales_Reporting](https://github.com/tristanperry17/Sales_Reporting)





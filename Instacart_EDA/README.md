
# Instacart Exploratory Data Analysis

## Description
This project aims to explore and analyze an Instacart public dataset, focusing on uncovering insights into customer behavior, product preferences, and order patterns. The notebook titled `Instacart_EDA.ipynb` contains a thorough exploratory data analysis (EDA) that delves into various aspects of the Instacart dataset, including orders, products, aisles, and departments. By examining trends and patterns in this dataset, we address questions related to shopping habits, frequency of purchases, and preferences across different segments of Instacart's product range.

### Features and Functionality
- **Data Loading and Cleaning**: Custom functions to load various CSV files, handling missing values and duplicates.
- **Exploratory Data Analysis**: Visualization of purchase patterns, product categories, and order frequencies.
- **Insightful Findings**: Summarization of key insights regarding customer behavior and product trends.

### Client Questions

#### A 
1. Verify that values in the 'order_hour_of_day' and 'order_dow' columns in the orders table are sensible (i.e. 'order_hour_of_day' ranges from 0 to 23 and 'order_dow' ranges from 0 to 6).
2. Create a plot that shows how many people place orders for each hour of the day.
3. Create a plot that shows what day of the week people shop for groceries.
4. Create a plot that shows how long people wait until placing their next order, and comment on the minimum and maximum values.

#### B

1. Is there a difference in 'order_hour_of_day' distributions on Wednesdays and Saturdays? 
2. Plot the distribution for the number of orders that customers place (e.g. how many customers placed only 1 order, how many placed only 2, how many only 3, and so on…)
3. What are the top 20 products that are ordered most frequently (display their id and name)?

#### C

1. How many items do people typically buy in one order? What does the distribution look like?
2. What are the top 20 items that are reordered most frequently (display their names and product IDs)?
3. For each product, what proportion of its orders are reorders (create a table with columns for the product ID, product name, and reorder proportion)?
4. For each customer, what proportion of their products ordered are reorders?
5. What are the top 20 items that people put in their carts first (display the product IDs, product names, and number of times they were the first item added to the cart)?

### Insights
#### Data Issues
1. 15 duplicate rows in `instacart_orders.csv`. Database Managers may want to investigate.
2. 104 duplicate product names in  `products.csv` with different product IDs. I suspect this is due to the same product being sold in different quantities, but its worth being aware of / looking in to.
3. There are 1,258 missing product names from  `products.csv`. In all cases the associated department ID was 21 (department name recorded as "missing" in `aisles.csv`) and the aisle ID was 100 (also recorded as "missing" in `departments.csv`). I highly recommend the Database Manager look into this.
4. It looks like the 'add to cart order' is correctly collected up to the 64th product added to each order in `order_products.csv`. Any subsequent order is given the NaN value. Developers may want to look into patching this bug.
5. Similarly, 'Days since prior order' in `orders.csv` looks to max out at the 30 day mark (values above 30 are recorded as 30).

#### Key Analysis Highlights
1. Volume by hour:
![Orders Per Hour](/images/orders_per_hour.png "Orders Per Hour")
The busiest hour of the day is 10 AM.<br>
The top five busiest hours of the day are 10 AM, 11 AM, 3 PM, 4 PM, and 1 PM (respectively).
82.17% of all orders are placed between 8AM and 6PM.

2. Volume by day of week:<br>
![Orders Per Day of Week](/images/orders_per_dow.png "Orders Per Day of Week")<br>
The volume is highest on Sundays and Mondays, with a relative dip for the rest of the week and a slight uptick on Fridays and Saturdays. I.E. Most volume is done in and around the weekend (Friday - Monday).

3. How long people wait before placing their next order:
![Distribution of Days Since Prior Order](/images/distri_days_since_prior_order.png "Distribution of Days Since Prior Order")
Considering point 5 from `Data Issues`, the next most occurring number of days since prior order is 7. Additionally 7 days is the median value for the dataset.<br>
Generally speaking, customers order about once every 7 days.

4. Item popularity:<br>
The most ordered products and most reordered products overlap by 95%, with only Organic Grape Tomatoes from the most ordered list being swapped with Organic Grape Tomatoes in the most reordered list. For both most ordered and most reordered, 75% were organic produce.

5. Typical order size:<br>
![Distribution of Products Per Order](/images/distri_prod_per_order.png "Distribution of Products Per Order")
Typically, people buy 5 items in a single order, as that's the most common order size (mode). The distribution of products per order is right-skewed, with the median at 8 items, slightly higher than the mode. The average (mean) number of items is about 10.

### Tools Used
- **Python** for data manipulation and analysis.
- **Pandas** and **NumPy** for data processing.
- **Matplotlib** for data visualization.

### Deployment and System Requirements
- **Python 3.8+** is required to ensure compatibility with the libraries used.
- **Pandas**, **NumPy**, and **Matplotlib** must be installed.

### Roadmap for Future Improvements
- **Enhance Visualizations**: Improve the current visualization by integrating interactive elements using Plotly to achieve a more engaging user experience.
- **Optimize Data Loading**: Streamline the data loading process using a more efficient data management system to handle larger datasets seamlessly.
- **Expand Analysis**: Incorporate machine learning models to predict customer purchasing behavior and product recommendations.

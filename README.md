## DATA ANALYSIS FOR COMPANY XYZ
* Company XYZ owns a supermarket in 3 cities across the Country - Lagos, Abuja and Portharcourt. This data analysis is conducted to determine sales trend and Company growth, as there has been an increase in Supermarket competition.

### Loading Datasets
* The process begins with importing the different Libraries.
* The data collected from the 3 different branches are combined using the concatenation method and it's exported to a CSV for easy Data analysis.
  *combined_csv = pd.concat([pd.read_csv(f) for f in all_filenames])
  *combined_csv.to_csv("combined_csv.csv", index = False, encoding = 'utf-8-sig')
* The pd_read.csv() and head() methods are used to to read and return the first few rows of the combined csv respectively.

### Data Exploration
* The shape attribute determines the number of rows and columns, while the column attributes generates the names of columns.
  *df.shape, df.columns
* The describe function generates the statistical summary of the dataframe which includes the count, mean, standard deviation, Minimum, Maximum, 25th, 50th and 75th percetile. From this result, different comparison and deductions could be made.
  *df.describe()

* Using df.isnull() and df.notna() method, we can determine wether there are missing values or not. The sum method can be added to get a summary and not a boolean (True/False).
  *df.isnull().sum()
  *df.notna().sum()
* The info() method is then used to check the information of the DataFrame. This includes the Columns, number of rows and columns, presence of missing values and the Data types of each column.
  *df.info()

### Dealing with DateTime Features
* The to_datetime method is used to convert the Date and Time to DateTime data type.
  **Date = df['Date'] = pd.to_datetime(df['Date'])
  **df['Time'] = pd.to_datetime(df['Time'])
* The dtype method is used to check if the datatype is in DateTime.
  **df['Date'].dtype
  **df['Time'].dtype
* Extraction of Day, Month, Year and Hour using .dt.day, .dt.mont, .dt.year and .dt.hour.
* The number of unique hours was determined using the nunique method and unique() method to show the unique sales hour.
  **df_hour.nunique(dropna = True)
  **ser.unique()

### Unique Values in column
* By iterating through the categorical columns, the unique values in the categorical column are determined. The value_counts() method  is used to generate the count figure of the categorical column.
  **for i in categorical_columns:
    if i != 'Invoice ID':
        print ("This is for {} columns".format(i))
        print (df[i].unique().tolist())
        print("Total Number of unique value: {}".format(len(df[i].unique().tolist())))
        **df['Gender'].value_counts()
### Aggregation with GroupBy
* The sum and mean of teh City column is determined using the aggregation function.
  **gross_income = City['gross income'].sum().reset_index()
* A groupby method also shows the gross income of each city and the city with the highest total gross income is determined using the .max() method.
  **gross_income.max().reset_index()
* A table showing the Unit Price, Quantity and gross margin percentage was generated using the GroupBy method.
* Also the product line and gross income are generated with the groupby function.
  **other_columns = City['Unit price', 'Quantity', 'gross margin percentage'].sum()
From this, City with the highest Unit price, highest quantity, gross margin percentage was determined, as well as Product line against Gross income to determine the product line with the highest gross income.

### Data Visualization
* The use of countplot to determine the branch with the highest sales record.
* Also, using countplot to determine the highest payment method used.
* The city with the highest sales was also determined using the count plot.
* The sales in different product line was determined using countplot()
* The payment method versus product line was explored to determine the payment method mostly used for each product line.
* The payment method mostly used in each branch was determined using the countplot() method.
* The customer's level of satisfaction in each branch was determined using the boxplot() by plotting the 'Rating column' against 'Branch'.

* It is believed that gender type affects the type of product being purchased at the supermarket. Hence, a catplot of the  'boxen' kind was used to determine what each gender buy most.

* A catplot() method of kind 'point' was used to compare Product line, Unit price and Quantity.

* In further Data analysis, countplot() was used to determine the payment method preferred by each gender.

  *sns.countplot(x = 'Payment', data = df, hue = 'Gender').set_title('Gender vs Payment method');
* The plotting of Gender against City also determines the number of each gender that makes more purchase.
  *sns.countplot(x = 'City', data = df, hue = 'Gender').set_title('Gender vs City');
* The last part showed a catplot() of the kind 'violiin' that shows the City that pays the highest tax.
  *sns.catplot(x = 'City', y = 'Tax 5%', kind = 'violin', data = df, aspect = 4);

### Insight
The standard deviation of the columns are not too low, and hence the values of the datasets does not deviate too much from the mean.
25% of customers made a Total purchase of N44792 and below, while the gross income made from 25% of customers was N2153 and below
Also, 75% of customers made a Total purchase of N169686 and below, while the gross income made from 75% of customers was N8080 and below.
From the Minimum and Maximum, we can say that the total purchase ranges from N3844 - N375354, while the gross income ranges from N183 - N17874.
The minimum and the maximum ratings also ranges from 4 - 10, which denote that the minimum level of satisfaction experienced by customers is 4/10, while the maximum is 10 and the average quantity purchased is 5.5.
Using the isnull() and notna() method, we realized that there were no missing data in the data sets.

With the GroupBy aggregate method, the gross income of Lagos, Abuja and Portharcourt were gotten, and the max() method shows Portharcourt to return the highest gross income of N3,790,927.08
Checking the gross income of the product lines, Food and beverages has the highest gross income, while Health and Beauty experienced the lowest. This may be due to Food being one of the primary human needs of people.
By comparing the different branches A, B, C and quantity, it was realized that Branch A has the highest Quantity purchased while Branch B has the least.Using the countplot() method, Branch A records the highest sales. The countplot() method also shows that the Epay payment is the most used method of Payment across the Branches.
Using the countplot method to check Sales across Lagos, Abuja and Portharcourt, Lagos City rrecorded the highest Sales trend, while Abuja recorded the least.~

### Future Work
Those factors that makes Lagos City to emerge as the City witht hte highest sales, can be explored, and the outcome can be used to drive sales in other Cities.

### Standout section
he groupby method was further used to explore gross income for te different product lines. From the result, Food and beverages has the highest gross income, while Health and Beauty experienced the lowest.

Also, the countplot() method returns Portharcourt to pay the highest Tax whenCity was plotted against Tax at 5%. From previous analysis, we also know that Portharcourt ha sthe highest gross income. There is a relationship between Gross income and Tax.
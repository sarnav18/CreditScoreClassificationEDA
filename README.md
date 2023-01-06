# Background
We are given with the credit score and their characteristics for 12.5k customers over 8 months, giving around 100k rows.Our dataset has many null values and outliers, and we must reformat certain categorical attributes for analysis. How can one maintain a good credit score, and what mistakes impact a credit score?
![image](https://user-images.githubusercontent.com/121786778/210924530-84ad17ae-3614-4d89-8d84-2465d9c4bdbe.png)

# Data Cleaning:


![image](https://user-images.githubusercontent.com/121786778/210924768-17e5577b-253e-4fea-b98b-0e966d268653.png)


We deep dive into each feature in the dataset to check for unexpected values in the column. Some unexpected values, example, Age being mentioned as -500, etc. needs sanitization. 
Whereas other columns such as credit history age which have time-periods mentioned as ‘5 year and 6 months’ needs to be changed to numeric columns as 5.5.

# Handling Null Values

## Fill zero
Delayed Payments, changed credit limit, Credit Inquiries, Amount Invested monthly are filled with 0 assuming they are null in that month

## Fill mean
Salary, Balances within same customer are filled with mean

## Fill zero
Categorical columns with null values are filled with mode within the same customer

# Removed Outliers

The dataset was heavily right-skewed
Age and Num_of_Loan had values outside of the lower bound for outliers
All attributes had outliers outside of the upper bound for outliers
![image](https://user-images.githubusercontent.com/121786778/210927101-ab4b9c15-8a09-4fcf-b107-cead16232a47.png)

Created a function to calculate the lower and upper bounds using a dataframe and column as input variables.The output was a dictionary with lower and upper bounds to filter outliers with.Using pandas.dataframe.describe() was only gave us minimum, maximum, and quartiles – not outlier bounds

Using values from the upper and lower bound dictionary and list of columns we identified with outliers.All highlighted lower bounds were modified because negative values did not make sense.A negative Delay_from_due_date represents paying ahead of time

# Trends in Data
## Occupation
![image](https://user-images.githubusercontent.com/121786778/210930203-62779e77-aaf6-4dce-9999-f1a3394db675.png)

## Distribution of credit score - month over month 
![image](https://user-images.githubusercontent.com/121786778/210930144-cc315348-eb41-4cf3-a5ab-902b598e3e5f.png)

## Increasing or decreasing your credit limit affects the credit utilization ratio thereby affecting the credit score
![image](https://user-images.githubusercontent.com/121786778/210930377-f20d5b1e-51fe-4d27-9a43-ea0636a6b54d.png)

## Factors affecting credit score
![image](https://user-images.githubusercontent.com/121786778/210930479-68c97eb9-760c-4809-a66d-2fb1395948ab.png)

![image](https://user-images.githubusercontent.com/121786778/210930592-e45cda8b-e286-43f7-9896-97870aa6a5ba.png)

## As the payment is delayed from the due date, outstanding debt increases.People with good credit score and high outstanding debt clear the dues early.
![image](https://user-images.githubusercontent.com/121786778/210930706-44a4b737-5d86-4ebb-8a90-a50c7ea819e4.png)

## Credit History Age decreases with increase in payment delay
![image](https://user-images.githubusercontent.com/121786778/210930735-f014550a-27df-479c-a789-5812f93139c2.png)

## Trends for outstanding Debt
![image](https://user-images.githubusercontent.com/121786778/210930888-dc08a225-2492-49e9-a89a-fc6fb4cebd1a.png)
![image](https://user-images.githubusercontent.com/121786778/210930922-3aff50ba-2847-48a2-8913-f3e5603b434f.png)

# Recommendations

## Maintain a high account balance and avoid delayed payments
![image](https://user-images.githubusercontent.com/121786778/210930996-9d844e5d-102d-4ecf-bb39-3f5aeb178bdb.png)

## Avoid more than 8 delayed payments per month
![image](https://user-images.githubusercontent.com/121786778/210931043-4e780348-032d-4701-9ed6-3218f9aad903.png)

## Avoid having multiple bank accounts. 
Having multiple bank accounts is not a negative characteristic, however, one must ensure not to have more than 5 accounts.Most of the customers with good credit score have less than 5 bank accounts

![image](https://user-images.githubusercontent.com/121786778/210931117-d6320d10-e3e2-45b9-8e1f-252413229074.png)

## Prioritize increasing the number of spends with large or medium dollar values and avoid payments with low small dollar values
High-spent-large-value and High-spent-medium-value customers usually tend to have a good credit score. Whereas customers that make Low-spent-medium-value and Low-spent-small-value payments tend to have poorer credit scores
![image](https://user-images.githubusercontent.com/121786778/210931179-aeabdeb9-6f7d-48c7-ae4a-b166e42572ae.png)

![image](https://user-images.githubusercontent.com/121786778/210931168-afa8a5ba-69e8-46e8-9684-424e9357d243.png)

## Maintain less than $ 1,500 outstanding debts to secure a good spot in good and standard credit score bucket
From the graph we can infer – After an outstanding debt of $1500 there is a sharp decline in  good and standard credit scores. 
![image](https://user-images.githubusercontent.com/121786778/210931353-a46acb99-b044-497e-b5c7-c90774b0cfb3.png)



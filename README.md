# Analyzing Customer Data with Pandas

## 📊 Introduction

This project demonstrates how to analyze customer data using the pandas library in Python. We will explore the dataset to answer key business questions, providing insights into customer demographics, spending patterns, and more.

## 📁 Prerequisites

Ensure you have the following packages installed:

```pip install pandas```

## 📂 Dataset

The dataset should contain information about customers, including their names, age, gender, profession, contact details, spending, and credit card information.

## 🔎 Questions and Solutions

### 1. How many entries and columns are in the dataset?
```
import pandas as pd

df = pd.read_csv('customer_data.csv')

print(f"Entries: {df.shape[0]}, Columns: {df.shape[1]}")
```
### 2. What are the maximum, minimum, and mean ages of customers?
```
print(f"Max Age: {df['Age'].max()}")

print(f"Min Age: {df['Age'].min()}")

print(f"Mean Age: {df['Age'].mean()}")
```
### 3. What are the three most common customer names?
```
print(df['Name'].value_counts().head(3))
```
### 4. Which customers have the same phone number?
```
duplicate_phones = df[df.duplicated('Phone', keep=False)]

print(duplicate_phones[['Name', 'Phone']])
```
### 5. How many customers are "Structural Engineer"?
```
print(df[df['Profession'] == 'Structural Engineer'].shape[0])
```
### 6. How many male customers are "Structural Engineers"?
```
male_structural_engineers = df[(df['Profession'] == 'Structural Engineer') & (df['Gender'] == 'Male')]

print(male_structural_engineers.shape[0])
```
### 7. How many female Structural Engineers are from Alberta (AB)?
```
female_ab_engineers = df[(df['Profession'] == 'Structural Engineer') & (df['Gender'] == 'Female') & (df['Province'] == 'AB')]

print(female_ab_engineers)
```
### 8. What is the maximum, minimum, and average spending?

print(df['Spending'].max(), df['Spending'].min(), df['Spending'].mean())

### 9. Who did not spend anything?
```
no_spending_customers = df[df['Spending'] == 0]

print(no_spending_customers)
```
### 10. Who spent 100 CAD or more (for a loyalty coupon)?\
```
loyal_customers = df[df['Spending'] >= 100]

print(loyal_customers)
```
### 11. How many emails are associated with credit card number '5020000000000230'?
```
print(df[df['Credit_Card'] == '5020000000000230']['Email'].nunique())
```
### 12. How many credit cards are expiring in 2019?
```
expiring_2019 = df[df['Card_Expiry'].str.endswith('19')]
print(expiring_2019.shape[0])
```
### 13. How many people use Visa as their credit card provider?
```
visa_users = df[df['Credit_Card_Provider'] == 'Visa']

print(visa_users.shape[0])
```
### 14. Who spent 100 CAD using Visa?
```
visa_high_spenders = df[(df['Credit_Card_Provider'] == 'Visa') & (df['Spending'] == 100)]

print(visa_high_spenders)
```
### 15. What are the two most common professions?

print(df['Profession'].value_counts().head(2))

### 16. What are the top 5 most popular email providers?
```
email_domains = df['Email'].str.split('@').str[1]

print(email_domains.value_counts().head(5))
```
### 17. Is there any customer using an email with "am.edu"?

print(df[df['Email'].str.contains('am.edu')])

### 18. Which day of the week does the store get the most customers?
```
df['Purchase_Date'] = pd.to_datetime(df['Purchase_Date'])

print(df['Purchase_Date'].dt.day_name().value_counts().head(1))
```
## 📊 Conclusion

Using pandas, you can efficiently explore and analyze customer data to answer business-related questions. Modify these scripts based on your specific dataset and business needs.

## 📌 Further Improvements
•	Automate analysis with custom reports.

•	Visualize trends with Matplotlib or Seaborn.

•	Implement data validation and cleansing procedures.



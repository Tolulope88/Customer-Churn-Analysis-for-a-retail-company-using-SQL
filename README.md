# Customer-Churn-Analysis-for-a-retail-company-using-SQL

**Project Overview**
This project aims to analyze customer behavior on Adventure work shopping platform to identify key drivers of churn and develop actionable insights that help the business reduce customer attrition, retain valuable customers, and increase long-term revenue.


**Data Set**


Source: Adventure Works



**Business Goal**
Adventure work has been experiencing high customer churn which refers to the loss of clients or customers. High churn rates can significantly affect a company’s revenue and growth. This analysis is aimed at helping the marketing and customer success teams:
1. Detect at-risk customers early.
2. Optimize retention strategies.
3. Improve overall customer lifetime value.
4. Reduce customer churn rate by providing actionable insights to the marketing and customer success teams.

**Methodology**
The ETL (Extract, Transform, Load) process was utilized as the methodology of choice to extrapolate pertinent information for this analysis. Azure Data Studio database was used to write queries to extract the required data and the results retrieved was saved in Excel to be transformed in Power BI. Data Tranformation in Power BI was used for
cleaning, filtering, aggregating and manipulating the data.

**SQL Query**

SELECT 
    c.CustomerID,
    p.FirstName + ' ' + p.LastName AS FullName,
    MAX(soh.OrderDate) AS LastOrderDate,
    DATEDIFF(DAY, MAX(soh.OrderDate), GETDATE()) AS DaysSinceLastPurchase
FROM Sales.SalesOrderHeader soh
JOIN Sales.Customer c ON soh.CustomerID = c.CustomerID
JOIN Person.Person p ON c.PersonID = p.BusinessEntityID
GROUP BY c.CustomerID, p.FirstName, p.LastName
HAVING DATEDIFF(DAY, MAX(soh.OrderDate), GETDATE()) > 180 -- customers inactive for over 6 months
ORDER BY DaysSinceLastPurchase DESC;

**Customer Segementation**
First the customers were categorized into different segments based on the last time they made a purchase at Adventure works

 ![Screenshot (378)](https://github.com/Tolulope88/Customer-Churn-Analysis-for-a-retail-company-using-SQL/blob/main/Screenshot%20(378).png)


**KEY FINDINGS**

1. 68.09% of the customers have not shopped in the last two months
2. North America has the highest number of shoppers
3. The most bought item on the website is Water bottle with a total of 4,700 units sold
4. The total number of customers are 19,120 however only 40% of them are active shoppers





  ![Screenshot (381)](https://github.com/Tolulope88/Customer-Churn-Analysis-for-a-retail-company-using-SQL/blob/main/Screenshot%20(381).png)





**CUSTOMER RETENTION STRATEGY**

**Email Marketing:**  Reach out to customers via email provided to get feedback on products and services, suggestions for improvement and
how to serve them better. Targeted emails with personalized offers can be sent.


**Market Survey:** Adventure work  can conduct survey to glean customer concerns regarding infrequency of purchase. Offer those that have not shopped in the last 12 months a
discount on their next order.

**Provide limited time offers:** To encourage dormant customers to take action, I recommend limited time offers to elicit a sense of urgency in the minds of customers.

**Referral Programs:** Encourage existing customers to refer dormant and prospective customers to your business by offering incentives such as discounts or freebies.

**Social Media Campaign:** A multi -pronged approach that targets the most popular social media platforms can be deployed to maximize potential reach. Facebook Ads, Intagram Ads, Tik Tok ads can make an impact on the brands visibility and encourage top of mind recall.






 ![Screenshot (384)](https://github.com/Tolulope88/Customer-Churn-Analysis-for-a-retail-company-using-SQL/blob/main/Screenshot%20(384).png)








 
 
 
 
 
 
 
 
 
 
 
 
 
 ![Screenshot (376)](https://github.com/Tolulope88/Customer-Churn-Analysis-for-a-retail-company-using-SQL/blob/main/Screenshot%20(376).png)

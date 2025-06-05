# Customer-Churn-Analysis-for-a-retail-company-using-SQL

**Project Overview**
Objective: Analyze customer behavior to identify factors contributing to customer churn and build a predictive model to flag at-risk customers.

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

**KEY FINDINGS**

First the customers were categorized into different segments based on the last time they made a purchase at Adventure works

 ![Screenshot (378)](https://github.com/Tolulope88/Customer-Churn-Analysis-for-a-retail-company-using-SQL/blob/main/Screenshot%20(378).png)




  ![Screenshot (381)](https://github.com/Tolulope88/Customer-Churn-Analysis-for-a-retail-company-using-SQL/blob/main/Screenshot%20(381).png)





**CUSTOMER RETENTION STRATEGY**

**Email Marketing:**  Reach out to customers via email provided to get feedback on products and services, suggestions for improvement and
how to serve them better. Targeted emails with personalized offers can be sent.






 
 
 
 
 
 
 
 
 
 
 
 
 
 ![Screenshot (376)](https://github.com/Tolulope88/Customer-Churn-Analysis-for-a-retail-company-using-SQL/blob/main/Screenshot%20(376).png)

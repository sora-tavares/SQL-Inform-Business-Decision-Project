
![SQL](https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)

# 🧠 Data Analysis with SQL: Inform a Business Decision (Guided Project)

This repository contains my solution and key takeaways from the Coursera Guided Project:  
**[Data Analysis with SQL: Inform a Business Decision](https://www.coursera.org/learn/award-sales-incentive-bonuses-using-w3schools-sql-tool)**  
Instructor: Judy Richardson | Platform: Coursera | Tool: W3Schools SQL Tryit Editor

> 🎯 **Goal:** Use SQL to help a fictional company identify employees eligible for sales bonuses by analyzing order data from the Northwind database.

---

## 📋 Project Summary
As a Data Analyst, I explored and queried relational data using SQL to answer the business question:
> _“How can we identify the employees who have earned bonuses?”_

Two specific deliverables were required:
1. A list of **orders with the five highest sales amounts** and the employees responsible.  
2. A list of the **five employees with the highest cumulative sales**.

Additionally, the final **cumulative challenge** involved determining how many orders were placed by each customer.

---

## 🧪 SQL Code Samples (from project work)

### ✅ Solution 1: Orders with the Five Highest Sales Amounts (Employee Details)
```sql
SELECT LastName, FirstName, Orders.OrderID, Products.ProductID,
       Quantity, Price, SUM(Quantity * Price) AS SalesAmt
FROM Employees
INNER JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID
INNER JOIN OrderDetails ON Orders.OrderID = OrderDetails.OrderID
INNER JOIN Products ON OrderDetails.ProductID = Products.ProductID
GROUP BY LastName, FirstName, Orders.OrderID, Products.ProductID, Quantity, Price
ORDER BY SUM(Quantity * Price) DESC;
```

### ✅ Solution 2: Five Employees with the Highest Sales Amounts
```sql
SELECT LastName, FirstName, SUM(Quantity * Price) AS SalesAmt
FROM Employees
INNER JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID
INNER JOIN OrderDetails ON Orders.OrderID = OrderDetails.OrderID
INNER JOIN Products ON OrderDetails.ProductID = Products.ProductID
GROUP BY LastName, FirstName
ORDER BY SUM(Quantity * Price) DESC;
```

### ✅ Cumulative Challenge: Count of Orders Per Customer
```sql
SELECT CustomerName, Customers.CustomerID, COUNT(Orders.OrderID) AS OrderCount
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID
GROUP BY CustomerName, Customers.CustomerID
ORDER BY COUNT(Orders.OrderID) DESC;
```

---

## 🧠 Key Takeaways

- A database is a collection of related tables organized in rows and columns.
- SQL allows analysts to extract and combine data using `INNER JOIN`.
- `GROUP BY` and `SUM()` are essential tools for summarising business data.
- `ORDER BY` helps rank values such as sales amount.
- Using online tools like W3Schools' SQL Tryit Editor makes practicing SQL accessible.

---

## 📜 Certification

🔗 [View Certificate](Resources/Data Analysis With SQL Certificate.pdf)

---

## 📎 About the Guided Project

- **Platform:** Coursera  
- **Project:** [Data Analysis with SQL: Inform a Business Decision](https://www.coursera.org/learn/award-sales-incentive-bonuses-using-w3schools-sql-tool)  
- **Tool used:** W3Schools SQL Tryit Editor  
- **Duration:** ~35 minutes  
- **Instructor:** Judy Richardson

---

*Thanks for visiting! Feel free to fork this repo if you're exploring SQL for data analysis.*

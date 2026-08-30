# Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

**Vulnerability:**

SQL Injection (SQLi)

**Overview:**

The application's product category filter directly incorporates user-controlled input into a SQL query without properly sanitizing or parameterizing it.

By injecting a SQL condition that always evaluates to true, it is possible to modify the application's WHERE clause and retrieve products that would normally be hidden.

The application carries out a SQL query like the following:

**SELECT * FROM products WHERE category = 'Gifts' AND released = 1**

**Attack Steps:**

1. Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Modify the category parameter, giving it the value '+OR+1=1--
3. Submit the request, and verify that the response now contains one or more unreleased products. 

**Impact:**

An SQL injection vulnerability can allow an attacker to manipulate database queries and potentially:
- Bypass application logic
- Retrieve unauthorized data
- Access sensitive database information
- Modify or delete database records
- Potentially compromise the underlying database, depending on the database configuration and application privileges
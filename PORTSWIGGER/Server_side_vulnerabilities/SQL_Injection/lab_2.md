# Lab: SQL injection vulnerability allowing login bypass

**Overview:**

The application's login functionality is vulnerable to SQL injection because user-supplied input is incorporated directly into the SQL query without proper sanitization or parameterization.

By injecting SQL syntax into the username parameter, it is possible to modify the authentication query and bypass the password check.

**Attack Steps:**

1. Use Burp Suite to intercept and modify the login request.
2. Modify the username parameter, giving it the value: administrator'-- 
After injecting the payload, the query effectively becomes:

SELECT * FROM users
WHERE username = 'administrator'--'
AND password = 'password';
The -- sequence comments out the remainder of the query, including the password check.

**Impact:**

An SQL injection vulnerability in an authentication mechanism can allow an attacker to bypass login controls and access another user's account.

Depending on the application's privileges, this could result in:

    Unauthorized account access

    Administrator account takeover

    Access to sensitive information

    Modification of application data

    Further compromise of the application
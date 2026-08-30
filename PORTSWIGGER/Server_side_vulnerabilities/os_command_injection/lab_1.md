# Lab: OS command injection, simple case

**Vulnerability:**

OS Command Injection

**Overview:**

The application uses the user-controlled storeID parameter when constructing an operating system command to check the stock level.

Because the parameter is not properly sanitized, it is possible to inject an additional operating system command and execute it on the server.

**Attack Steps:**

1. Use Burp Suite to intercept and modify a request that checks the stock level.
2. Modify the storeID parameter, giving it the value 1|whoami.
3. Observe that the response contains the name of the current user.

**Impact:**

Successful OS command injection can allow an attacker to execute arbitrary commands on the underlying server with the privileges of the application process.

Depending on those privileges, this could lead to:

- Sensitive information disclosure
- Unauthorized modification of files
- Access to application secrets and credentials
- Further compromise of the underlying server
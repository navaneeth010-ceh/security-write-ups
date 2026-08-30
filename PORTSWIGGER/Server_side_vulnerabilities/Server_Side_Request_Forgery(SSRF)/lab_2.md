# Lab: Basic SSRF against another back-end system

**Vulnerability:** SSRF

**Impact:** back-end misconfiguration leads to information disclosure. 

**Attack Chain:** 

1. Visit a product, click Check stock, intercept the request in Burp Suite, and send it to Burp Intruder.
2. Change the stockApi parameter to http://192.168.0.1:8080/admin then highlight the final octet of the IP address (the number 1) and click Add §.
3. In the Payloads side panel, change the payload type to Numbers, and enter 1, 255, and 1 in the From and To and Step boxes respectively.
4. Click Start attack.
5. Click on the Status column to sort it by status code ascending. You should see a single entry with a status of 200, showing an admin interface.
6. Click on this request, send it to Burp Repeater, and change the path in the stockApi to: /admin/delete?username=carlos 

**Why the Vulnerability Exists:**

-The application trusts the user-controlled stockApi parameter and allows the server to make requests to arbitrary internal addresses.
-Because the server has access to internal systems that are not directly reachable by an external user, this functionality can be abused to:
-Discover internal hosts.
-Access internal services.
-Reach administrative interfaces.
-Perform actions using the application's internal network access.
-This demonstrates a Server-Side Request Forgery (SSRF) vulnerability.
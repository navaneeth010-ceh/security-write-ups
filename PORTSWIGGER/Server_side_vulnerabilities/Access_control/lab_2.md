# Lab: Unprotected admin functionality with unpredictable URL

**Core Issue:**

Information Disclosure
The admin panel URL `/admin-nbja94` is "hidden" by being unpredictable, but it's 
exposed in the client-side JavaScript code. Any user can:
1. View the page source (or intercept with Burp)
2. Search for keywords like "admin"
3. Extract the URL from script tags

**Attack Chain:**

1. Inspect the home-page using web-browser dev-tool or by intercepting response using Burp suite.
2. Search for keyword 'admin'.
3. It reveals path to admin-panel [/admin-nbja94] in the script.
4. Go to the admin-panel and delete carlos.

**Overview:** Disclosed admin-panel in javascript and unauthorized access to admin-panel is possible. 
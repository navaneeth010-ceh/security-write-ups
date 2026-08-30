# Lab: User role controlled by request parameter

**The Core Problem:**
The application stores the user's role in a cookie set by the server (`Admin=false`), 
but then **trusts the client to enforce authorization**. If the cookie says `Admin=true`, 
the browser shows admin features. The server never verifies this claim.

**Steps:**

1. Browse to /admin and observe that you can't access the admin panel. 
2. Browse to the login page. 
3. In Burp Proxy, turn interception on and enable response interception. 
4. Observe that the response sets the cookie Admin=false. Change it to Admin=true. 
5. Load the admin panel and delete carlos. 
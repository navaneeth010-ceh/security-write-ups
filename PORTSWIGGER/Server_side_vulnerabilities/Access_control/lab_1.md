# Lab: Unprotected admin functionality

**The Core Issue:**
The admin panel exists at `/administrator-panel` but has NO access control checks.
Any user—authenticated or not—can access it and perform admin actions.

**Attack Chain:**

1. Go to the lab and view robots.txt by appending /robots.txt to the lab URL. Notice that the Disallow line discloses the path to the admin panel. 
2. In the URL bar, replace /robots.txt with /administrator-panel to load the admin panel. 
3. Delete carlos. 

**Overview:**

The disallow funtionallity is not secure enough to protect admin-panel.
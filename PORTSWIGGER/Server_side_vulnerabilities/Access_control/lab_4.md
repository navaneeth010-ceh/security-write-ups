# Lab: User ID controlled by request parameter, with unpredictable user IDs 


**The Problem:**
The application exposes user account pages via a user ID parameter in the URL. 
While the IDs themselves are unpredictable (not sequential), the access control 
logic doesn't verify that the logged-in user owns the account they're viewing. 
This allows horizontal privilege escalation.

**Attack Chain** 

1. Discover a valid user ID from public information (blog posts, comments, etc.). 
2. Click on carlos and observe that the URL contains his user ID, Make a note of this ID. 
3. Log in using the supplied credentials and access your account page. 
4. Change the "id" parameter to the saved user ID. 
5. Retrieve and submit the API key. 


**Why This Matters in VAPT:**
This is one of the most common vulnerabilities I find in real applications. 
Developers often assume that because user IDs are unpredictable, they're "hidden" 
and therefore safe. In reality, IDs appear in:
- Blog posts/author profiles (like in this lab)
- API responses
- Email headers
- Referrer logs
- OAuth/social logins

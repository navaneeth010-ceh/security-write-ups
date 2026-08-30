# Lab: User ID controlled by request parameter with password disclosure

**Attack chain:**
1. Log in using the supplied credentials and access the user account page.
2. Change the "id" parameter in the URL to administrator.
3. View the response in Burp and observe that it contains the administrator's password.
4. Log in to the administrator account and delete carlos. 

**The Real Problem:**

Even if access control was *perfect* (you could only view your own account), 
the fact that passwords are returned in responses means:
- **Credential theft** — any breach of the response (intercepted via HTTP, cached, logged) exposes passwords
- **Lateral movement** — stolen admin password grants full access
- **Account takeover** — permanent access, even after password reset

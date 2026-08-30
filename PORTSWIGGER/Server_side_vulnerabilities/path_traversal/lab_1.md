# Lab: File path traversal, simple case

**Attack Chain:**

1.  Use Burp Suite to intercept and modify a request that fetches a product image. 
2.  Modify the filename parameter, giving it the value: ../../../etc/passwd
3.  Observe that the response contains the contents of the /etc/passwd file. 

**Payload:** ../../../etc/passwd

**Why '/etc/passwd'?**
On Linux, '/etc/passwd' is world-readable and contains usernames/UIDs.
It's a reliable test for path traversal because:
- It's a known file location
- It's often readable even by unprivileged processes
- Confirms file-read capability
- Doesn't require system-level access
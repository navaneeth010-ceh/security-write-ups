# Lab: Basic SSRF against the local server

**Steps:**
1. Browse to /admin and observe that you can't directly access the admin page.
2. Visit a product, click "Check stock", intercept the request in Burp Suite, and send it to Burp Repeater.
3. Change the URL in the stockApi parameter to http://localhost/admin. This should display the administration interface.
4. Read the HTML to identify the URL to delete the target user, which is: http://localhost/admin/delete?username=carlos
5. Submit this URL in the stockApi parameter, to deliver the SSRF attack. 

**Why SSRF is Critical:**

SSRF doesn't just bypass firewalls—it bypasses **everything** that trusts the server:

1. **Firewall rules** — Internal services trust localhost
2. **Cloud metadata endpoints** — AWS, Azure, GCP expose credentials at `http://169.254.169.254/latest/meta-data/`
3. **Internal APIs** — Database management interfaces, admin panels, monitoring systems
4. **Private network services** — Internal dashboards, wikis, chat servers
5. **Local services** — Redis, Memcached, databases running on localhost

An attacker can:
- Read configuration files
- Steal credentials
- Compromise internal systems
- Pivot into the network
- Cause denial of service (request internal resources repeatedly)

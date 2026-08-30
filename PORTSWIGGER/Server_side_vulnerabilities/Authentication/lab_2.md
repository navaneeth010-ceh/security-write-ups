# Lab: 2FA simple bypass

**The Core Problem:**

The application has a fundamental flaw in its **authentication flow**:

1. User enters username/password ✓
2. Password verified, **session created** ← HERE'S THE BUG
3. User sent to 2FA verification page
4. User enters 2FA code (or navigates away)
5. Session grants access to account

The problem: **A valid session is created BEFORE 2FA is verified.**

**Attack Chain:**

1. Log in with victim's credentials
2. Intercepted at 2FA prompt (asks for verification code)
3. **Manually navigate to `/my-account`** (change the URL)
4. Session is still valid (created after password, before 2FA check)
5. Server grants access to account page **without re-verifying 2FA**
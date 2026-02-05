# VWO Login Page Test Cases

**Role:** Senior QA Manager / Architect
**Date:** 2026-02-04
**Application:** [app.vwo.com](https://app.vwo.com)

---

| Test Case ID | Test Case Name | Steps | Expected Result | Actual Result | Status | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_VWO_01** | Valid Login | 1. Navigate to https://app.vwo.com<br>2. Enter a valid registered email.<br>3. Enter the correct password.<br>4. Click the "Sign In" button. | User should be successfully logged in and redirected to the VWO Dashboard. | | Pending | High |
| **TC_VWO_02** | Invalid Password | 1. Navigate to https://app.vwo.com<br>2. Enter a valid registered email.<br>3. Enter an incorrect password.<br>4. Click the "Sign In" button. | An error message should appear: "The email address or password you entered is incorrect" [ASSUMPTION]. User remains on the login page. | | Pending | High |
| **TC_VWO_03** | Invalid Email Format | 1. Navigate to https://app.vwo.com<br>2. Enter an invalid email format (e.g., "user@com").<br>3. Enter any password.<br>4. Click the "Sign In" button. | The system should display a validation error: "Please enter a valid email address" [ASSUMPTION]. | | Pending | High |
| **TC_VWO_04** | Empty Credentials | 1. Navigate to https://app.vwo.com<br>2. Leave both Email and Password fields blank.<br>3. Click the "Sign In" button. | Validation messages should appear for both fields: "Email is required" and "Password is required" [ASSUMPTION]. | | Pending | High |
| **TC_VWO_05** | Remember Me Functionality | 1. Navigate to https://app.vwo.com<br>2. Enter valid credentials.<br>3. Check the "Remember Me" checkbox.<br>4. Click "Sign In".<br>5. Log out and close the browser.<br>6. Re-open the login page. | The email field should be pre-filled with the user's email address. | | Pending | Medium |
| **TC_VWO_06** | Forgot Password Redirection | 1. Navigate to https://app.vwo.com<br>2. Click on the "Forgot Password" link. | User should be redirected to the password reset/recovery page. | | Pending | Medium |
| **TC_VWO_07** | SSO Login Redirection | 1. Navigate to https://app.vwo.com<br>2. Click on "Sign in using SSO" [ASSUMPTION - Link/Button name]. | User should be redirected to the SSO authentication provider page. | | Pending | Medium |
| **TC_VWO_08** | Password Masking | 1. Navigate to https://app.vwo.com<br>2. Type a password into the password field. | The password should be masked (e.g., asterisks or bullets) and not visible as plain text. | | Pending | High |
| **TC_VWO_09** | UI - Responsive Layout | 1. Navigate to https://app.vwo.com<br>2. Resize the browser window to mobile and tablet dimensions. | The login form and all elements (logo, fields, buttons) should adjust gracefully to the screen size without overlapping or losing functionality. | | Pending | Medium |
| **TC_VWO_10** | UI - Cross-Browser Compatibility | 1. Open the login page in Chrome, Firefox, Safari, and Edge. | The page layout, fonts, and colors should remain consistent across all supported browsers. | | Pending | Medium |
| **TC_VWO_11** | Edge Case - Account Lockout | 1. Navigate to https://app.vwo.com<br>2. Enter a valid email.<br>3. Enter incorrect passwords repeatedly (e.g., 5-10 times). | The account should be temporarily locked or a CAPTCHA should appear to prevent brute-force attacks [ASSUMPTION]. | | Pending | High |
| **TC_VWO_12** | Edge Case - SQL Injection | 1. Navigate to https://app.vwo.com<br>2. Enter SQL injection payloads (e.g., `' OR '1'='1`) into the fields. | The system must sanitize inputs and not execute any SQL commands. Generic error message should be shown. | | Pending | High |
| **TC_VWO_13** | Edge Case - XSS Injection | 1. Navigate to https://app.vwo.com<br>2. Enter script tags (e.g., `<script>alert(1)</script>`) into the fields. | The system should not execute any scripts and should sanitize the input properly. | | Pending | High |
| **TC_VWO_14** | Performance - Page Load Time | 1. Clear browser cache.<br>2. Navigate to https://app.vwo.com while recording network performance. | The login page should load completely within 2-3 seconds under standard network conditions. | | Pending | Low |
| **TC_VWO_15** | Performance - Concurrent Login Attempt | 1. Attempt to log in from multiple browser tabs/windows simultaneously with the same credentials. | The system should handle concurrent sessions according to the application's policy (either allow multiple or invalidate the previous session). | | Pending | Low |

---

### Notes & Constraints
- **[ASSUMPTION]**: Specific error message text and SSO link labels are assumed based on standard VWO patterns and general web standards, as live access was limited by environment constraints.
- Test cases follow the requirement of 15 years' experience standards (covering Functional, Security, UI, and Performance).
- Status is "Pending" as execution hasn't been performed.

# BStackDemo Advanced Payment & OTP Test Cases

**Role:** Senior QA Manager / Architect
**Application:** [bstackdemo.com](https://bstackdemo.com/signin?checkout=true)
**Focus:** Multi-Method Payments, OTP Flows, Security, and Performance

---

| Test Case ID | Test Case Name | Steps | Expected Result | Actual Result | Status | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_BSD_PAY_01** | Login & Redirect to Checkout | 1. Navigate to https://bstackdemo.com/signin?checkout=true.<br>2. Select 'demouser' and password 'testingisfun99'.<br>3. Click 'Sign In'. | User is successfully authenticated and redirected immediately to the checkout/address page. | | Pending | High |
| **TC_BSD_PAY_02** | Payment Method Selection - Credit Card | 1. Fill address details.<br>2. On Payment section, select 'Credit/Debit Card'.<br>3. Enter valid card number, expiry, and CVV. | Form accepts details and 'Checkout' button is enabled. | | Pending | High |
| **TC_BSD_PAY_03** | Payment Method Selection - PayPal | 1. Select 'PayPal' as payment method.<br>2. Click 'Checkout'. | User is redirected to the PayPal login/consent window. | | Pending | Medium |
| **TC_BSD_PAY_04** | Payment Method Selection - Google/Apple Pay | 1. Select 'Digital Wallet' (Google/Apple Pay).<br>2. Click 'Checkout'. | The native device/browser payment sheet should be triggered. | | Pending | Medium |
| **TC_BSD_OTP_01** | OTP - Success Flow (3D Secure) | 1. Enter valid Card details.<br>2. Click 'Checkout'.<br>3. On OTP screen, enter the correct 6-digit OTP received.<br>4. Click 'Submit'. | Order is placed successfully; "Your order has been placed successfully" message appears. | | Pending | High |
| **TC_BSD_OTP_02** | OTP - Incorrect OTP | 1. Proceed to OTP screen.<br>2. Enter an incorrect 6-digit code.<br>3. Click 'Submit'. | Error message: "Invalid OTP. Please try again" [ASSUMPTION]. User remains on the OTP screen. | | Pending | High |
| **TC_BSD_OTP_03** | OTP - Resend Functionality | 1. Wait for 30 seconds on OTP screen.<br>2. Click 'Resend OTP'. | Status message "New OTP sent to your registered mobile/email" appears. | | Pending | Medium |
| **TC_BSD_OTP_04** | OTP - Expired Code | 1. Wait for OTP to expire (e.g., 5 mins).<br>2. Enter the now-expired OTP.<br>3. Click 'Submit'. | Error message: "OTP has expired. Please request a new one". | | Pending | Medium |
| **TC_BSD_OTP_05** | OTP - Maximum Retries | 1. Enter incorrect OTP 3 times consecutively. | System should block further attempts and display "Too many attempts. Your transaction is cancelled for security". | | Pending | High |
| **TC_BSD_EDGE_01** | Zero Amount Transaction | 1. Add items worth $0 (if possible) or use a 100% discount code.<br>2. Proceed to payment. | System should bypass OTP/Payment and complete checkout directly. | | Pending | Low |
| **TC_BSD_SEC_01** | Data Masking in OTP | 1. View the OTP screen. | Mobile number/Email should be masked (e.g., +91 ******1234) to protect PII. | | Pending | Critical |
| **TC_BSD_SEC_02** | Payment Page - HTTPS Check | 1. Inspect the URL on the payment page. | The protocol must be HTTPS with a valid SSL certificate. | | Pending | Critical |
| **TC_BSD_ERR_01** | Network Interruption during OTP | 1. Click 'Submit' on OTP screen.<br>2. Simulate network disconnect immediately. | Application should show a "Connection Timed Out" error and allow the user to retry without double-charging. | | Pending | High |
| **TC_BSD_PERF_01** | OTP Screen Load Time | 1. Trigger the OTP flow. | The OTP redirection/iframe should load within 3 seconds. | | Pending | Low |
| **TC_BSD_PERF_02** | High Volume Concurrent OTP | 1. Trigger OTP for 50 concurrent sessions using automated tool. | Server should maintain 100% delivery rate for OTP codes without latency. | | Pending | Medium |

---

### **Notes & Methodology**
- **Template Context:** Follows the Senior QA Architect standard for comprehensive coverage (Functional, Security, Performance).
- **Assumptions:** OTP error messages and resend time-outs are based on standard financial gateway integrations (like Stripe/Braintree) as the environment is a sandbox demo.
- **Constraints:** Test cases are strictly for the specified domain: `bstackdemo.com`.

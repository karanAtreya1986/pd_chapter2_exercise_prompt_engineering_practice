# Forgot Password Test Cases

**Role:** Senior QA Engineer (10+ Years Experience)
**Reference Document:** PRD - Forgot Password Feature
**Date:** 2026-02-05

---

| TID | Category | Description | Pre-conditions | Steps | Expected | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TID_01** | Functional | Successful reset link request | User has a registered email | 1. Navigate to Forgot Password page.<br>2. Enter registered email.<br>3. Click submit. | System sends a reset link to the entered email. | High |
| **TID_02** | Functional | Create new password (Happy Path) | User has received a valid reset link | 1. Click on the reset link.<br>2. Enter a new password with 8 or more characters.<br>3. Submit. | Password is successfully updated. | High |
| **TID_03** | Boundary | Password with exactly 8 characters | User has received a valid reset link | 1. Click on the reset link.<br>2. Enter a password with exactly 8 characters.<br>3. Submit. | Password is successfully updated. | High |
| **TID_04** | Boundary | Password with 7 characters | User has received a valid reset link | 1. Click on the reset link.<br>2. Enter a password with 7 characters.<br>3. Submit. | [NEEDS CLARIFICATION] - Specific error message not specified in PRD. | High |
| **TID_05** | Edge | Link expiration (Post 24 hours) | User has a reset link older than 24 hours | 1. Click on the reset link after 24 hours of receipt. | [NEEDS CLARIFICATION] - System behavior for expired link not specified. | High |
| **TID_06** | Edge | Link accessed within 24-hour window | User has a reset link received 23 hours ago | 1. Click on the reset link.<br>2. Enter a valid new password.<br>3. Submit. | Password is successfully updated. | Medium |
| **TID_07** | Negative | Reset request with invalid email format | User is on Forgot Password page | 1. Enter an invalid email format.<br>2. Click submit. | [NEEDS CLARIFICATION] - Validation rules for email format not specified. | Medium |
| **TID_08** | Negative | Reset request with non-existent email | Email is not registered in the system | 1. Enter a non-registered email.<br>2. Click submit. | [NEEDS CLARIFICATION] - Success/Error behavior for non-existent email not specified. | Medium |
| **TID_09** | Negative | Creating password with 0 characters | User has received a valid reset link | 1. Click on the reset link.<br>2. Leave password field blank.<br>3. Submit. | [NEEDS CLARIFICATION] - System behavior for empty password not specified. | Medium |

---

### **Items for Clarification [NEEDS CLARIFICATION]**
1. **Error Messages:** No specific error messages are documented in the PRD for invalid inputs (e.g., short password, invalid email).
2. **Email Validation:** The PRD does not define what constitutes a "valid" email vs an "invalid" email format.
3. **Link Reuse:** It is not specified if a reset link can be used multiple times before it expires.
4. **Non-Existent User:** It is unclear if the system should reveal whether an email exists or provide a generic "Link sent if email exists" message for security.
5. **Password Complexity:** Beyond the "8+ characters" rule, it is not specified if symbols, numbers, or uppercase letters are required.
6. **Confirmation Step:** There is no mention of a "Confirm Password" field in the requirement.

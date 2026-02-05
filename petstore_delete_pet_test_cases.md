# Comprehensive Petstore API Test Cases: Delete Pet

**Endpoint:** `DELETE /pet/{petId}`
**Role:** API QA Engineer & Security Auditor
**Date:** 2026-02-05
**API Type:** REST (Swagger 2.0)

---

### **1. Positive Test Scenarios**
| Test ID | Scenario | Field | Input | Expected Status | Expected Message | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_DEL_POS_01** | Successful Deletion | `petId` | Valid existing ID (e.g., 101) | 200 OK | Pet deleted / Successful operation | High |
| **TC_DEL_POS_02** | Deletion with API Key | `api_key` | Valid Header + Valid ID | 200 OK | Successful operation | Medium |

### **2. Negative Test Scenarios**
| Test ID | Scenario | Field | Input | Expected Status | Expected Message | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_DEL_NEG_01** | Non-Existent ID | `petId` | 999999 (Not in DB) | 404 Not Found | Pet not found | High |
| **TC_DEL_NEG_02** | Invalid Data Type | `petId` | "string_id" | 400 Bad Request | Invalid ID supplied | High |
| **TC_DEL_NEG_03** | Empty ID | `petId` | (Empty trailing slash) | 405 Method Not Allowed | | High |

### **3. Edge Case Scenarios**
| Test ID | Scenario | Field | Input | Expected Status | Expected Message | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_DEL_EDGE_01** | Integer Boundary (Min) | `petId` | 1 | 200 or 404 | (Based on existence) | Low |
| **TC_DEL_EDGE_02** | Integer Boundary (Max) | `petId` | 9223372036854775807 | 200 or 404 | (Max int64 value) | Medium |
| **TC_DEL_EDGE_03** | Large ID (Overflow) | `petId` | 9223372036854775808 | 400 Bad Request | Invalid ID supplied | Medium |

### **4. Security Test Scenarios**
| Test ID | Security Vulnerability | Scenario | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- |
| **TC_DEL_SEC_01** | **Broken Authentication** | Call endpoint without the `petstore_auth` (OAuth2) token. | **401 Unauthorized** | Critical |
| **TC_DEL_SEC_02** | **Invalid Token** | Use an expired or malformed OAuth2 token in the Authorization header. | **401 Unauthorized** | Critical |
| **TC_DEL_SEC_03** | **Insufficient Privileges** | Use a token with `read:pets` scope but missing `write:pets` scope. | **403 Forbidden** | Critical |
| **TC_DEL_SEC_04** | **BOLA / IDOR** | Attempt to delete a pet ID that belongs to another user's account. | **403 Forbidden** or **404 Not Found** | Critical |
| **TC_DEL_SEC_05** | **SQL Injection** | Pass `' OR 1=1--` or `' UNION SELECT NULL--` in the `petId` path. | **400 Bad Request** / No DB leak | Critical |
| **TC_DEL_SEC_06** | **XSS Injection** | Pass `<script>alert(1)</script>` in the `api_key` header or path. | **400 Bad Request** / Input Escaped | High |
| **TC_DEL_SEC_07** | **HTTP Method Tampering** | Use `POST` or `PUT` on the `/pet/{petId}` path intended for DELETE. | **405 Method Not Allowed** | Medium |
| **TC_DEL_SEC_08** | **Exposure via Errors** | Submit invalid input; check if stack traces or DB details are revealed. | No sensitive info in response | High |
| **TC_DEL_SEC_09** | **Rate Limiting (DoS)** | Perform 1000+ delete requests in 1 second for the same/different IDs. | **429 Too Many Requests** | Medium |
| **TC_DEL_SEC_10** | **Session Fixation** | Attempt to use the same session identifier after the pet is deleted. | Session should not grant further unauthorized actions | Medium |

---

### **Security Methodology Note**
- **Authentication:** The `deletePet` operation strictly requires `petstore_auth` (OAuth2) as defined in the Swagger schema.
- **Input Sanitization:** The `petId` must be strictly cast to a 64-bit integer before processing in the backend to prevent injection attacks.
- **Authorization:** Implementation should verify that the authenticated user has ownership rights over the specific `petId` before finalizing the deletion.

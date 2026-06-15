# Security Findings

## Assessment Summary

| ID   | Finding                                       | Severity | Status    |
| ---- | --------------------------------------------- | -------- | --------- |
| F-01 | Missing Login Rate Limiting                   | Medium   | Confirmed |
| F-02 | Duplicate Product Reviews Allowed             | Low      | Confirmed |
| F-03 | Information Disclosure via File Upload Error  | Low      | Confirmed |
| F-04 | Information Disclosure via API Error Handling | Low      | Confirmed |

---

# F-01: Missing Login Rate Limiting

**Severity:** Medium

**CVSS v3.1:** 5.3 (Medium)

**OWASP Top 10:** A07:2021 – Identification and Authentication Failures

**Description**

The application did not implement account lockout, CAPTCHA, or request throttling after multiple failed authentication attempts. Unlimited login attempts increase the risk of password brute-force attacks.

**Impact**

* Increased likelihood of credential stuffing attacks.
* Increased risk of brute-force password guessing.

**Evidence**

* Multiple consecutive failed login attempts.
* No CAPTCHA presented.
* No account lockout observed.
* No rate limiting detected.

**Recommendation**

* Implement account lockout after a defined number of failed attempts.
* Introduce rate limiting for authentication endpoints.
* Consider CAPTCHA after repeated failures.
* Monitor authentication logs for suspicious activity.

---

# F-02: Duplicate Product Reviews Allowed

**Severity:** Low

**CVSS v3.1:** 3.7 (Low)

**OWASP Category:** Business Logic Issue

**Description**

The application allowed the same authenticated user to submit multiple reviews for the same product.

**Impact**

* Manipulation of product ratings.
* Reduced trustworthiness of review data.
* Potential abuse by malicious users.

**Evidence**

* Successfully submitted multiple reviews for the same product.

**Recommendation**

* Restrict each authenticated user to one review per product.
* Allow updates to existing reviews instead of creating duplicates.

---

# F-03: Information Disclosure via File Upload Error

**Severity:** Low

**CVSS v3.1:** 3.5 (Low)

**OWASP Top 10:** A05:2021 – Security Misconfiguration

**Description**

Uploading an unsupported file type caused the server to return an HTTP 500 response exposing internal implementation details, including source file names and stack trace information.

**Impact**

An attacker may gain insight into:

* Internal application structure
* Backend framework
* Source file locations

This information can assist further attacks.

**Evidence**

Observed error:

```
500 Error: Illegal file type

/juice-shop/build/routes/profileImageFileUpload.js
```

**Recommendation**

* Return generic error messages to clients.
* Disable stack traces in production.
* Log detailed errors only on the server.

---

# F-04: Information Disclosure via API Error Handling

**Severity:** Low

**CVSS v3.1:** 3.5 (Low)

**OWASP Top 10:** A05:2021 – Security Misconfiguration

**Description**

Malformed or unauthorized API requests returned verbose error responses containing internal file paths and stack traces.

**Impact**

The application disclosed backend implementation details that may assist attackers during reconnaissance.

**Evidence**

Example response:

```
Blocked illegal activity by ::ffff:192.168.65.1

/juice-shop/build/routes/orderHistory.js
```

**Recommendation**

* Suppress stack traces in production responses.
* Return generic error messages.
* Record detailed exceptions only in server-side logs.

---

# Security Controls Successfully Validated

The following controls were assessed and found to be functioning as expected during testing:

| Control                           | Result |
| --------------------------------- | ------ |
| SQL Injection Protection          | Passed |
| Basic XSS Protection              | Passed |
| JWT Signature Validation          | Passed |
| Dangerous File Upload Rejection   | Passed |
| Double Extension Upload Rejection | Passed |
| Unsupported File Type Validation  | Passed |

---

# Overall Risk Rating

**Overall Risk:** Medium

The application demonstrated effective protection against several common web application attacks, including SQL injection, unrestricted file upload, and JWT tampering. However, improvements are recommended in authentication controls, business logic validation, and error handling to reduce information disclosure and strengthen overall security posture.

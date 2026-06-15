# Penetration Testing Activity Log

## Assessment Information

**Target:** OWASP Juice Shop

**Environment:** Local Docker Lab

**Assessment Type:** Black Box Web Application Penetration Test

---

## Activity Timeline

### Phase 1 – Environment Setup

* Configured Kali Linux testing environment.
* Deployed OWASP Juice Shop using Docker.
* Verified application accessibility.
* Configured Burp Suite Community Edition as an intercepting proxy.

---

### Phase 2 – Reconnaissance

Activities performed:

* Port scanning using Nmap.
* Service identification.
* Technology fingerprinting.
* Initial application review.

Evidence:

* `scans/nmap.txt`

---

### Phase 3 – Directory Enumeration

Activities performed:

* Directory brute forcing.
* robots.txt inspection.
* Public resource enumeration.

Tools:

* Gobuster
* Nikto

Evidence:

* `scans/gobuster.txt`
* `scans/nikto.txt`

---

### Phase 4 – Vulnerability Scanning

Activities performed:

* Security header assessment.
* SQL Injection assessment.
* Information disclosure review.

Tools:

* Nikto
* SQLMap

Evidence:

* `scans/sqlmap.txt`

---

### Phase 5 – Authentication Testing

Activities performed:

* User registration.
* Login testing.
* Brute-force testing.
* Rate limiting verification.
* JWT inspection.

Result:

* No account lockout observed.
* No rate limiting detected.

---

### Phase 6 – Business Logic Testing

Activities performed:

* Duplicate review testing.
* Profile validation.
* Input validation.
* Workflow verification.

Result:

* Duplicate product reviews allowed.

---

### Phase 7 – File Upload Testing

Activities performed:

* Profile image upload testing.
* Dangerous extension validation.
* Double extension testing.
* SVG upload testing.
* Error handling assessment.

Result:

* Dangerous file types rejected.
* Stack trace disclosed during upload failures.

---

### Phase 8 – API Security Testing

Activities performed:

* Authentication verification.
* Authorization testing.
* HTTP method testing.
* Parameter manipulation.
* Error handling assessment.

Result:

* Unauthorized requests blocked.
* Stack trace exposed in error responses.

---

### Phase 9 – Documentation

Completed:

* Scope documentation.
* Testing methodology.
* Findings documentation.
* Final VAPT report preparation.

---

# Assessment Outcome

The assessment identified several low and medium severity issues related to authentication controls, business logic validation, and information disclosure.

No critical vulnerabilities such as SQL Injection, Remote Code Execution, or Cross-Site Scripting were confirmed during testing.

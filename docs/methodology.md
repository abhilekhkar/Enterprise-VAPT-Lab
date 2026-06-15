# Penetration Testing Methodology

## Overview

The Vulnerability Assessment and Penetration Testing (VAPT) engagement was conducted against the OWASP Juice Shop web application in a controlled laboratory environment. The objective was to identify security weaknesses through a combination of automated scanning and manual verification.

The assessment followed industry-recognized web application testing practices aligned with the OWASP Web Security Testing Guide (WSTG) and the OWASP Top 10 (2021).

---

# Testing Environment

* **Operating System:** Kali Linux
* **Target Application:** OWASP Juice Shop
* **Deployment:** Docker
* **Testing Type:** Black Box Web Application Assessment
* **Browser:** Firefox
* **Intercepting Proxy:** Burp Suite Community Edition

---

# Assessment Phases

## Phase 1 – Reconnaissance

Initial reconnaissance was performed to identify exposed services, technologies, and accessible resources.

### Activities

* Port scanning
* Service identification
* Banner enumeration
* Technology fingerprinting

### Tools

* Nmap



## Phase 2 – Content Discovery

Directory and endpoint enumeration were performed to identify hidden resources and publicly accessible files.

### Activities

* Directory enumeration
* robots.txt review
* Public endpoint discovery

### Tools

* Gobuster
* Nikto


## Phase 3 – Vulnerability Assessment

Automated scanners were used to identify common web application security issues.

### Activities

* Security header assessment
* Information disclosure testing
* SQL Injection assessment

### Tools

* Nikto
* SQLMap

---

## Phase 4 – Authentication Testing

Authentication controls were manually evaluated.

### Activities

* Login functionality
* Brute-force resistance
* Rate limiting assessment
* Account lockout verification
* JWT analysis

### Tools

* Burp Suite
* JWT.io

---

## Phase 5 – Business Logic Testing

Application workflows were manually tested for logical weaknesses.

### Activities

* Duplicate review submission
* Profile input validation
* Password reset behavior
* User workflow validation

---

## Phase 6 – File Upload Testing

The profile image upload functionality was assessed for file validation weaknesses.

### Activities

* Extension validation
* Double extension testing
* SVG upload testing
* Dangerous file upload testing
* Error handling review

---

## Phase 7 – API Security Testing

REST API endpoints were manually inspected.

### Activities

* Authentication verification
* Authorization testing
* HTTP method testing
* Parameter manipulation
* Error handling assessment

---

# Reporting

All confirmed findings were documented with:

* Severity rating
* Description
* Impact
* Evidence
* Remediation recommendations

Only validated findings were included in the final report to avoid false positives.

---

# Standards Referenced

* OWASP Web Security Testing Guide (WSTG)
* OWASP Top 10 (2021)
* CVSS v3.1
* Common Weakness Enumeration (CWE)

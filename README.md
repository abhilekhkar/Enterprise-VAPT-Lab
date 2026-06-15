# Enterprise Web Application VAPT Lab – OWASP Juice Shop

## Overview

This project demonstrates a complete **Web Application Vulnerability Assessment and Penetration Test (VAPT)** performed against the OWASP Juice Shop application. The assessment combines automated security scanning with manual penetration testing to identify security vulnerabilities and evaluate the application's security posture.

> **Disclaimer:** This assessment was performed in a controlled lab environment on OWASP Juice Shop, an intentionally vulnerable application designed for security training.

---

# Objectives

* Perform reconnaissance and enumeration.
* Identify common web application vulnerabilities.
* Assess authentication and authorization controls.
* Evaluate business logic flaws.
* Test file upload security.
* Assess REST API security.
* Document findings and recommend remediations.

---

# Scope

**Target Application:** OWASP Juice Shop

**Target IP:** 192.168.1.36

**Testing Type:** Black Box Web Application Penetration Testing

**Environment:** Local Lab

---

# Tools Used

* Burp Suite Community Edition
* Nmap
* Gobuster
* Nikto
* SQLMap
* Firefox Developer Tools
* Kali Linux
* Docker
* JWT.io

---

# Testing Methodology

The assessment followed a structured penetration testing methodology:

1. Reconnaissance
2. Service Enumeration
3. Authentication Testing
4. JWT Analysis
5. Cross-Site Scripting (XSS) Testing
6. Broken Access Control (IDOR)
7. Business Logic Testing
8. File Upload Testing
9. API Security Testing
10. Reporting

---

# Findings Summary

| Finding                                | Severity     |
| -------------------------------------- | ------------ |
| No Login Rate Limiting                 | Medium       |
| Duplicate Product Reviews Allowed      | Low          |
| Information Disclosure via Stack Trace | Low          |
| File Upload Validation Enforced        | Passed       |
| JWT Signature Validation               | Passed       |
| XSS Protection                         | Passed       |
| SQL Injection                          | Not Detected |

---

# Project Structure

```text
Enterprise-VAPT-Lab/
│
├── docs/
├── evidence/
├── payloads/
├── reports/
├── scans/
├── scripts/
├── tools/
├── wordlists/
└── README.md
```

---

# Evidence

The repository contains:

* Burp Suite screenshots
* Nmap scan results
* Nikto scan results
* SQLMap results
* Business Logic testing evidence
* File Upload testing evidence
* API Security testing evidence

---

# Skills Demonstrated

* Web Application Penetration Testing
* API Security Testing
* Business Logic Assessment
* Authentication Testing
* JWT Security Analysis
* File Upload Security Testing
* Burp Suite Repeater
* Vulnerability Validation
* Security Reporting
* Risk Assessment

---

# References

* OWASP Testing Guide
* OWASP Top 10 (2021)
* CWE (Common Weakness Enumeration)
* CVSS v3.1

---

# Author

**Abhilekh Kar**

MSc AI & Cybersecurity

Christ University

---

# License

This project is intended for educational and portfolio purposes only.

# Assessment Scope

## Engagement Overview

This Vulnerability Assessment and Penetration Testing (VAPT) engagement was conducted against the OWASP Juice Shop application in a controlled laboratory environment for educational and portfolio purposes.

The assessment focused on identifying security vulnerabilities through reconnaissance, automated scanning, and manual penetration testing.

---

# Target Information

| Item               | Details                                       |
| ------------------ | --------------------------------------------- |
| Target Application | OWASP Juice Shop                              |
| Deployment         | Docker                                        |
| Target Host        | 192.168.1.36                                  |
| Target Port        | 3000                                          |
| Protocol           | HTTP                                          |
| Testing Type       | Black Box Web Application Penetration Testing |

---

# Objectives

The objectives of this assessment were to:

* Identify exposed services and endpoints.
* Assess authentication and authorization mechanisms.
* Evaluate business logic security.
* Test file upload functionality.
* Assess REST API security.
* Identify information disclosure issues.
* Validate security controls against common web application attacks.

---

# In Scope

The following areas were included in the assessment:

* Web Application Reconnaissance
* Port and Service Enumeration
* Directory Enumeration
* Authentication Testing
* Authorization Testing
* JWT Analysis
* SQL Injection Testing
* Cross-Site Scripting (XSS) Testing
* Business Logic Testing
* File Upload Testing
* REST API Security Testing
* Error Handling Assessment

---

# Out of Scope

The following activities were intentionally excluded:

* Denial of Service (DoS) attacks
* Distributed Denial of Service (DDoS)
* Social Engineering
* Phishing
* Physical Security Testing
* Wireless Security Testing
* Source Code Review
* Infrastructure Penetration Testing
* Operating System Exploitation

---

# Rules of Engagement

* Testing was performed only against the designated target application.
* Testing was conducted within a controlled lab environment.
* No attacks were performed against third-party systems.
* Findings were manually validated where applicable.
* Only confirmed vulnerabilities are included in the final report.

---

# Limitations

* Assessment was performed using the Community Edition of Burp Suite.
* Testing was limited to functionality exposed by the web application.
* Results represent the application's security posture at the time of testing.

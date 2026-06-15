Enterprise Web Application Vulnerability Assessment & Penetration Testing Report
Project: Enterprise Web Application VAPT Lab

Target: OWASP Juice Shop

Assessment Type: Black Box Web Application Penetration Test

Environment: Local Docker Lab

Tester: Abhilekh Kar

Date: April 2026

Executive Summary
I conducted a Vulnerability Assessment and Penetration Test against the OWASP Juice Shop application to get a realistic picture of where it stands security-wise. Over the course of the engagement, I put the app through its paces — authentication flows, business logic, file uploads, REST APIs, and the usual suspects from the OWASP Top 10.
The results were mixed, in a good way. A handful of low and medium severity issues surfaced, mostly around rate limiting and error handling. The more serious stuff — SQL injection, remote code execution, XSS — didn't pan out. The protections there are working.

Scope
What I tested:

Web application security across authentication, authorization, JWT handling, business logic, file uploads, API endpoints, information disclosure, SQL injection, and XSS.
What I didn't touch:

Denial of Service, social engineering, physical security, infrastructure, and source code.

How I Approached It
I followed OWASP's Web Security Testing Guide alongside the OWASP Top 10 (2021). The work moved through eight phases: reconnaissance, enumeration, vulnerability assessment, authentication testing, business logic testing, file upload testing, API security testing, and finally this report.
Nothing fancy about the methodology — just working through it systematically and documenting what I found (and what I didn't).

Tools
Kali Linux was my base. From there I used Burp Suite Community Edition for intercepting and manipulating traffic, Nmap for port/service scanning, Gobuster for directory brute-forcing, Nikto for automated web scanning, SQLMap for injection testing, JWT.io for token analysis, Docker for the lab environment, and Firefox Developer Tools for client-side inspection.

What I Found
IDFindingSeverityF-01Missing Login Rate LimitingMediumF-02Duplicate Product Reviews AllowedLowF-03Information Disclosure via File Upload ErrorsLowF-04Information Disclosure via API Error HandlingLow
F-01 — Missing Login Rate Limiting (Medium)

The login endpoint doesn't throttle repeated attempts. An attacker can fire off as many password guesses as they like without any pushback from the server. This is the kind of thing that makes credential stuffing and brute-force attacks trivially easy. It's the most impactful finding from this engagement and should be addressed first.
F-02 — Duplicate Product Reviews Allowed (Low)

The application lets the same user submit multiple reviews for a single product. There's no deduplication logic on the backend, which means review scores can be manipulated artificially. Not a critical flaw, but it's a business logic gap worth closing.
F-03 — Information Disclosure via File Upload Errors (Low)

When an unsupported file type is uploaded, the error message the server returns is a bit too chatty. It leaks details about the backend environment that could help an attacker map the system. Generic error messages would do the job just as well without giving anything away.
F-04 — Information Disclosure via API Error Handling (Low)

Similar story on the API side. Some error responses include stack traces or internal details. In production, that's a problem — it hands reconnaissance data to anyone willing to poke around with a few bad requests.

What's Actually Working
Not everything was a finding. Several controls held up under testing and deserve to be called out:
SQL injection defenses are solid — SQLMap didn't find a foothold anywhere. Basic XSS protections are in place and blocked the test payloads I threw at them. JWT signature validation is enforced properly; I wasn't able to tamper with tokens and have them accepted. File upload restrictions are doing their job — dangerous file types and double extensions were rejected. API endpoints correctly require authentication; unauthenticated requests get turned away.

What I'd Recommend
Do these first:

Implement rate limiting on the login endpoint. Pair it with an account lockout policy after a defined number of failed attempts — five to ten is typical. If locking out accounts isn't practical for your use case, a CAPTCHA after a threshold of failures would at least slow things down meaningfully.
Worth addressing soon:

Block duplicate reviews at the backend level. Whichever user submitted the first review for a product should be the only one who can update it, not add to it.
When you get a chance:

Swap out the verbose error messages for generic ones on both the file upload endpoint and the API. Stack traces and environment details should never reach the client in production. The file upload restrictions are good — keep them as-is.

Overall Risk Rating: Medium
The application is in reasonable shape. The fundamentals — injection protection, token validation, file upload security — are working. The gaps are real but not catastrophic. Tightening up authentication controls and cleaning up error handling would meaningfully improve the security posture without requiring major rework.

Wrapping Up
This assessment gave me a solid look at how the application behaves under adversarial conditions. Some things held up well; a few things need attention. The findings documented here are straightforward to remediate, and the controls that passed testing provide a decent foundation to build on.
Practically speaking, this work covered web application pentesting, authentication analysis, API security assessment, business logic testing, file upload security, manual vulnerability validation, and professional security reporting — end to end.

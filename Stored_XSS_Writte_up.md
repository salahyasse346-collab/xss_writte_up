VULNERABILITY RESEARCH REPORT
Cross-Site Scripting (XSS) – Medium Severity CRUDS App – Task Management Application Date: 17/06/2026 
1. Executive Summary
During an independent security assessment of the CRUDS App (a web-based task management application), a Cross-Site Scripting (XSS) vulnerability was identified that allows an attacker to inject and execute arbitrary JavaScript code within the victim's browser. This vulnerability poses a significant risk to end users, potentially leading to arbitrary JavaScript execution, content manipulation, phishing attacks, and exposure of browser-stored application data.

2. Vulnerability Details
Category
Details
Vulnerability Type
Cross-Site Scripting (XSS) – -XSS
Target Application
CRUDS App – Task Management
Affected URL
https://sbrysrhan557-stack.github.io/CRUDS-App/
Severity
Medium
CVSS Score
6.3 (CVSS:3.1/AV:N/AC:L/PR:N/UI:R/S:C/C:H/I:L/A:N)
CVE Reference
CWE-79: Improper Neutralization of Input During Web Page Generation
Date Discovered
17/06/2026
Researcher
Salah Yasser Ali Sokair
Status
Unpatched – No Bug Bounty Program
3. Technical Description
The application stores user input in LocalStorage and renders it using innerHTML without proper sanitization.
4. Proof of Concept (PoC)
4.1 Steps to Reproduce
    1. Navigate to: https://sbrysrhan557-stack.github.io/CRUDS-App/ 
    2. Click "Add Task" and enter the following payload in the Title field: <img src=x onerror=alert(document.domain)> 
    3. Enter any text in the Description field and set any Status. 
    4. Click "Add Task" to save. 
    5. Click “In Progress”. 
    6. Observe that the JavaScript payload executes. 
5. Impact Assessment
    • Arbitrary JavaScript Execution: High
    • Content Manipulation: High
    • Local Storage Data Exposure: Medium
    • Phishing Attacks: Medium
    • Reputational Damage: Medium 
6. Remediation Recommendations
    • Implement input validation and output encoding. 
    • Use textContent instead of innerHTML. 
    • Sanitize with a library like DOMPurify. 
    • Implement a strict Content Security Policy (CSP). 
7. Responsible Disclosure Note
This vulnerability was discovered during an independent security research exercise. The affected application does not operate a formal Bug Bounty program. This report is for educational and portfolio purposes only. 

8. Visual Demonstration

<img width="1600" height="899" alt="WhatsApp Image 2026-06-15 at 12 57 34 PM" src="https://github.com/user-attachments/assets/0d0cd787-d49b-4cb1-b768-8f2e426da431" />

# Vulnerability Assessment: The Social Anti-Fake News System

This repository contains a comprehensive security assessment report for the **Social Anti-Fake News System**, a platform built with Spring Boot (Backend) and Vue.js (Frontend).

## 🛡️ Executive Summary
The assessment, conducted in January 2026, identified several **Critical** vulnerabilities that could lead to full system compromise. The findings emphasize the risks of improper API authorization and excessive trust in client-supplied data.

## 🔍 Key Vulnerabilities Found
* **[VULN-001] Sensitive Data Exposure:** API responses leaked sensitive User entity data, including BCrypt-hashed passwords.
* **[VULN-002] IDOR in Bookmarks:** Improper validation of `userId` in GET requests allowed unauthorized access to other users' data.
* **[VULN-003] BOLA in Comments:** Lack of server-side verification allowed attackers to post comments on behalf of any user.
* **[VULN-004] Privilege Escalation via Mass Assignment:** Weakness in the profile update endpoint allowed standard users to elevate their privileges to `ROLE_ADMIN`.

## 🛠️ Tools & Methodology
* **Methodology:** Black-box & Gray-box Testing.
* **Tools:** * **Burp Suite Community:** For intercepting and analyzing HTTP traffic.
    * **VS Code:** For code-level audit and remediation analysis.
    * **Browser DevTools:** For frontend JavaScript mapping and API endpoint identification.

## 💡 Recommended Mitigations
1.  **Implement DTOs:** Never return JPA entities directly; use Data Transfer Objects to filter sensitive fields.
2.  **Server-Side Identity Verification:** Always extract the user identity from the verified **JWT claims**, never from request parameters or bodies.
3.  **Field Whitelisting:** Use strict mapping for update requests to prevent Mass Assignment attacks.

---
**Prepared by:** Sattaya Mingsanthia (Software Engineering @ CAMT)
**Date:** January 14, 2026

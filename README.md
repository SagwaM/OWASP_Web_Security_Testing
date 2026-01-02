# 🔍 OWASP ZAP Vulnerability Scan & WSTG Investigation

Target: DVWA (Damn Vulnerable Web Application), Cisco Ethical Hacker Course (ParoCyber).

## 📌 Overview

This lab demonstrates the use of OWASP Zed Attack Proxy (ZAP) to perform an automated vulnerability scan against an intentionally vulnerable web application (DVWA). The scan results are then analyzed, and a critical finding is further investigated using the OWASP Web Security Testing Guide (WSTG) to understand exploitation techniques and testing methodology.

Screenshots included in this repository (see PDF) document:

- Scan initiation and progress

- Alert output

- Detailed vulnerability inspection

## 🧪 Lab Environment

- Operating System: Kali Linux

- Target Application: DVWA

- Target URL: http://172.17.0.2/dvwa

- Security Tool: OWASP ZAP

### 🛠️ Step 1: Automated Vulnerability Scan Using OWASP ZAP
**Workflow**

1. Launched the Kali Linux virtual machine.

2. Opened OWASP ZAP from the Kali application menu.

3. Selected Persist Session to ensure scan data could be saved and reviewed later.

4. Closed the Manage Add-ons dialog window.

5. Clicked Automated Scan from the ZAP main dashboard.

6. Entered the target URL:

`http://172.17.0.2/dvwa`


7. Clicked Attack to start the scan.

**Scan Process**

- ZAP first executed a spider crawl to discover accessible pages and endpoints.

- After crawling, ZAP performed active scanning, testing discovered resources for known web vulnerabilities.


### 🚨 Step 2: Scan Results and Alert Review
**Alerts Summary**

- Upon scan completion, ZAP automatically displayed results in the Alerts tab.

- Multiple alerts of varying risk levels were identified, as shown in the screenshots.

- These alerts represent common web application security issues present in DVWA.


## 🛑 Vulnerability Analysis: Remote Code Execution (CVE-2012-1823)
**Description**

One of the critical findings identified by ZAP was:

**Remote Code Execution – CVE-2012-1823**

This vulnerability affects **PHP when running in CGI mode** and allows attackers to execute arbitrary code on the target server.

**Source of the Vulnerability**

- The issue originates from improper handling of query string parameters in PHP-CGI.

- PHP interprets user-supplied parameters as command-line arguments when input validation is not enforced.

**Exploitation Method**

An attacker can exploit this vulnerability by:

- Crafting a malicious HTTP request

- Injecting PHP configuration directives via the URL

- Forcing the server to execute arbitrary PHP code

**Potential Impact**

- Full system compromise

- Unauthorized access to sensitive data

- Web shell installation or persistent backdoors


### 📚 Step 3: WSTG Reference Investigation
**WSTG Mapping**

- The ZAP alert includes an OWASP WSTG reference tag

- This tag links directly to a relevant section of the OWASP Web Security Testing Guide

**Purpose of Using WSTG**

By following the WSTG reference:

- The vulnerability can be understood beyond automated detection

- Manual testing techniques are provided

- Expected behaviors and validation steps are outlined

This highlights how WSTG complements automated tools like ZAP by offering structured, repeatable testing guidance.

## 🛡️ Remediation Recommendations

To mitigate vulnerabilities such as CVE-2012-1823:

1. Avoid running PHP in CGI mode

2. Apply security patches and use updated PHP versions

3. Disable dangerous PHP directives

4. Implement strong server-side input validation

5. Deploy a Web Application Firewall (WAF)


## 🎯 Key Takeaways

1. Automated scanners are effective for identifying common vulnerabilities.

2. Critical findings require manual validation and deeper understanding.

3. The OWASP WSTG provides essential structure and consistency to penetration testing.

4. Combining tools and frameworks results in more accurate and meaningful security assessments.


# 📬 Contact

For questions or collaboration:
- 📧 Maria Sagwa
- 🔗 GitHub: [repo](https://github.com/SagwaM/OWASP_Web_Security_Testing)
- 🔗 Medium: [profile](https://medium.com/@sagwamkaari/scanning-a-vulnerable-web-application-with-owasp-zap-wstg-d16a0094c16f)
- Cisco Ethical Hacker course by **ParoCyber**

# Penetration Test: GreenOptic: 1 (Vulnhub)

This directory contains all the artifacts and documentation for a comprehensive penetration test conducted on the "GreenOptic: 1" virtual machine from Vulnhub.

The engagement was performed as a black-box test, simulating a real-world scenario where an attacker has no prior knowledge of the internal infrastructure. The primary objective was to achieve full system compromise (`root` access) and deliver professional-grade reports suitable for both technical and executive stakeholders.

### Attack Path Summary

The path to compromise involved chaining multiple vulnerabilities across different services:

1.  **Initial Foothold:** An initial web server reconnaissance revealed a **Local File Inclusion (LFI)** vulnerability.

2.  **Information Gathering:** The LFI was leveraged to read sensitive system files, including `/etc/passwd`, a `.htpasswd` file for a protected web area, and user mailboxes located in `/var/mail/`.

3.  **Credential Discovery:** This process revealed passwords for a phpBB forum and a password-protected `.zip` file. Further analysis of a `.pcap` file within the archive exposed cleartext **FTP credentials**.

4.  **Lateral Movement:** The compromised FTP credentials were successfully reused for **SSH access**, granting a user-level shell on the target system.

5.  **Privilege Escalation:** Full root access was achieved by exploiting two well-known local privilege escalation vulnerabilities: **PwnKit (CVE-2021-4034)** and **Sudo Baron Samedit (CVE-2021-3156)**.

6.  **Post-Exploitation:** A **Stored XSS** vulnerability was identified in the phpBB forum and exploited to hook an administrator's browser using the **BeEF Framework**, demonstrating impact beyond server compromise.

### Technical Highlights & Skills Demonstrated

This project showcases hands-on proficiency in the following areas:

*   **Web Application Pentesting:** Manual discovery and exploitation of LFI and Stored XSS vulnerabilities.
*   **Privilege Escalation on Linux:** Identifying and exploiting kernel/system-level vulnerabilities.
*   **Script Analysis & Modification:** Adapting a public Python exploit script (CSRF/RCE) to function correctly within the target environment.
*   **Network Traffic Analysis:** Extracting cleartext credentials from captured network traffic (`.pcap` file) using Wireshark.
*   **Methodical Reporting:** Creating detailed, structured reports suitable for a professional engagement.
*   **Presentation Skills:** Summarizing technical findings into a clear and concise presentation format.

### Project Artifacts

*   **[Penetration Test Report](./Penetration_Test_Report.pdf):** The final, client-ready report detailing all findings, risk ratings, and remediation advice.
*   **[Attack Methodology](./Penetration_Test_Methodology.pdf):** A step-by-step narrative of the entire attack, from reconnaissance to root.
*   **[Modified Exploit Script](./exploit_CSRF_Webmin_modificato.py):** The customized Python script used during the engagement.
*   **[Executive Summary Presentation](./Greenoptic_Presentation.pdf):** A PDF version of the slide deck summarizing the project.
*   **[Evidence Files](./artifacts/):** A sub-directory containing supporting evidence, such as Nessus, Nmap and OpenVAS scan results.

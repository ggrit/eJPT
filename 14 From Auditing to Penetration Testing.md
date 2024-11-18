# 14 From Auditing to Penetration Testing

- We will use a practical example to explain and demonstrate how security audits work, how they are performed and how they relate to a penetration test.
- The objective of this section is to provide you with tacit knowledge of how results from security audits affect the objectives and scope of a penetration test, in addition to outlining the changes/adaptations that need to be made when performing a pentest for an organization that is required to comply with specific standards or regulations.

## Phase 1 - Develop a Security Policy

**Background:**
- Company: SecureTech Solutions

**Description:**
- SecureTech Solutions is a fictitious cybersecurity consultancy that specializes in securing IT infrastructure for various clients.
- In this example, we will be demonstrating the process of developing a security policy for Linux servers, performing a risk assessment using the NIST SP 800-53 framework, performing a security audit and testing the remediations.
- This example will guide you through the entire process, from initial policy creation to auditing and penetration testing, highlighting the importance of compliance with industry standards.

**Objectives:**
- Establish a baseline security policy for Linux servers that aligns with NIST SP 800-53 guidelines, ensuring that servers are configured and managed securely.
- This policy should ensure that Linux servers are secure and protected from unauthorized access, vulnerabilities, and other security threats.
- It will be used to establish baseline security requirements for configuring, maintaining, and monitoring Linux servers within the organization, aligned with NIST SP 800-53.

**Security Policy Development Process: Requirements Gathering**
- Purpose: Define the purpose and scope of the security policy.
- Access Control: Outline user account management, authentication methods, and privilege management.
- Audit and Accountability: Specify logging requirements and log review procedures.
- Configuration Management: Define baseline configurations, software update practices, and change management.
- Identification and Authentication: Enforce strong password policies and unique user identification.
- System and Information Integrity: Implement malware protection, security monitoring, and vulnerability management.
- Maintenance: Outline controlled maintenance and approved maintenance tools.

**Simple Security Policy for Linux Servers Aligned with NIST SP 800-53**

| Policy Area                                | Control ID | Policy Statement                                                                                                                                                                                                                                                                                                      |
| ------------------------------------------ | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Access Control (AC)**                    | AC-2, AC-5 | User Accounts: Only authorized personnel shall be granted access to Linux servers.<br>Each user must have a unique user account; shared accounts are prohibited.<br>Inactive accounts must be disabled or removed within 30 days.                                                                                     |
|                                            | IA-2, IA-5 | Authentication: Enforce strong password policies: minimum length of 12 characters, including upper/lower case letters, numbers, and special characters. Use SSH key-<br>based authentication where possible; disable password-based SSH access.<br>Implement two-factor authentication (2FA) for privileged accounts. |
| **Audit and Accountability (AU)**          | AU-2, AU-3 | System Logging: Enable and configure system logging to capture critical events. Use rsyslog or journald for centralized logging.                                                                                                                                                                                      |
|                                            | AU-6, AU-7 | Log Review: Regularly review logs for suspicious activities. Retain logs for at least 90 days.                                                                                                                                                                                                                        |
| **Configuration Management**               | CM-2       | Configuration Baseline: Maintain a secure baseline configuration for all Linux servers.<br>Use configuration management tools (e.g., Ansible, Puppet) to enforce configurations.                                                                                                                                      |
|                                            | CM-3, CM-5 | Software Updates: Keep the system and installed software up to date. Apply security patches within 30 days of release.                                                                                                                                                                                                |
| **Identification and Authentication (IA)** | IA-5       | Password Management: Enforce password complexity and expiration policies. Use password managers to securely store and manage passwords.                                                                                                                                                                               |
|                                            | IA-4       | User Identification: Ensure all users are uniquely identified.                                                                                                                                                                                                                                                        |
| **System and Information Integrity (SI)**  | SI-3       | Malware Protection: Implement malware detection and prevention measures.<br>Regularly scan servers for malware.                                                                                                                                                                                                       |
|                                            | SI-4       | Security Monitoring: Monitor systems for security breaches or anomalies.<br>Use tools like Lynis to perform regular security audits.                                                                                                                                                                                  |
| **Maintenance**                            | MA-2       | Controlled Maintenance: Perform regular maintenance on servers according to documented procedures.                                                                                                                                                                                                                    |
|                                            | MA-3       | Maintenance Tools: Use only approved maintenance tools and ensure they are secure.                                                                                                                                                                                                                                    |

## Phase 2 - Security Auditing with Lynis

**Objective:**
Perform a security audit on a Linux server using Lynis, identify vulnerabilities, and remediate the findings based on the security policy.

**1. Installing and Running Lynis:**
- Install Lynis: Install Lynis on the Linux server.
- Audit the Server: Run a Lynis audit scan on the target Linux server.
- Review the Report: Analyze the Lynis report to identify security issues and recommendations.

**2. Remediation:**
- Address Findings: Remediate vulnerabilities identified in the Lynis report (e.g., updating software, enforcing password policies).
- Update Security Policy: Document remediation actions and update the security policy to reflect changes.

## Phase 3 - Conduct Penetration Test

**Objective:** 
To validate the effectiveness of remediation actions through a penetration test, ensuring that the Linux server is secure and compliant with the security policy.

**1. Execution:**
- Network Scan: Use Nmap to identify open ports and services.
- Vulnerability Scanning: Use Metasploit to find and exploit vulnerabilities.
- Web Application Testing: Use Burp Suite to test web applications (if applicable).

**2. Validating Remediation:**
- Compare Results: Compare initial audit findings with penetration test results to verify that vulnerabilities have been addressed.
- Check for New Vulnerabilities: Identify and remediate any new vulnerabilities introduced during the remediation phase.

**3. Reporting:**
- Executive Summary: Provide an overview of the penetration test and major findings.
- Methodology: Detail the tools and techniques used during the test.
- Findings: Describe vulnerabilities found, including severity and potential impact.
- Recommendations: Offer steps to further secure the system.

#eJPT #cybersecurity 
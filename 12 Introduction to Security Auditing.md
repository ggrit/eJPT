# 12 Introduction to Security Auditing

## Overview of Security Auditing

Security Auditing is a systematic process of evaluating and verifying the security measures and controls in place within an organization to ensure they are effective, appropriate, and compliant with relevant standards, policies, and regulations.

It involves reviewing various aspects of the organization's information systems, networks, applications, and operational procedures to identify vulnerabilities, weakness, and area for improvement.

### Importance of Security Auditing
1. **Identifying Vulnerabilities and Weaknesses:**
	 1. Security audits help uncover vulnerabilities and weaknesses in an organization's information systems and infrastructure that could be exploited by attackers.
	 2. Regular audits ensure that security controls are effective and up-to-date, minimizing the risk of breaches.
2. **Ensuring Compliance:**
	1. Organizations must comply with various regulatory requirements and industry standards to protect sensitive data and maintain trust with customers and stakeholders
	2. Security audits help verify compliance with standards such as GDPR, HIPAA, PCI DSS, and ISO 27001, avoiding legal and financial penalties.
3. **Enhancing Risk Management:**
	1. Audits provide comprehensive assessment of an organization's security posture, identifying and prioritizing risks based on their potential impact.
	2. Effective risk management strategies can be developed and implemented based on audit findings to mitigate identified risks.
4. **Improving Security Policies & Procedures:**
	1. Security audits review the effectiveness of existing security policies and procedures, identifying areas for improvement.
	2. Updated and robust security policies and procedures help creare a strong security culture within the organization.
5. **Supporting Business Objectives:**
	1. A strong security posture supports overall business objectives by ensuring that critical business operations are protected from disruptions caused by security incidents.
	2. Audits help build customer trust and confidence, as clients are assured that their data in handled securely and responsibly.
6. **Continuous Improvement:**
	1. Security auditing is not a one-time activity an ongoing process that promotes continuous improvement.
	2. Regular audits ensure that security measures evolve to address new threats and vulnerabilities, maintaining a proactive approach to security.

## Essential Terminology

| **Term**              | **Definition**                                                                                                                | **Importance**                                                                                                   |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Security Policies** | Formal documents that define an organization's security objectives, guidelines, and procedures to protect information assets. | Establishes the framework for implementing and enforcing security controls.                                      |
| **Compliance**        | Adherence to regulatory requirements, industry standards, and internal policies related to security and data protection.      | Ensures that the organization meets legal obligations and best practices.                                        |
| **Vulnerability**     | A weakness in a system or process that can be exploited to gain unauthorized access or cause harm.                            | Identifying vulnerabilities is crucial for assessing and improving security measures.                            |
| **Control**           | A safeguard or countermeasure implemented to mitigate risks and protect information assets.                                   | Controls are designed to prevent, detect, or respond to security threats and weaknesses.                         |
| **Risk Assessment**   | The process of identifying, analyzing, and evaluating risks to an organization's information assets.                          | Help prioritize security measures based on the likelihood and impact of identified risks.                        |
| **Audit Trail**       | A chronological record of events and activities that provides evidence of actions taken within a system.                      | Supports accountability and traceability during security audits and investigations.                              |
| **Compliance Audit**  | An examination of an organization's adherence to regulatory requirements and industry standards.                              | Validated whether the organization meets the necessary compliance criteria and identifies areas for improvement. |
| **Access Control**    | Measures and mechanisms used to regulate who can access specific information or systems and what actions they can perform.    | Protects sensitive information from unauthorized access and misure.                                              |
| **Audit Report**      | A formal document that presents the findings, conclusions, and recommendations resulting from a security audit.               | Communicates audit results and provides guidance for improving security practices.                               |

## Security Auditing Process/Lifecycle

1. **Planning and Preparation:**
	1. Define Objectives and Scope: Determine the goals of the audit and the specific systems, processes, and controls to be evaluated.
	2. Gather Relevant Documentation: Collect policies, procedures, network diagrams, and previous audit reports.
	3. Establish Audit Team and Schedule: Assemble the audit team and set a timeline for the audit activities.
2. **Information Gathering:**
	1. Review policies and Procedures: Examine the organization's security policies, procedures, and standards.
	2. Conduct Interviews: Interview key personnel to understand security practices and identify potential gaps.
	3. Collect Technical Information: Gather data on system configurations, network architecture, and security controls.
3. **Risk Assessment:**
	1. Identify Assets and Threats: List critical assets and potential threats to those assets.
	2. Evaluate Vulnerabilities: Assess existing vulnerabilities in systems and processes.
	3. Determine Risk Levels: Assign risk levels based on the likelihood and impact of identified threats and vulnerabilities.
4. **Audit Execution:**
	1. Perform Technical Testing: Conduct technical assessments such as vulnerability scans, penetration test, and configuration reviews.
	2. Verify Compliance: Check adherence to relevant regulations and standards.
	3. Evaluate Controls: Assess the effectiveness of security controls and practices.
5. **Analysis and Evaluation:**
	1. Analyze Findings: Review data collected during the audit to identify security weakness and area for improvement.
	2. Compare Against Standards: Measure the organization's security posture against industry standards and best practices.
	3. Prioritize Issues: Rank findings based on their severity and potential impact on the organization.
6. **Reporting:**
	1. Documents Findings: Create a detailed report outlining audit findings, including identified vulnerabilities, non-compliance issues, and ineffective controls.
	2. Provide Recommendations: Offer actionable recommendations to address identified issues and enhance security.
	3. Present Results: Share the audit report with relevant stakeholders and discuss key findings and recommendations.
7. **Remediation:**
	1. Develop Remediation Plans: Work with the organization to create plans for addressing the audit findings.
	2. Implement Changes: Assist in implementing recommended changes and improvements.
	3. Conduct Follow-Up Audits: Schedule follow-up audits to ensure that remediation efforts have been completed and are effective.
	4. Monitor and Update: Continuously monitor the organization's security posture and update security measures as needed.

## Types of Security Audits

| **Securitty Audit**    | **Objective**                                                                                                                                                   | **Importance**                                                                                                                                                  | **Example**                                                                                                                                                   |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Internal Audits**    | Conducted by the organization's internal audit team or security professionals to evaluate the effectiveness of internal controls and compliance with policies.  | Internal audits provide insight into the organization's self-assessment of its security posture and highlight areas that may require more in-depth testing.     | An internal audit might review user access controls to ensure that only authorized personnel have access to sensitive data.                                   |
| **External Audits**    | Performed by independent third-party auditors to provide an unbiased evaluation of the organization's security measures and compliance with external standards. | External audits often serve as benchmarks for compliance and security effectiveness. Penetration testers can use these findings to guide their testing efforts. | A company undergoing a PCI DSS compliance audit might hire an external auditor to validate its security controls and ensure they meet the required standards. |
| **Compliance Audits**  | Focus on verifying that the organization complies with specific regulatory requirements and industry standards (e.g., GDPR, HIPAA, PCI DSS).                    | Compliance audits help identify regulatory gaps that penetration testers can address through targeted testing.                                                  | A healthcare provider might undergo a HIPAA compliance audit to ensure that patient data is protected according to federal regulations.                       |
| **Technical Audits**   | Focus on assessing the technical aspects of the organizations's IT infrastructure, including hardware, software, and network configurations.                    | Technical audits provide a detailed view of the technical controls in place, highlighting areas where penetration testing can uncover vulnerabilities.          | A technical audit might involve a thorough review of firewall configurations to ensure they are properly securing the network perimeter.                      |
| **Network Audits**     | Assess the security of the organization's network infrastructure, including routers, switches, firewalls, and other network devices.                            | Network audits can reveal vulnerabilities in network design and configurations that penetration testers can exploit to assess network security.                 | A network audit might identify insicure protocols being used for data transmission, prompting penetration testers to test for potential exploits.             |
| **Application Audits** | Evaluate the security of software applications, focusing on code quality, input validation, authentication mechanisms, and data handling.                       | Application audits highlight security flaws in applications that penetration testers can exploit to demonstrate real-word attack scenarios.                     | An application audit might reveal vulnerabilities such as SQL injection or cross-site scripting (XSS) in a web application.                                   |

## Security Auditing & Penetration Testing

- In order for you to operate successfully as penetration tester, it is imperative that you understand **when, how and why** Security Audits are performed and how they relate to and affect penetration testing.
- The reason this is important is because Security Audits and Penetration testing are two separate types of security assessments that have their own unique scope, objectives and desired outcomes.
- Furthermore, given the separation, it is important to understand when each is performed (sequentially), and whether they can be combined into a singular process/assessment.
- Before we dive into the when and the how, we first need to understand the differences between a Security Audit and a Penetration Test, more specifically, the differences in their objectives, scope and outcomes.
- Understanding the differences between the two will paint a clearer picture as to when each assessment is performed and how they (potentially) feed into each other.

|                 | **Security Audit**                                                                                                                                                                                     | **Penetration Test**                                                                                                                                                                      |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Purpose**     | Evaluate an organization's overall security posture by assessing compliance with policies, standards, and regulations. It focuses on the effectiveness of security controls, processes, and practices. | Simulate real-world attacks to identify and exploit vulnerabilities in systems, networks, or applications. It focuses on technical weaknesses and how they can be exploited by attackers. |
| **Scope**       | Comprehensive, covering various aspects such as policies, procedures, technical controls, physical security, and compliance with regulations.                                                          | Specific to the systems, networks, or applications being tested. The scope is defined to focus on particular areas of interest.                                                           |
| **Methodology** | Tipically involves reviewing documentation, conducting interviews, performing technical assessments, and evaluating compliance with security standards.                                                | Involves using various tools and techniques to attempt to breach systems, exploit vulnerabilities, and assess the effectiveness of security defenses.                                     |
| **Outcome**     | Identifies gaps in security policies, procedures and controls. Provides recommendations for improving overall security and ensuring compliance.                                                        | Provides a detailed assessment of vulnerabilities and potential attack vectors. Offers recommendations for mitigating identified risks and improving security defenses.                   |
| **Frequency**   | Often performed on a regular basis (eg., annually or biannually) or as required by compliance regulations.                                                                                             | Typically performed as needed, such as after significant changes to systems, on a regular schedule, or as part of compliance requirements.                                                |

### Sequential Approach

- **Perform Security Audit First**: Companies often conduct a security audit fist to evaluate their overall security posture, ensure compliance with regulations, and identify areas for improvement in policies and procedures.
- **Conduct Penetration Test Afterwards**: Based on the findings of the audit, a penetration test may be performed to assess the effectiveness of technical controls and identify specific vulnerabilities. 

#### Advantages

- Provides a comprehensive view of security from both policy and technical perspectives.
- Identifies and addresses gaps in both procedural and technical controls.
- Helps prioritize remediation efforts based on audit findings.

### Combined Approach

- **Integrate Security Audit and Penetration Testing:** Some organizations choose to combine security audits and penetration tests, often through a holistic security assessment that incorporates both elements.

#### Advantages

- Streamlines the assessment process by combining policy, procedural, and technical evaluations.
- Provides a more complete picture of the organization's security posture in a single engagement.
- Can be more efficient and cost-effective by addressing both compliance and technical vulnerability simultaneously.

### Example: Sequential Approach

- Consider a fictional organization, "SecurePayments Inc.", which processes credit card transactions and **must adhere to PCI DSS standard**
- In this example, "SecurePayments Inc." is using a sequential approach to assess their overall security posture. The organization has already performed a security audit through an indipendent audit firm and are using the findings in the audit report as the basis of their remediation plan/efforts.
- As part of their remediation plan, the organization has decided to hire you (or your firm) to perform a penetration test with a focus on ensuring PCI DSS compliance.
- The external audit performed by the indipendent audit firm outlined the following findings:
	- Inadequate encryption for cardholder data in transit.
	- Weak/inadequate network security controls and traffic monitoring.
	- Weak access control policies that allow excessive permissions.
	- Outdated incident response procedures.
- The corresponding recommendations for the findings outlined above are:
	- Implement strong encryption protocols for data in transit.
	- Revise access control policies to follow the principle of least privilege.
	- Update and test incident response procedures regularly.

**The company followed the Security Audit lifecycle/process outlined in the "Security Auditing Process/Lifecycle" video and made the necessary improvements based on the recommendations.**

**SecurePayments Inc. - Penetration Test**

**Objectives:**
- After making the necessary changes/improvements based on the findings and recommendations in the external audit report, "SecurePayments Inc." has hired you to the the **Technical controls** and **security measures** implemented **based on audit findings** to verify whether they are effective.

**Phase 1: Planning and Preparation:**
During the initial phase, you identify that the PCI DSS scope includes the cardholder data environment (CDE). You review SecurePayments Inc.'s network diagrams and PCI DSS self-assessment questionnaires to understand their current security measures and compliance status.

**Objectives:**
- Define the scope of the penetration test to focus on the areas identified in the audit, such as network security and application vulnerabilities.
- Set up a testing schedule and inform stakeholders.

**Phase 2: Information Gathering and Reconnaissance:**
- You gather information on SecurePayments Inc's security policies, such as their access control policies, encryption standards, and incident response procedures.
- You also review their most recent PCI DSS audit report to identify areas of concern highlighted by auditors.

**Phase 3: Penetration Test Execution:**
- Conduct network scanning, enumeration and vulnerability assessments to identify weaknesses, misconfigurations or vulnerabilities.
- Attempt exploitation of identified vulnerabilities to assess their impact.
- Test the effectiveness of newly implemented encryption and access controls.

**Phase 4: Findings and Recommendations:**
- Outcome: The penetration test uncovers additional vulnerabilities:
	- An exposed administrative interface that allows unauthorized access.
	- SQL injection vulnerabilities in a customer-facing web application.
- Recommendation:
	- Secure the administrative interface by implementing additional authentication and access controls.
	- Path the SQL injection vulnerabilities and conduct a thorough review of application security.

**Summary of Sequential Approach**

- Security Audit Results:
	- Identified compliance gaps and policy deficiencies.
	- Provided recommendations for improving security policies and procedures.
- Penetration Testing Results:
	- Revealed specific technical vulnerabilities.
	- Offered targeted recommendations to address these technical weaknesses.


#eJPT #cybersecurity 
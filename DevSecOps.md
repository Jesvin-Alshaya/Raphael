**12/3/25**
DevSecOps

1. **Continuous integration and delivery (CI/CD) and automation**: The use of automated security testing and deployment enabling organizations to build and deploy secure software quickly and efficiently.
2. **Cloud security** - securing cloud environments. e.g. securing cloud infrastructure, containers, and serverless environments and including all of protecting sensitive data
3. **Compliance and regulatory requirements-** comply with a growing number of regulatory requirements.
4. **Application security**
5. **Cloud Native Security**
6. **Container security**
7. **Cybersecurity skills shortage**
8. **Zero trust security =>** which assumes that all network traffic is potentially malicious
9. **Security culture**
10. **DevSecOps Maturity**
11. **Incident Response**
12. **Third-party security**
13. \*\*Supply Chain security-\*\*software supply chain refers to the entire lifecycle of software, from its initial design and coding to its deployment and maintenance. It includes various components such as:

* Source Code: The original code written by developers.
* Dependencies: Third-party libraries and components that enhance functionality.
* Build Systems: Tools that automate the compilation and assembly of software.
* Testing and Quality Assurance: Processes to ensure the software functions correctly and securely.
* Distribution: The methods used to deliver the software to end-users, including packaging and deployment artifact

15\. Vulnerability Management:

16.Cyber Threat Intelligence



Main parts of

1. **SAST (Static Application Security Testing)=>** method of security testing that analyzes the source code of an application while it is being developed. It helps identify potential vulnerabilities in the code
2. DAST (Dynamic Application Security Testing):**method of security testing that analyzes an application while it is running.**
3. IAST (Interactive Application Security Testing):combines the benefits of SAST and DAST
4. RASP (Runtime Application Self-Protection):method of security testing that monitors the application in real-time and provides protection against known and unknown attacks.



#### 2.1 Roles and Responsibilities

* **Planning** ->Defining security requirements and overall security architecture for the software and infrastructure. With Project Management Team
* **Design** with Sec Arch \& GRC regarding  =>Governance over security policy implementation

                                           Audit of Secure coding best-practices

                                           Coordination on regulatory compliance

                                           Recommendations for remediation or compensating controls

* **Development**
* **Testing** with VAPT and GRC by Automating security testing and validation, running security scans and penetration testing to identify vulnerabilities.

GRC team will involve on RAF Process for unknown vulnerability fixes.

* Deployment
* Operations/ Monitoring > SOC + DR + Regional IT support
* Compliance, Auditing, investigation, and Patching with CSRIT \& CDC



#### 2.2 Phases

PHASES                                            TOOLS

Source Code Analysis/Code                        SonarQube

Software Composition Analysis (SCA)              CheckmarX SCA

SAST                                             FortifySCA/CheckmarX

DAST                                             WebInspect/Acuentix

Container Scan                                   Qualys Container Scan/Docker Scan



12/4/25

* threat modeling to map threat in pipeline
  all communication through TLS
* access control list with  RBAC
* regular audit
* least privilege
* Secure credentials who access these credentials
* making sure all secrets are encrypted and injected during  run time
* No secrets in source code
* never print a secret in console log
* 2FA authentication \& signed commits minimum by 2 people for repo
* access control for repo
* git protect and also secure and maintain backup locally
* continue testing into ci/cd pipeline ensuring all backdoors are closed and doing OWASP top 10 for DAST testing security control audit
* Data security especially with PII



Azure Pipeline Hardening

* 2FA+RBAC+Limit access with least privilege
* security scanning
* code review
* Encryption of all data and tls for communication
* regular updates



12/5/25

* Once the source code
* Select to hide  the dev code the options
* Once Vulnerability is taken the the first go top then medium and low
* the Single once is considered as confirmed risk and the remarked confirmed and then move to next one
* once there is two of same vulnerability check which has more better version if same move to CVSS score goes to highest and the second one is exploit not proposed and remark it as duplicate.

  **Inclusion to VAPT, SPOKE with Audit team not GRC.**


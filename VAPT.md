VAPT

12/8/25

1\) OWASP TOP 10 -2025 



* A01:2025 - Broken Access Control + , Server-Side Request Forgery (SSRF) 40 

How to prevent.

1. Except for public resources, deny by default.
2. Implement access control mechanisms once and reuse them throughout the application, including minimizing CORS usage.
3. should enforce record ownership 
4. Disable web server directory listing and ensure file metadata (e.g., .git) and backup files are not present within web roots.
5. Log access control failures, alert admins when appropriate
6. Implement rate limits on API and controller access to minimize the harm from automated attack tooling.

* A02:2025 - Security Misconfiguration 16 CWE =>An automated process to verify the effectiveness of the configurations and settings in all environments. \& Proactively add a central configuration to intercept excessive error messages as a backup.

The application might be vulnerable if:

1. missing appropriate security hardening across any part of the application stack or improperly configured permissions on cloud services
2. Unnecessary features are enabled or installed 
3. Default accounts and their passwords are still enabled and unchanged.
4. A lack of central configuration for intercepting excessive error messages
5. The security settings in the application servers, application frameworks are not set to secure values.
6. server Dont send security headers or not set to secure values



* A03:2025 - Software Supply Chain Failures => expansion of Vulnerable and Outdated Components 

vulnerable if:-

1. carefully track the versions of all components, libraries,  platform, frameworks, and dependencies that you use vulnerable, or unsupported/outdated.
2. not tracking of changes within your supply chain,
3. Doesnt have two person approval 
   pipeline doesn't have a access control and least privilege
4. &nbsp;use components from untrusted sources, for use in production.
   not fixing or upgrade the underlying platform, frameworks, and dependencies in a risk-based, timely fashion

How to prevent.

Know your Software Bill of Materials (SBOM) of your entire software and manage it dictionary centrally.

Track their (transitive) dependencies also



* A04:2025 - Cryptographic Failures 

How to prevent.

Classify and label data processed, stored, or transmitted by an application.

Store your most sensitive keys in a hardware 

Use well-trusted AND UPDATED implementations of cryptographic algorithms

Protect all information whether it PCI or PII

encrypt all sensitive data at rest
all communication through TLS with forward secrecy ciphers, use HSTS
Store passwords using strong adaptive and salted hashing functions with a work factor (delay factor), such as Argon2, scrypt, bcrypt (legacy systems) or PBKDF2-HMAC-SHA-256.

use of  CSPRNG (cryptographically secure pseudo random number generator)with  the initialization vector (IV)

Password into Keys and any key that is should be generated cryptographically randomly and stored in memory as byte arrays. 





* A05:2025 - Injection 
* A06:2025 - Insecure Design 
* A07:2025 - Authentication Failures
* A08:2025 - Software or Data Integrity Failures 
* A09:2025 - Logging \& Alerting Failures
* A10:2025 - Mishandling of Exceptional Conditions
&nbsp;


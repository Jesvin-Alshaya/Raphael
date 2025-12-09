VAPT
12/8/25
1) OWASP TOP 10 -2025

⦁	A01:2025 - Broken Access Control + , Server-Side Request Forgery (SSRF) 40
How to prevent.
1.	Except for public resources, deny by default.
2.	Implement access control mechanisms once and reuse them throughout the application, including minimizing CORS usage.
3.	should enforce record ownership
4.	Disable web server directory listing and ensure file metadata (e.g., .git) and backup files are not present within web roots.
5.	Log access control failures, alert admins when appropriate
6.	Implement rate limits on API and controller access to minimize the harm from automated attack tooling.
⦁	A02:2025 - Security Misconfiguration 16 CWE =>An automated process to verify the effectiveness of the configurations and settings in all environments. & Proactively add a central configuration to intercept excessive error messages as a backup.
The application might be vulnerable if:
1.	missing appropriate security hardening across any part of the application stack or improperly configured permissions on cloud services
2.	Unnecessary features are enabled or installed
3.	Default accounts and their passwords are still enabled and unchanged.
4.	A lack of central configuration for intercepting excessive error messages
5.	The security settings in the application servers, application frameworks are not set to secure values.
6.	server Dont send security headers or not set to secure values

⦁	A03:2025 - Software Supply Chain Failures => expansion of Vulnerable and Outdated Components
vulnerable if:-
1.	carefully track the versions of all components, libraries,  platform, frameworks, and dependencies that you use vulnerable, or unsupported/outdated.
2.	not tracking of changes within your supply chain,
3.	Doesnt have two person approval
pipeline doesn't have a access control and least privilege
4.	 use components from untrusted sources, for use in production.
not fixing or upgrade the underlying platform, frameworks, and dependencies in a risk-based, timely fashion
How to prevent.
Know your Software Bill of Materials (SBOM) of your entire software and manage it dictionary centrally.
Track their (transitive) dependencies also

⦁	A04:2025 - Cryptographic Failures
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


⦁	A05:2025 - Injection
⦁	A06:2025 - Insecure Design
⦁	A07:2025 - Authentication Failures
⦁	A08:2025 - Software or Data Integrity Failures
⦁	A09:2025 - Logging & Alerting Failures
⦁	A10:2025 - Mishandling of Exceptional Conditions

12/9/25
JWT or Json Web token
it is data transmitted from server to client

it made up of header and a payload =>(Header).(Payload)
eyJhbGciOiJub25l4oCdfQ.ewogICJpZCI6ICIxMjM0NTY3ODkwIiwKICAibmFtZSI6ICJKb2huIERvZSIsCiAgImFnZSI6IDM2Cn0K =>example of a token
JOSE(JSON Object Signing and Encryption ) header:
{
  "alg": "none"
}
// base64url encoded to: eyJhbGciOiJub25l4oCdfQ
Claims:
{
  "id": "1234567890",
  "name": "John Doe",
  "age": 36
}
// base64url encoded to: ewogICJpZCI6ICIxMjM0NTY3ODkwIiwKICAibmFtZSI6ICJKb2huIERvZSIsCiAgImFnZSI6IDM2Cn0

JWT aren’t sent directly as JSON strings because they’re UTF-8 encoded meaning that they can contain characters that aren’t URL-safe so in order to make tokens URL-safe, they’re encoded into base64url format. This allows them to be safely put in query parameters and authorization headers.
JWT is Signed with cryptographically generated signature
                                                   /\
                                                  /  \
                                                    |
This is a string of characters created by hashing the payload and header (or just the payload) using the algorithm specified in the JOSE header. After generation, the signature is base64url encoded and added to the JWS
JWT signature ->  sure it wasnt tampered
algorithms (alg) =>
⦁	HS256 / HS384 / HS512 — HMAC with SHA-2 (symmetric key; same secret to sign & verify)
⦁	RS256 / RS384 / RS512 — RSA PKCS#1 v1.5 with SHA-2 (asymmetric; private key signs, public key verifies)
⦁	PS256 / PS384 / PS512 — RSA-PSS with SHA-2 (asymmetric; more modern padding)
⦁	ES256 / ES384 / ES512 — ECDSA over P-256/P-384/P-521 (asymmetric)
⦁	EdDSA (Ed25519 / Ed448) — Edwards-curve signatures (asymmetric; compact, modern)

How the signature is generated (step-by-step)

Serialize header and payload as compact JSON (no extra whitespace).
Base64URL-encode each separately (no padding =).
Concatenate with a dot: encodedHeader + "." + encodedPayload.
Sign that string using the algorithm and key.
Base64URL-encode the raw signature bytes to get the JWT’s 3rd part.

s the signature is directly derived from the rest of the token, changing a single byte of the header or payload results in a mismatched signature.

Without knowing the server's secret signing key, it shouldn't be possible to generate the correct signature for a given header or payload.

Attacks on JWT
These are attacks that exploit weaknesses in JWT implementation or configuration:

1.	Algorithm Confusion Attack
If the server accepts the alg header without validation, an attacker can change it from RS256 (asymmetric) to HS256 (symmetric) and use the public key as the HMAC secret to forge tokens.
2. None Algorithm Attack
If the server allows alg: none, the attacker can remove the signature and send an unsigned token, which might be accepted.
3. Weak Secret Key
If the HMAC secret is weak or guessable, brute-force attacks can generate valid signatures.
4.Key Leakage
If keys are exposed in logs, code repositories, or error messages, attackers can sign their own tokens.
5.JWT Injection
Malicious payloads in JWT claims can lead to injection attacks if the application uses claims unsafely (e.g., SQL injection via sub claim).
6.Replay Attack
If tokens don’t expire or lack proper revocation, attackers can reuse stolen tokens indefinitely.
7.Timing Attacks
Poor signature comparison (non-constant time) can leak information about the secret key.
SSL handshake

CORS
is a browser security mechanism that allows controlled access to resources hosted on a different domain than the one serving the web page.
GET POST HEAD
No stand preflight to request to server from bowser

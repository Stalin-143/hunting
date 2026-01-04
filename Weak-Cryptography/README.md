# Weak Cryptography

## Description
Weak cryptography vulnerabilities occur when applications use outdated, weak, or improperly implemented cryptographic algorithms and protocols. This can lead to data exposure, man-in-the-middle attacks, and other security breaches.

## Common Issues
- Use of weak hashing algorithms (MD5, SHA1)
- Weak encryption algorithms (DES, RC4)
- Hardcoded cryptographic keys
- Insufficient key lengths
- Improper SSL/TLS configuration
- Predictable random number generation

## Testing Approach
Identify cryptographic implementations and test for weak algorithms, hardcoded secrets, and improper configurations.

## Payloads
See `weak-crypto-payloads.txt` for a comprehensive list of weak cryptography indicators and test cases.

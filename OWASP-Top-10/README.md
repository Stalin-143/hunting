# OWASP Top 10 Security Testing Payloads

This directory contains comprehensive payload collections for testing applications against the OWASP Top 10 security risks (2021 edition). These payloads are intended for authorized security testing, penetration testing, and bug bounty hunting only.

## ⚠️ Legal Disclaimer

**IMPORTANT:** These payloads are for educational and authorized testing purposes only. Using these payloads against systems without explicit permission is illegal and unethical. Always obtain proper authorization before conducting security testing.

## Directory Structure

Each OWASP Top 10 category has its own directory containing:
- **README.md** - Description of the vulnerability category
- **Payload files** - Collections of test payloads specific to that category

## OWASP Top 10 (2021) Categories

### [A01 - Broken Access Control](./A01-Broken-Access-Control/)
Testing payloads for access control vulnerabilities including:
- Path Traversal
- IDOR (Insecure Direct Object References)
- Missing function level access control

### [A02 - Cryptographic Failures](./A02-Cryptographic-Failures/)
Testing payloads for cryptographic weaknesses including:
- Weak hashing algorithms
- Hardcoded credentials
- Insecure key storage

### [A03 - Injection](./A03-Injection/)
Comprehensive injection payloads including:
- **SQL Injection** - Database query manipulation
- **XSS (Cross-Site Scripting)** - Client-side code injection
- **Command Injection** - OS command execution
- **LDAP Injection** - Directory service manipulation

### [A04 - Insecure Design](./A04-Insecure-Design/)
Testing payloads for design flaws including:
- Business logic vulnerabilities
- Missing security controls
- Rate limiting bypass

### [A05 - Security Misconfiguration](./A05-Security-Misconfiguration/)
Testing payloads for configuration issues including:
- Default credentials
- Common misconfiguration paths
- Directory listing

### [A06 - Vulnerable and Outdated Components](./A06-Vulnerable-Outdated-Components/)
Reference lists of:
- Known vulnerable libraries
- Outdated components
- Version detection strings

### [A07 - Identification and Authentication Failures](./A07-Identification-Authentication-Failures/)
Testing payloads for authentication issues including:
- Authentication bypass techniques
- Weak password lists
- Session manipulation

### [A08 - Software and Data Integrity Failures](./A08-Software-Data-Integrity-Failures/)
Testing payloads for integrity issues including:
- Deserialization attacks
- Unsafe deserialization patterns

### [A09 - Security Logging and Monitoring Failures](./A09-Security-Logging-Monitoring-Failures/)
Testing payloads for logging issues including:
- Log injection attacks
- CRLF injection in logs

### [A10 - Server-Side Request Forgery (SSRF)](./A10-Server-Side-Request-Forgery/)
Testing payloads for SSRF vulnerabilities including:
- Internal network access
- Cloud metadata endpoints
- Protocol handler abuse

## Usage Guidelines

1. **Authorization First**: Always obtain written permission before testing
2. **Scope Definition**: Only test systems within the authorized scope
3. **Responsible Disclosure**: Report vulnerabilities responsibly
4. **Legal Compliance**: Follow all applicable laws and regulations
5. **Ethical Testing**: Never cause damage or access sensitive data without permission

## Testing Methodology

1. **Reconnaissance**: Understand the target application
2. **Vulnerability Identification**: Use payloads to identify potential issues
3. **Exploitation**: Validate vulnerabilities safely
4. **Documentation**: Record findings with evidence
5. **Reporting**: Submit detailed vulnerability reports

## Payload Usage

Payloads can be used in various contexts:
- **URL Parameters**: `?param=<payload>`
- **POST Data**: Form fields and JSON/XML bodies
- **Headers**: Custom HTTP headers
- **Cookies**: Cookie values
- **File Uploads**: File content and metadata

## Tools Integration

These payloads can be integrated with:
- Burp Suite
- OWASP ZAP
- ffuf/wfuzz
- SQLMap
- Custom scripts

## Contributing

This is a living resource. Contributions of new payloads, techniques, or improvements are welcome. Please ensure all contributions:
- Follow the existing structure
- Include clear documentation
- Focus on educational/testing value
- Maintain ethical standards

## Resources

- [OWASP Top 10 Official Site](https://owasp.org/www-project-top-ten/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)

## Version

Based on OWASP Top 10 - 2021

---

**Remember**: With great power comes great responsibility. Use these resources ethically and legally.

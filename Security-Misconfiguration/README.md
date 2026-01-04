# Security Misconfiguration

## Description
Security misconfiguration vulnerabilities arise from insecure default configurations, incomplete or ad-hoc configurations, open cloud storage, misconfigured HTTP headers, and verbose error messages containing sensitive information. These are among the most common security issues.

## Common Issues
- Default credentials
- Unnecessary features enabled
- Directory listing enabled
- Detailed error messages
- Outdated software
- Misconfigured security headers
- Open cloud storage buckets

## Common Attack Vectors
- Default admin interfaces
- Configuration files exposed
- Backup files accessible
- Development/debug modes enabled
- Unnecessary services running

## Testing Approach
Test for common misconfigurations, default credentials, exposed configuration files, and security header weaknesses.

## Payloads
See `default-credentials-payloads.txt` and `misconfiguration-paths-payloads.txt` for comprehensive lists of security misconfiguration tests.

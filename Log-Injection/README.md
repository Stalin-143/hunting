# Log Injection

## Description
Log injection vulnerabilities occur when an application includes untrusted data in log files without proper validation or encoding. Attackers can exploit this to forge log entries, inject malicious content into logs, or hide their activities by manipulating log data.

## Common Attack Vectors
- User input fields that get logged
- HTTP headers
- Error messages
- Authentication attempts
- Application events

## Common Techniques
- CRLF injection to create fake log entries
- Log forging
- Log poisoning
- Log file pollution

## Testing Approach
Submit special characters and control sequences in input fields that are logged to test for log injection vulnerabilities.

## Payloads
See `log-injection-payloads.txt` for a comprehensive list of log injection payloads.

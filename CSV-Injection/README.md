# CSV Injection (Formula Injection)

## Description
CSV Injection (also known as Formula Injection) is a vulnerability that occurs when websites embed untrusted input inside CSV files. When a spreadsheet application (like Microsoft Excel, LibreOffice Calc, or Google Sheets) opens a CSV file containing malicious formulas, it may execute the formulas, leading to arbitrary command execution, information disclosure, or other attacks.

## Common Attack Vectors
- Export functionality (user data, reports, analytics)
- Contact forms that export to CSV
- User profile data exports
- Order history exports
- Any feature that generates downloadable CSV files
- Import/Export features in CRM systems
- Billing and invoice downloads
- Survey results exports

## Testing Approach
Submit formula characters (=, +, -, @, \t, \r) followed by commands or formulas in:
- Name fields
- Address fields
- Comment/description fields
- Any user-controllable data that might be exported to CSV

## Risk Impact
- Remote code execution via DDE (Dynamic Data Exchange)
- Information disclosure (reading local files)
- SSRF (Server-Side Request Forgery)
- Credential theft
- Malware distribution

## Common Vulnerable Patterns
- Direct export of user input to CSV without sanitization
- Missing CSV encoding/escaping
- Lack of formula character stripping
- Client-side only validation

## Payloads
See `csv-injection-payloads.txt` for a comprehensive list of CSV injection payloads covering:
- Formula injection techniques
- DDE (Dynamic Data Exchange) attacks
- Command execution payloads
- Data exfiltration methods
- Multi-application compatibility

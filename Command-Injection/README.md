# Command Injection

## Description
Command injection is a cyber attack that involves executing arbitrary commands on a host operating system. This vulnerability occurs when an application passes unsafe user-supplied data to a system shell.

## Common Attack Vectors
- System administration interfaces
- File upload functionality
- Network diagnostic tools (ping, traceroute)
- Backup/restore functions
- Any feature that executes system commands

## Testing Approach
Submit command separators and system commands in input fields to test if the application executes arbitrary commands.

## Payloads
See `command-injection-payloads.txt` for a comprehensive list of command injection payloads.

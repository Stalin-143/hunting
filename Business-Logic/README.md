# Business Logic Vulnerabilities

## Description
Business logic vulnerabilities are flaws in the design and implementation of an application that allow an attacker to elicit unintended behavior. These vulnerabilities occur when the application's legitimate processing flow can be used in a way that results in a negative consequence to the organization.

## Common Issues
- Insufficient workflow validation
- Price manipulation
- Quantity manipulation
- Race conditions
- Bypassing business rules
- Abuse of functionality
- Lack of rate limiting

## Common Attack Vectors
- Payment processing
- Discount/coupon systems
- Account creation/management
- Transaction processing
- File upload limits
- Resource allocation

## Testing Approach
Understand the application's business logic and test for ways to manipulate or bypass intended workflows and rules.

## Payloads
See `business-logic-payloads.txt` for a comprehensive list of business logic testing scenarios and payloads.

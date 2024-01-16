

## Table of Contents

- [Broken Object Property Level Authorization](#broken-object-property-level-authorization)
  - [Excessive Data Exposure:](#excessive-data-exposure)
  - [Mass Assignment:](#mass-assignment)
  - [Object Property Level Authorization:](#object-property-level-authorization)
  - [Impact of Broken Object Property Level Authorization:](#impact-of-broken-object-property-level-authorization)
  - [How to spot Broken Object Property Level Authorization in an API?](#how-to-spot-broken-object-property-level-authorization-in-an-api)
  - [Example Attack Scenarios](#example-attack-scenarios)
    - [Scenario 1: Unauthorized Data Retrieval in a Healthcare API](#scenario-1-unauthorized-data-retrieval-in-a-healthcare-api)
    - [Scenario 2: Unauthorized Account Access in a Banking API](#scenario-2-unauthorized-account-access-in-a-banking-api)
  - [How To Prevent Broken Object Property Level Authorization?](#how-to-prevent-broken-object-property-level-authorization)
  - [Conclusion](#conclusion)


# Broken Object Property Level Authorization

This category combines **API3:2019 Excessive Data Exposure** and **API6:2019 - Mass Assignment**, focusing on the root cause: the lack of or improper authorization validation at the object property level. This leads to information exposure or manipulation by unauthorized parties.

Let's begin by exploring Excessive Data Exposure, Mass Assignment, and Object Property Level Authorization for a better understanding of these concepts.

## Excessive Data Exposure:
Excessive Data Exposure occurs when an application **unintentionally** reveals **more information** than **needed**, potentially exposing **sensitive data**. This vulnerability arises from inadequate security controls, posing risks of unauthorized access and data breaches. 

## Mass Assignment:

Mass Assignment is a security vulnerability that occurs when a user can manipulate an application's input parameters to assign values to unintended model properties. Typically found in web applications, this oversight allows attackers to modify sensitive data fields, gaining unauthorized access and potentially leading to unauthorized actions or data exposure.

## Object Property Level Authorization:

Object Property Level Authorization involves controlling access to specific properties or attributes of an object within a system. Instead of granting blanket access to an entire object, this approach enables fine-grained control, allowing administrators to restrict or permit access to individual properties based on user roles or permissions. This enhances security by limiting the exposure of sensitive data and ensuring that users can only interact with the properties they are authorized to access.


## Impact of Broken Object Property Level Authorization:

1. **Unauthorized Data Access:**
   - Broken Object Property Level Authorization can lead to unauthorized users accessing sensitive data within an object, compromising confidentiality and potentially violating privacy regulations.

2. **Data Tampering:**
   - Attackers may exploit broken property-level authorization to manipulate or modify specific properties within an object, leading to data integrity issues and potential misinformation.

3. **Elevation of Privileges:**
   - Insecure property-level authorization may result in unauthorized users gaining elevated privileges to access or modify properties beyond their intended scope, leading to security breaches and misuse.

4. **Compliance Violations:**
   - Organizations may face compliance issues, as broken property-level authorization can result in unauthorized access to sensitive information, potentially leading to legal consequences and reputational damage.


## How to spot Broken Object Property Level Authorization in an API?

- The API endpoint exposes properties of an object that are considered sensitive and should not be read by the user. 

- The API endpoint allows a user to change, add/or delete the value of a sensitive object's property which the user should not be able to access.


## Example Attack Scenarios

### Scenario 1: Unauthorized Data Retrieval in a Healthcare API

**Attack Details:**
In this scenario, an attacker exploits broken Object Property Level Authorization in a healthcare API to gain unauthorized access to sensitive patient data. The API, responsible for retrieving patient records, has inadequate authorization controls, allowing the attacker to manipulate the request parameters and access restricted information.

The attack involves the following key steps:

1. **Identification of Weakness:**
   - The attacker identifies vulnerabilities in the API's Object Property Level Authorization, realizing that insufficient checks exist when retrieving patient records.

2. **Manipulating Request Parameters:**
   - By carefully manipulating the request parameters, such as patient ID or record number, the attacker crafts requests that bypass intended restrictions, aiming to retrieve unauthorized patient data.

3. **Unauthorized Data Retrieval:**
   - Exploiting the broken Object Property Level Authorization, the attacker successfully retrieves sensitive patient information that should have been restricted. This could include medical history, diagnoses, and other confidential details.

4. **Potential Data Exfiltration:**
   - The attacker may further attempt to exfiltrate the retrieved data for malicious purposes, such as selling it on the dark web or using it for identity theft.

5. **Covering Tracks:**
   - To avoid detection, the attacker may modify or obfuscate their request parameters, making it challenging to trace the unauthorized data retrieval back to them.

**Mitigation:**
Implementing robust Object Property Level Authorization checks, validating input parameters, and encrypting sensitive data during transmission are critical measures to prevent unauthorized data retrieval attacks. Regular security audits and penetration testing can help identify and address vulnerabilities in the API's authorization mechanisms.

### Scenario 2: Unauthorized Account Access in a Banking API

**Attack Details:**
In this scenario, an attacker exploits broken Object Property Level Authorization in a banking API, gaining unauthorized access to specific account details. The API, responsible for retrieving account information, lacks proper authorization controls, enabling the attacker to manipulate parameters and access restricted account data.

The attack involves the following key steps:

1. **Identification of Weakness:**
   - The attacker identifies vulnerabilities in the API's Object Property Level Authorization, recognizing a lack of adequate checks when accessing specific account details.

2. **Parameter Manipulation:**
   - By manipulating parameters in the API request, such as account number or user ID, the attacker crafts requests designed to bypass intended restrictions, attempting to access account information they are not authorized to view.

3. **Unauthorized Account Access:**
   - Exploiting the broken Object Property Level Authorization, the attacker successfully retrieves account details beyond their authorized scope. This could include account balances, transaction histories, and other sensitive financial information.

4. **Potential Financial Exploitation:**
   - With unauthorized access to account details, the attacker may attempt further malicious actions such as initiating unauthorized transactions, account transfers, or other financial exploits.

5. **Covering Tracks:**
   - To evade detection, the attacker may modify or obfuscate the manipulated parameters, making it challenging to trace the unauthorized account access back to their actions.

**Mitigation:**
Implementing robust authorization checks at the Object Property Level, validating input parameters, and monitoring for unusual account access patterns are crucial steps to prevent unauthorized access in a banking API. Regular security assessments and code reviews can help identify and rectify vulnerabilities in the API's authorization mechanisms.


## How To Prevent Broken Object Property Level Authorization?

- When exposing an object using an API endpoint, always make sure that the user should have access to the object's properties you expose.

- Avoid using generic methods such as to_json() and to_string(). Instead, cherry-pick specific object properties you specifically want to return.

- If possible, avoid using functions that automatically bind a client's input into code variables, internal objects, or object properties ("Mass Assignment").

- Allow changes only to the object's properties that should be updated by the client.

- Implement a schema-based response validation mechanism as an extra layer of security. As part of this mechanism, define and enforce data returned by all API methods.

- Keep returned data structures to the bare minimum, according to the business/functional requirements for the endpoint.

## Conclusion
In the world of API security, fixing broken Object Property Level Authorization is crucial. By understanding real-world attacks and using strong security measures, we build a solid defense. Thorough checks and regular security checks are the keys to keeping our systems safe from unauthorized access and data issues. As we wrap up, let's stay committed to keeping our APIs secure and trustworthy.

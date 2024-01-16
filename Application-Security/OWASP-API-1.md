
## Table of Contents

- [Broken Object Level Authorization(BOLA)](#broken-object-level-authorizationbola)
  - [What is Object Level Authorization](#what-is-object-level-authorization)
    - [Impacts:](#impacts)
  - [Example Attack Scenarios](#example-attack-scenarios)
    - [Scenario 1: Unauthorized Fund Transfer in a Financial Application](#scenario-1-unauthorized-fund-transfer-in-a-financial-application)
    - [Scenario 2: Unauthorized Patient Record Access in a Healthcare System](#scenario-2-unauthorized-patient-record-access-in-a-healthcare-system)
    - [Scenario 3: Unauthorized Product Discounts in an E-commerce Platform](#scenario-3-unauthorized-product-discounts-in-an-e-commerce-platform)
  - [How To Prevent Broken Object Level Authorization(BOLA)?](#how-to-prevent-broken-object-level-authorizationbola)
  - [Conclusion](#conclusion)



# Broken Object Level Authorization(BOLA)
To grasp this security vulnerability, it's essential to delve into the concept of **Object Level Authorization** first.

## What is Object Level Authorization

Object level authorization is an access control mechanism that is usually implemented at the code level to validate that a user can only access the objects that they should have permissions to access.

Every API endpoint that receives an ID of an object, and performs any action on the object, should implement object-level authorization checks. The checks should validate that the logged-in user has permissions to perform the requested action on the requested object.

Failures in this mechanism typically lead to unauthorized information disclosure, modification, or destruction of all data. This is called **Broken Object Level Authorization**.

### Impacts:

1. **Unauthorized Access:**
   - **Risk:** Users may gain access to sensitive data or functionalities they are not supposed to access.
   - **Impact:** Breach of confidentiality, potential exposure of critical information.

2. **Data Manipulation:**
   - **Risk:** Malicious users might alter or delete data they are not authorized to modify.
   - **Impact:** Loss of data integrity, potential disruption of business processes.

3. **Elevation of Privileges:**
   - **Risk:** Exploitation of broken Object Level Authorization may lead to unauthorized elevation of user privileges.
   - **Impact:** Malicious users can perform actions reserved for higher-privileged roles, potentially causing significant damage.


## Example Attack Scenarios

### Scenario 1: Unauthorized Fund Transfer in a Financial Application

**Attack Details:**
In this scenario, an attacker exploits broken Object Level Authorization in a banking application to execute unauthorized fund transfers. By manipulating the authorization checks within the application, the attacker gains access to functionalities intended only for legitimate users. Leveraging technical vulnerabilities in the code logic governing transaction permissions, the attacker crafts requests that bypass intended restrictions.

The attack involves the following key steps:

1. **Identification of Weakness:**
   - The attacker identifies vulnerabilities in the Object Level Authorization mechanism of the banking application, allowing them to navigate through the code and find areas with insufficient access controls.

2. **Bypassing Security Controls:**
   - Through various techniques such as session hijacking, cookie manipulation, or exploiting flaws in authentication mechanisms, the attacker gains unauthorized access to the victim's account.

3. **Transaction Tampering:**
   - With access to the victim's account, the attacker manipulates the application's transaction authorization protocols. This involves crafting requests that mimic legitimate transactions but are intended to initiate fund transfers to the attacker's own or another external account.

4. **Execution of Unauthorized Transactions:**
   - The attacker successfully executes unauthorized fund transfers using the compromised account. This could involve exploiting vulnerabilities in the transaction processing logic, allowing them to override the intended restrictions and security checks.

5. **Covering Tracks:**
   - To avoid detection, the attacker may attempt to cover their tracks by modifying logs or manipulating transaction records. This ensures that their unauthorized activities go unnoticed for a more extended period.

**Mitigation:**
Implementing stringent access controls, robust session management, and multi-factor authentication are crucial in mitigating such attacks. Regular security audits and monitoring for anomalous transactions can help detect and prevent unauthorized fund transfers. Additionally, continuous code reviews and addressing vulnerabilities in the application's logic contribute to a more resilient security posture.


### Scenario 2: Unauthorized Patient Record Access in a Healthcare System

**Attack Details:**
Within a healthcare system plagued by Object Level Authorization issues, an attacker exploits vulnerabilities to gain unauthorized access to patient records. The attacker, aiming to compromise sensitive medical information, manipulates the application's access controls and authentication mechanisms.

The attack unfolds as follows:

1. **Identifying Access Control Weakness:**
   - The attacker identifies weaknesses in the Object Level Authorization mechanism, discovering areas where access controls are insufficiently enforced or improperly configured.

2. **Exploiting Authentication Flaws:**
   - Leveraging weak authentication mechanisms, the attacker gains initial access to the application. This could involve exploiting password vulnerabilities, session management issues, or other authentication-related weaknesses.

3. **Navigating to Patient Records:**
   - With the initial access, the attacker traverses the application's data objects or manipulates URLs meant to be restricted. They exploit direct object reference flaws, allowing them to access patient records they are not authorized to view.

4. **Potential Data Alteration :**
   - The attacker may not only view but also alter  sensitive medical information. This could lead to unauthorized modifications of patient records or the extraction of confidential data for malicious purposes.

5. **Concealing Unauthorized Access:**
   - To avoid detection, the attacker may attempt to cover their tracks by modifying logs or manipulating audit trails. This ensures their unauthorized access remains undetected for an extended period.

**Mitigation:**
Mitigating such attacks involves implementing robust access controls, encrypting sensitive data, and conducting regular security audits. Strengthening authentication protocols, monitoring for unusual access patterns, and promptly addressing identified vulnerabilities contribute to a more secure healthcare system.


### Scenario 3: Unauthorized Product Discounts in an E-commerce Platform

**Attack Details:**
In an e-commerce platform with Object Level Authorization vulnerabilities, an attacker aims to gain unauthorized control over administrative functionalities. By exploiting weaknesses in the application's access controls and authentication mechanisms, the attacker manipulates pricing-related functionalities to apply unauthorized product discounts.

The attack unfolds through the following steps:

1. **Identifying Administrative Weakness:**
   - The attacker identifies vulnerabilities in the Object Level Authorization mechanism, focusing on areas where administrative access controls are inadequately enforced or improperly configured.

2. **Exploiting Authentication and Session Management:**
   - Leveraging weaknesses in authentication methods or session management, the attacker gains unauthorized access to administrative functionalities. This could involve exploiting weak passwords, session hijacking, or other authentication-related flaws.

3. **Navigating to Pricing Controls:**
   - With access to administrative features, the attacker navigates to pricing-related functionalities. They exploit direct object reference flaws or manipulate URLs to access controls governing product prices and discounts.

4. **Applying Unauthorized Discounts:**
   - The attacker modifies pricing settings, applying unauthorized discounts to products. This could lead to financial losses for the e-commerce platform as customers exploit the discounted prices.

5. **Concealing Unauthorized Access:**
   - To avoid detection, the attacker may attempt to cover their tracks by modifying logs or manipulating audit trails. This ensures their unauthorized access remains undetected for an extended period.

**Mitigation:**
Mitigating such attacks involves implementing strong authentication protocols, robust access controls, and conducting regular security assessments. Monitoring for unusual administrative activities and promptly addressing identified vulnerabilities contribute to a more secure e-commerce platform.

## How To Prevent Broken Object Level Authorization(BOLA)?

1. Implement a proper authorization mechanism that relies on the user policies and hierarchy.

1. Use the authorization mechanism to check if the logged-in user has access to perform the requested action on the record in every function that uses an input from the client to access a record in the database.

1. Prefer the use of random and unpredictable values as GUIDs for records' IDs.

1. Write tests to evaluate the vulnerability of the authorization mechanism. Do not deploy changes that make the tests fail.

## Conclusion

Keeping an eye on Broken Object Level Authorization (BOLA) is key to stopping unauthorized access and data problems. Learning from real stories, using strong security like access controls is super important. Your watchful eye helps create a safer online space. Stay safe, and a big thank you for caring about online security!
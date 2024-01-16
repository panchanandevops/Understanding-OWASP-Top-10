
## Table of Contents

- [Broken Function Level Authorization](#broken-function-level-authorization)
  - [Function Level Authorization:](#function-level-authorization)
  - [How to spot Broken Function Level Authorization in an API?](#how-to-spot-broken-function-level-authorization-in-an-api)
  - [Example Attack Scenarios](#example-attack-scenarios)
    - [Scenario 1: Unauthorized Data Retrieval in a Healthcare API](#scenario-1-unauthorized-data-retrieval-in-a-healthcare-api)
    - [Scenario 2: Unauthorized Financial Transaction in Banking API](#scenario-2-unauthorized-financial-transaction-in-banking-api)
  - [How To Prevent Broken Function Level Authorization:](#how-to-prevent-broken-function-level-authorization)
  - [Conclusion](#conclusion)


# Broken Function Level Authorization
Let's start by grasping the concept of Function Level Authorization in the field of Information Technology.

## Function Level Authorization:

Function Level Authorization refers to the practice of controlling access to specific functions or operations within an application or system. Instead of granting blanket access, it ensures that users or entities can only perform authorized actions based on their assigned permissions. This fine-grained approach restricts users to specific functionalities, allowing for more precise control over who can execute particular tasks or access specific features within an application.


## How to spot Broken Function Level Authorization in an API?

The best way to find broken function level authorization issues is to perform a deep analysis of the authorization mechanism while keeping in mind the user hierarchy, different roles or groups in the application, and asking the following questions:

- Can a regular user access administrative endpoints?

- Can a user perform sensitive actions (e.g. creation, modification, or deletion ) that they should not have access to by simply changing the HTTP method (e.g. from `GET` to `DELETE`)?

- Can a user from group X access a function that should be exposed only to users from group Y, by simply guessing the endpoint URL and parameters (e.g. `/api/v1/users/export_all`)?

**Don't assume that an API endpoint is regular or administrative only based on the URL path.**

While developers might choose to expose most of the administrative endpoints under a specific relative path, like `/api/admins`, it's very common to find these administrative endpoints under other relative paths together with regular endpoints, like `/api/users`.


## Example Attack Scenarios

### Scenario 1: Unauthorized Data Retrieval in a Healthcare API

**Attack Details:**
In this scenario, an attacker exploits a Broken Function Level Authorization vulnerability in a healthcare API to gain unauthorized access to sensitive patient data. Identifying weaknesses in the function-level authorization controls, the attacker manipulates API requests to access patient records beyond their authorized scope.

The attack involves the following key steps:

1. **Identifying Weakness in Function-Level Authorization:**
   - The attacker identifies vulnerabilities in the API's function-level authorization controls, allowing them to discern areas with insufficient access restrictions.

2. **Manipulating API Requests:**
   - Exploiting the broken function-level authorization, the attacker crafts API requests to retrieve patient data. By manipulating parameters or endpoints, they aim to access records that are not within their authorized scope.

3. **Unauthorized Data Retrieval:**
   - The attacker successfully retrieves sensitive patient information by exploiting the broken function-level authorization. This could involve accessing medical records, diagnoses, or other confidential data beyond their legitimate permissions.

4. **Data Exfiltration or Modification:**
   - With unauthorized access to patient data, the attacker may choose to exfiltrate the information for malicious purposes or even modify records, introducing potential integrity issues.

5. **Covering Tracks:**
   - To evade detection, the attacker may attempt to cover their tracks by obfuscating their activities within the API logs or manipulating audit trails.

**Mitigation:**
Implementing robust function-level authorization controls, conducting regular security audits, and employing encryption for sensitive data can help prevent unauthorized data retrieval through API endpoints. Continuous monitoring of API activities and anomaly detection mechanisms enhance the overall security posture.


### Scenario 2: Unauthorized Financial Transaction in Banking API

**Attack Details:**
In this scenario, an attacker exploits the Broken Function Level Authorization vulnerability in a banking API to execute unauthorized financial transactions. Identifying weaknesses in the API's function-level authorization mechanisms, the attacker manipulates requests to access functionalities intended only for authenticated and authorized users. The attack unfolds as follows:

1. **Identification of Critical Endpoints:**
   - The attacker identifies API endpoints related to financial transactions that lack proper function-level authorization controls. This could involve analyzing the API documentation, examining network traffic, or using automated tools to discover potential vulnerabilities.

2. **Request Tampering:**
   - Leveraging the identified vulnerabilities, the attacker manipulates API requests to access and execute financial transactions on behalf of legitimate users. This may involve tampering with transaction parameters, modifying authentication tokens, or exploiting weaknesses in the authorization logic.

3. **Unauthorized Transaction Execution:**
   - With manipulated requests, the attacker successfully executes unauthorized financial transactions, transferring funds between accounts, initiating withdrawals, or performing other illicit activities.

4. **Monetary Gain:**
   - The attacker benefits financially from the unauthorized transactions, either by transferring funds to their accounts or conducting fraudulent activities that result in monetary gains.

5. **Concealing Activities:**
   - To evade detection, the attacker may attempt to conceal their activities by manipulating transaction logs or altering API response data. This helps in prolonging the unauthorized access without raising suspicion.

**Mitigation:**
Implementing stringent function-level authorization controls, employing multi-factor authentication for financial transactions, and regularly auditing API security are crucial to mitigate such attacks. Continuous monitoring for abnormal transaction patterns and implementing transaction verification mechanisms enhance the overall security of the banking API.

## How To Prevent Broken Function Level Authorization:

Your application should have a consistent and easy-to-analyze authorization module that is invoked from all your business functions. Frequently, such protection is provided by one or more components external to the application code.

- The enforcement mechanism(s) should deny all access by default, requiring explicit grants to specific roles for access to every function.

- Review your API endpoints against function level authorization flaws, while keeping in mind the business logic of the application and groups hierarchy.

- Make sure that all of your administrative controllers inherit from an administrative abstract controller that implements authorization checks based on the user's group/role.

- Make sure that administrative functions inside a regular controller implement authorization checks based on the user's group and role.


## Conclusion

Fixing Broken Function Level Authorization is key for strong API security. By implementing robust authorization controls, conducting regular security audits, and staying vigilant against unauthorized access attempts, organizations can fortify their APIs. Building a secure foundation at the function level is a fundamental step toward creating resilient and trustworthy APIs in the dynamic landscape of cybersecurity.

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Unrestricted Resource Consumption](#unrestricted-resource-consumption)
- [How to spot Unrestricted Resource Consumption Vulnerability  in an API?](#how-to-spot-unrestricted-resource-consumption-vulnerability--in-an-api)
- [Impact of Unrestricted Resource Consumption Vulnerability:](#impact-of-unrestricted-resource-consumption-vulnerability)
- [Example Attack Scenarios](#example-attack-scenarios)
  - [Scenario 1: DDoS Amplification Attack on an API](#scenario-1-ddos-amplification-attack-on-an-api)
  - [Scenario 2: Cryptocurrency Mining Through API Resource Exhaustion](#scenario-2-cryptocurrency-mining-through-api-resource-exhaustion)
- [How To Prevent Unrestricted Resource Consumption:](#how-to-prevent-unrestricted-resource-consumption)
- [Conclusion](#conclusion)



## Unrestricted Resource Consumption

Unrestricted Resource Consumption is an API vulnerability where an attacker exploits the lack of limitations on resource usage within an API, causing excessive consumption of resources such as CPU, memory, or network bandwidth. This vulnerability can lead to denial-of-service (DoS) attacks, impacting the availability and performance of the targeted system or service. Attackers may deliberately trigger resource-intensive operations, overwhelming the system and disrupting its normal functioning, thereby affecting legitimate users' access to the API.

## How to spot Unrestricted Resource Consumption Vulnerability  in an API?

An API is vulnerable if at least one of the following limits is missing or set inappropriately (e.g. too low/high):

- Execution timeouts

- Maximum allocable memory

- Maximum number of file descriptors

- Maximum number of processes

- Maximum upload file size

- Number of operations to perform in a single API client request (e.g. GraphQL batching)

- Number of records per page to return in a single request-response

- Third-party service providers' spending limit

## Impact of Unrestricted Resource Consumption Vulnerability:

1. **Denial of Service (DoS):**
   - Unrestricted Resource Consumption can make the API unresponsive for regular users, causing service outages.

2. **Impact on Other Services:**
   - Exploiting this flaw may not only disrupt the targeted API but also harm connected services, creating a ripple effect.

3. **Resource Exhaustion:**
   - Continuous exploitation drains critical resources like CPU and memory, leaving the system unable to handle valid requests.

4. **Loss of Customer Trust:**
   - Service disruptions and poor performance can erode customer trust, leading to a damaged reputation and potential customer loss.


## Example Attack Scenarios

### Scenario 1: DDoS Amplification Attack on an API

**Attack Details:**
In this scenario, an attacker exploits the Unrestricted Resource Consumption vulnerability in an API to launch a Distributed Denial of Service (DDoS) amplification attack, overwhelming the target system's resources.

The attack involves the following steps:

1. **Identification of Vulnerability:**
   - The attacker identifies an API with Unrestricted Resource Consumption vulnerability, allowing them to make requests that consume excessive resources without proper checks.

2. **Amplification Technique:**
   - The attacker leverages amplification techniques, such as abusing APIs that generate large responses for small requests or exploiting functionalities that trigger resource-intensive operations.

3. **Multiple Request Origination:**
   - Using botnets or multiple compromised systems, the attacker floods the target API with a massive volume of requests. Each request is designed to be small in size but triggers resource-intensive operations on the API server.

4. **Resource Saturation:**
   - As the target system processes the amplified requests, it exhausts its resources (CPU, memory, bandwidth), leading to a state of resource saturation. Legitimate users experience degraded service quality or complete unavailability.

5. **Impact and Intent:**
   - The DDoS amplification attack disrupts the availability of the API, causing service downtime for legitimate users. The intent may vary from financial gain through extortion to a form of protest or sabotage.

**Mitigation:**
Implementing rate limiting, traffic analysis, and utilizing DDoS mitigation tools can help detect and mitigate such attacks. Regularly monitoring API usage patterns and implementing proper resource throttling mechanisms can prevent Unrestricted Resource Consumption vulnerabilities from being exploited in this manner.

### Scenario 2: Cryptocurrency Mining Through API Resource Exhaustion

**Attack Details:**
In this scenario, an attacker exploits Unrestricted Resource Consumption in an API to perform cryptocurrency mining, utilizing the target system's resources for their gain. The attack unfolds as follows:

1. **Discovery of Vulnerable API:**
   - The attacker identifies an API with Unrestricted Resource Consumption, allowing them to make requests that trigger resource-intensive operations.

2. **Exploitation of Resource-Intensive Operations:**
   - Leveraging the vulnerability, the attacker crafts requests that initiate computationally expensive operations, exploiting features or functionalities that are not adequately restricted.

3. **Mining Payload Injection:**
   - The attacker injects cryptocurrency mining payloads into the API requests, causing the server to execute resource-intensive mining algorithms in addition to the legitimate operations.

4. **Botnet Utilization:**
   - To scale the attack, the attacker deploys a botnet to send a large volume of requests to the vulnerable API, amplifying the resource consumption and increasing the mining operations' effectiveness.

5. **Resource Drain and Cryptocurrency Gain:**
   - As the API server processes the requests, it expends excessive resources on both legitimate and mining operations. The attacker benefits from the mined cryptocurrency, leveraging the compromised infrastructure.

6. **Impact and Intent:**
   - The attack impacts the performance of the API server, potentially causing service disruptions for legitimate users. The attacker's intent is to gain financial profit through illicit cryptocurrency mining at the expense of the target's resources.

**Mitigation:**
Implementing proper input validation, rate limiting, and monitoring for anomalous API usage patterns can help detect and prevent Unrestricted Resource Consumption vulnerabilities. Regular security audits, code reviews, and the use of intrusion detection systems can enhance the overall security posture of the API.

## How To Prevent Unrestricted Resource Consumption:

- Use a solution that makes it easy to limit memory, CPU, number of restarts, file descriptors, and processes such as Containers / Serverless code (e.g. Lambdas).

- Define and enforce a maximum size of data on all incoming parameters and payloads, such as maximum length for strings, maximum number of elements in arrays, and maximum upload file size (regardless of whether it is stored locally or in cloud storage).

- Implement a limit on how often a client can interact with the API within a defined timeframe (rate limiting).

- Rate limiting should be fine tuned based on the business needs. Some API Endpoints might require stricter policies.

- Limit/throttle how many times or how often a single API client/user can execute a single operation (e.g. validate an OTP, or request password recovery without visiting the one-time URL).

- Add proper server-side validation for query string and request body parameters, specifically the one that controls the number of records to be returned in the response.

- Configure spending limits for all service providers/API integrations. When setting spending limits is not possible, billing alerts should be configured instead.

## Conclusion
In a digital landscape increasingly reliant on APIs, the Unrestricted Resource Consumption vulnerability emerges as a potent threat. This susceptibility can lead to disruptive attacks, impacting service availability and user trust. Mitigation strategies, including proper limits, rate controls, and vigilant security practices, are essential to fortify APIs against exploitation. By adopting these measures, organizations can uphold the integrity of their APIs, thwart potential attacks, and ensure a secure digital experience for users.
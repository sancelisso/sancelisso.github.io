---
layout: post
title: OWASP Smart Contract Top 10
date: 2025-01-21 08:25 +0000
categories: release
tags:
- blockchain
- smart contract
- cybersecurity 
---
The Open Web Application Security Project (OWASP) has recently released its Smart Contract Top 10 for 2025, a standard awareness document providing Web3 developers and security teams with insights into the top 10 vulnerabilities found in smart contracts.

## Quick Intro to OWASP

**OWASP** is stand for **Open Web Application Security Project**. It is a foundation that works to improve the security of software through its community-led open source software projects, hundreds of chapters worldwide, tens of thousands of members, and by hosting local and global conferences.**

## The Smart Contract top 10

The **Smart Contract Top 10** is a security-focused framework that identifies the most critical vulnerabilities and risks associated with smart contracts.

The Smart Contract Top 10 acts as a guide to ensure that smart contracts are protected against the most significant vulnerabilities exploited or identified in recent years.  The Smart Contract Top 10 can be paired with other security initiatives for smart contracts to achieve comprehensive risk mitigation. 

It is worth mentionning that the most recent publication of this Top 10 was released two years ago.

## What changes are made for this new release ?

![Mapping2023-2025.png](assets/img/Mapping2023-2025.png)

From the picture above you can notice there are some weaknesses have been removed, while others have been added and some have been moved up or moved down.

# The TOP 10

For the new release, the top 10 is elaborated like below:


**SC01 - Access Control Vulnerabilities**: Access control flaws allow unauthorized users to access or modify a contract’s data or functions. These vulnerabilities arise when the code fails to enforce proper permission checks, potentially leading to severe security breaches.

**SC02 - Price Oracle Manipulation**: Price Oracle Manipulation exploits vulnerabilities in how smart contracts fetch external data. By tampering with or controlling oracle feeds, attackers can affect contract logic, leading to financial losses or system instability.

**SC03 - Logic Errors**: Logic errors, or business logic vulnerabilities, occur when a contract’s behavior deviates from its intended functionality. Examples include incorrect reward distribution, token minting issues, or flawed lending/borrowing logic.

**SC04 - Lack of Input Validation**: Insufficient input validation can lead to vulnerabilities where an attacker may manipulate the contract by providing harmful or unexpected inputs, potentially breaking logic or causing unexpected behaviors.

**SC05 - Reentrancy Attacks**: Reentrancy attacks exploit the ability to reenter a vulnerable function before its execution is complete. This can lead to repeated state changes, often resulting in drained contract funds or broken logic.

**SC06 - Unchecked External Calls**: Failing to verify the success of external function calls can result in unintended consequences. When a called contract fails, the calling contract may incorrectly proceed, risking integrity and functionality.

**SC07 - Flash Loan Attacks**: Flash loans, while useful, can be exploited to manipulate protocols by executing multiple actions in a single transaction. These attacks often result in drained liquidity, altered prices, or exploited business logic.

**SC08 - Integer Overflow and Underflow**: Arithmetic errors due to exceeding the limits of fixed-size integers can lead to serious vulnerabilities, such as incorrect calculations or token theft. Unsigned integers wrap around on underflow, while signed integers flip between extremes.

**SC09 - Insecure Randomness**: Due to the deterministic nature of blockchain networks, generating secure randomness is challenging. Predictable or manipulable randomness can lead to exploitation in lotteries, token distributions, or other randomness-dependent functionalities.

**SC10 - Denial of Service (DoS) Attacks**: DoS attacks exploit vulnerabilities to exhaust contract resources, rendering it non-functional. Examples include excessive gas consumption in loops or function calls designed to disrupt normal contract operation.

## Some Key highlights from Web3HackHub for 2024 include:

- Total Financial Impact: $1.42 billion lost across 149 documented incidents in 2024.
- Top Attack Vectors (by frequency, total losses):
    - Access Control Vulnerabilities: $953.2M in losses.
    - Logic Errors: $63.8M in losses.
    - Reentrancy Attacks: $35.7M in losses.
    - Flash Loan Attacks: $33.8M in losses.
    - Lack of Input Validation: $14.6M in losses.
    - Price Oracle Manipulation: $8.8M in losses.
    - Unchecked External Calls: $550.7K in losses.

# Thoughts

In light of the rapid expansion of WEB3 technologies, this Top 10 must be considered with the utmost diligence. It will be of significant value to the key players within this ecosystem.

- **Smart contract developers**: It serves as a crucial tool, enabling developers to recognize potential vulnerabilities and proactively mitigate them during the coding process.
- **Bug Hunters**: This Top 10 provides an invaluable guide for bug hunters seeking to identify vulnerabilities in smart contract projects, facilitating more effective and targeted security assessments.
- **Blockchain Projects and Organizations**: For companies and organizations leveraging blockchain technology, the Top 10 serves as a baseline to assess the overall security posture of their smart contract infrastructure. It assists in prioritizing security investments and developing comprehensive risk mitigation strategies.
- **Security Auditors**: For auditors, the Top 10 offers a structured framework to evaluate and ensure that smart contracts adhere to industry best practices. It can guide the auditing process, helping identify critical weaknesses that could lead to exploitation or financial loss.

In summary, the Smart Contract Top 10 is not just a tool for identifying vulnerabilities; it is an essential resource for building a culture of security and fostering trust in the Web3 space.

# Useful links

- [https://owasp.org/www-project-smart-contract-top-10/](https://owasp.org/www-project-smart-contract-top-10/)

- [https://cybersecuritynews.com/owasp-top-10-2025-smart-contract/](https://cybersecuritynews.com/owasp-top-10-2025-smart-contract/)






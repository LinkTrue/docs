---
description: System Security Implications.
icon: book-open
cover: >-
  https://images.unsplash.com/photo-1637190623651-e6b10007a0b7?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwxMHx8ZGlhZ3JhbXxlbnwwfHx8fDE3NDE3ODg1MzN8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Overview

## Thread Model

<figure><img src="../.gitbook/assets/dtip flow.png" alt=""><figcaption><p>system diagram</p></figcaption></figure>

### Principals (Actors)

Key actors in the system that can be targeted by threats:

* Users:
  * Create a profile with their data
  * View a specific profile
* **Official Website** (Vercel): Frontend interface for interacting with the smart contract
* **Smart Contract**: Stores profile data and enforces rules for modification
* **Blockchain Network (Ethereum L1 & Soneium L2)**: Processes transactions and stores profile data
* **Website Hosting Provider (Vercel)**: Delivers the frontend; potential attack vector

### Goals (Security Properties)

* **Profile Data Security**
  * Only the owner can modify their profile&#x20;
  * Prevent unauthorized modifications (e.g., smart contract exploits)
* **Profile Data Availability**
  * Users should always be able to retrieve profile data, even if the website is down
  * Alternative access: Directly from blockchain explorer ([Soneium Blockscout](https://soneium-minato.blockscout.com/address/0xB5500E2C3B09Eb7cfb19437BF88f3b3fe739C3b6?tab=read_contract))
* **Data Authenticity & Verification**
  * Users should be able to verify profile data integrity from the blockchain
  * Verified smart contract ensures authenticity
* **Ease of Use**
  * While blockchain verification is possible, most users prefer using the website; maintaining website availability is critical

### Adversities (Threats)

**a) In Our Control (Can Be Mitigated)**

* **Website Downtime (Vercel Issues)**
  * Mitigation: Users can access data from [Soneium Blockscout](https://soneium-minato.blockscout.com/address/0xB5500E2C3B09Eb7cfb19437BF88f3b3fe739C3b6?tab=read_contract)
* **Phishing Attacks (Fake&#x20;**_**dTip**_**&#x20;Websites)**
  * Attackers can clone the website and trick users into interacting with a malicious contract
  * Mitigation:
    * Clear branding and verified domains
      * Encourage users to verify contract addresses before interacting
* **Smart Contract Exploits**
  * Unauthorized profile modification due to coding flaws
  * Possible attack vectors: access control issues, storage manipulation
  * Mitigation:
    * White-box Security audits with industry best practices and extensive testing

**b) Out of Our Control (But Can Affect&#x20;**_**dTip**_**'s Integrity)**

These are external factors that impact _dTip_ but are not directly under our control:

* **Blockchain Congestion (Ethereum L1 & Soneium L2)**
  * Transaction delays could impact profile updates
  * No direct mitigation, but users can wait for network conditions to improve
* **L2 Security Risks (Soneium OP Stack)**
  * If Soneium experiences a security breach, profile data integrity may be affected
  * Mitigation: Monitor network health and provide fallback options (e.g., consider alternative rollups if Soneium becomes unstable)
* **Blockchain Censorship or Validator Attacks**
  * Validators could censor transactions, preventing profile updates
  * While unlikely, this is outside _dTip_’s control

### Invariants (System Integrity Must-Holds)

To ensure _dTip_ remains functional and secure:

*   **Profile Data Must Always Be Accessible**

    * Even if the website is down, users should access data via blockchain explorersComment

    CommentComment
*   **Smart Contract Should Always Enforce Profile Ownership**

    * Unauthorized edits should never be possibleComment

    CommentComment
*   **Blockchain Networks Must Be Operational**

    * Ethereum L1 & Soneium L2 must be running for _dTip_ to workComment

    CommentComment
* **Users Must Always Have an easy Way to Verify Profile Authenticity**
  * Either through the official website or directly via the blockchain explorer

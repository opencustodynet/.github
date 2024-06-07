# OpenCustody

## Goal

The goal of OpenCustody is to provide the highest level of security for cryptocurrency custody through an open-source solution.

## Project Overview

One of the main obstacles to broader cryptocurrency adoption is wallet and key management, which can be challenging for average users. Key management in crypto falls into two categories: self-custody and custodial services. While self-custody aligns with the philosophy of blockchain, self-sovereignty, and distributed systems, most users prefer not to self-custody due to the significant responsibility it entails. Instead, they rely on custodial services like exchanges and Wallet-as-a-Service (WaaS) providers.

These custodial services typically use closed-source software, which means users must trust the service provider's implementation. Since it is not open source, independent researchers, white-hat hackers, cryptographers, and other experts cannot review it for potential flaws. Crypto users deserve a better solution—one that offers top-tier security architecture and a robust trust model, all within an open-source framework. OpenCustody is that solution.

OpenCustody is a secure open-source custody solution designed for exchanges, crypto banks, and any crypto project requiring custody. It leverages Hardware Security Modules (HSM), dedicated cryptographic hardware devices well-established in securing digital and online banking, payment networks (like VISA and MasterCard), network security (PKI and TLS/SSL), and government and military applications. HSMs feature True Random Number Generators (TRNG), secure tamper-resistant key storage, and cryptographic engines. They often hold security certifications like FIPS 140 and Common Criteria.
In OpenCustody, HSMs are central to generating keys, signing transactions, and other secure operations. Keys are generated inside the HSM using TRNG and never leave the HSM in plain form. Even backup procedures are encrypted end-to-end between HSMs.

OpenCustody also employs a concept known as the “approval module,” which is used to get user approval on transactions or actions, such as transferring funds. It displays messages received from the HSM to the user, who then confirms the action. The approval module can be a web app, mobile app, or hardware wallet, with the hardware wallet being the most secure option.

## Trust Model

OpenCustody’s trust model is designed to minimize trust outside of the HSM. Only the HSM and the approval module are trusted, while other components like middle programs, clients, servers, and networks are considered untrusted. This model ensures that key materials reside inside the HSM and never leave in plain form. This approach contrasts with the current trust models used by many exchanges, where key materials are stored on servers and clouds.

![OpenCustody Logo](https://raw.githubusercontent.com/opencustodynet/.github/main/profile/OpenCustody_Trust_Model.png)

Some custodial service providers use Intel SGX on servers and clouds for key material computation, but SGX, designed as an Intel extension for its processors for Trusted Execution Environments (TEE), has known vulnerabilities and is not suited for securing millions or billions of dollars. In contrast, OpenCustody uses HSMs, which are specifically designed for secure cryptographic operations and large-scale security.

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->

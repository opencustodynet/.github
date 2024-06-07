# OpenCustody

The goal of OpenCustody is to provide the highest level of security for cryptocurrency custody through an open-source solution.

## Introduction

One of the main obstacles to broader cryptocurrency adoption is wallet and key management, which can be challenging for average users. Key management in crypto falls into two categories: self-custody and custodial services. While self-custody aligns with the philosophy of blockchain, self-sovereignty, and distributed systems, most users prefer not to self-custody due to the significant responsibility it entails. Instead, they rely on custodial services like exchanges and Wallet-as-a-Service (WaaS) providers.

These custodial services typically use closed-source software, which means users must trust the service provider's implementation. Since it is not open source, independent researchers, white-hat hackers, cryptographers, and other experts cannot review it for potential flaws. Crypto users deserve a better solution—one that offers top-tier security architecture and a robust trust model, all within an open-source framework. OpenCustody is that solution.

OpenCustody is a secure open-source custody solution designed for exchanges, crypto banks, and any crypto project requiring custody. It leverages Hardware Security Modules (HSM), dedicated cryptographic hardware devices well-established in securing digital and online banking, payment networks (like VISA and MasterCard), network security (PKI and TLS/SSL), and government and military applications. HSMs feature True Random Number Generators (TRNG), secure tamper-resistant key storage, and cryptographic engines. They often hold security certifications like FIPS 140 and Common Criteria.
In OpenCustody, HSMs are central to generating keys, signing transactions, and other secure operations. Keys are generated inside the HSM using TRNG and never leave the HSM in plain form. Even backup procedures are encrypted end-to-end between HSMs.

OpenCustody also employs a concept known as the “approval module,” which is used to get user approval on transactions or actions, such as transferring funds. It displays messages received from the HSM to the user, who then confirms the action. The approval module can be a web app, mobile app, or hardware wallet, with the hardware wallet being the most secure option.

OpenCustody primarily uses Rust due to its security-by-design approach, which helps prevent buffer overflows and other memory-related bugs. Rust was chosen as the ideal language for developing such a secure system. However, many embedded systems, including Hardware Security Modules (HSMs), only support C/C++. To bridge this gap, OpenCustody utilizes the HSM's C SDK within Rust. The Rust code is compiled into a static library, which is then linked to a C library. This approach, employed in `opencustody-vault`, allows for the development of HSM firmware code in Rust 👌, leveraging the language's robust security features.

## Trust Model

OpenCustody’s trust model is designed to minimize trust outside of the HSM. Only the HSM and the approval module are trusted, while other components like middle programs, clients, servers, and networks are considered untrusted. This model ensures that key materials reside inside the HSM and never leave in plain form. This approach contrasts with the current trust models used by many exchanges, where key materials are stored on servers and clouds.

![OpenCustody Logo](https://raw.githubusercontent.com/opencustodynet/.github/main/profile/OpenCustody_Trust_Model.png)

Some custodial service providers use Intel SGX on servers and clouds for key material computation, but SGX, designed as an Intel extension for its processors for Trusted Execution Environments (TEE), has known vulnerabilities and is not suited for securing millions or billions of dollars. In contrast, OpenCustody uses HSMs, which are specifically designed for secure cryptographic operations and large-scale security.

## Supported HSMs

OpenCustody can technically support any HSM that provides the required cryptographic primitives (e.g., ECDSA and EDDSA) since it employs the PKCS#11 interface. For development and testing, OpenCustody supports SoftHSM and officially supports the [Thales Luna HSM](https://cpl.thalesgroup.com/encryption/hardware-security-modules/network-hsms). OpenCustody can be configured to work with an HSM or built as firmware for an HSM, ensuring the highest level of security by performing all key and sensitive operations inside the HSM.

These are supported Luna HSM models:
| HSM                 | Description                                                | Performance          |
|---------------------|------------------------------------------------------------|----------------------|
| Luna PCIe HSM A700| Embedded HSM Password-Authentication with 4 MB key space     | ECC P256: 2,000 tps  |
| Luna PCIe HSM A750| Embedded HSM Password-Authentication with 32 MB key space    | ECC P256: 10,000 tps |
| Luna PCIe HSM A790| Embedded HSM Password-Authentication with 64 MB key space    | ECC P256: 22,000 tps |
| Luna PCIe HSM S700| Embedded HSM PED-Authentication with 4 MB key space          | ECC P256: 2,000 tps  |
| Luna PCIe HSM S750| Embedded HSM PED-Authentication with 32 MB key space         | ECC P256: 10,000 tps |
| Luna PCIe HSM S790| Embedded HSM PED-Authentication with 64 MB key space         | ECC P256: 22,000 tps |
| Luna Network HSM A700| Network HSM Password-Authentication with 4 MB key space  | ECC P256: 2,000 tps  |
| Luna Network HSM A750| Network HSM Password-Authentication with 32 MB key space | ECC P256: 10,000 tps |
| Luna Network HSM A790| Network HSM Password-Authentication with 64 MB key space | ECC P256: 22,000 tps |
| Luna Network HSM S700| Network HSM PED-Authentication with 4 MB key space       | ECC P256: 2,000 tps  |
| Luna Network HSM S750| Network HSM PED-Authentication with 32 MB key space      | ECC P256: 10,000 tps |
| Luna Network HSM S790| Network HSM PED-Authentication with 64 MB key space      | ECC P256: 22,000 tps |

## How to Contribute

1. Clone a repo like `opencustody-vault` and create a new branch:
```bash
$ git checkout https://github.com/opencustodynet/opencustody-vault.git -b name_for_new_branch
```
2. Make changes and test
3. Submit Pull Request with comprehensive description of changes

The most important part to contribute is adding more assets to `opencustody-vault`. 👩‍💻

## License
OpenCustody is licensed under [GPL-3.0 License](https://github.com/opencustodynet/opencustody-vault/blob/main/LICENSE), and you can use it to provide Software-as-a-Service like for an exchange. However, for support and additional information, please contact _hossein[at]cyrussec[dot]com_.

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->

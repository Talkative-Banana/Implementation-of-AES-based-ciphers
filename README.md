<!-- PROJECT LOGO --> <br /> <p align="center"> <a> <img src="https://github.com/user-attachments/assets/ad44efa3-8019-4104-b0e6-be60701f5072" alt="Logo"> </a>

# Cryptographic Ciphers: Rocca and SNOW-V

This project demonstrates the implementation and analysis of two advanced cryptographic ciphers: **Rocca** and **SNOW-V**. Both algorithms are designed to meet modern cryptographic needs with a focus on speed, security, and resource efficiency.

---

## Table of Contents
- [Introduction](#introduction)
- [Rocca Cipher](#rocca-cipher)
  - [Overview](#overview)
  - [Algorithm Components](#algorithm-components)
  - [Encryption Process](#encryption-process)
  - [Performance Analysis](#performance-analysis)
- [SNOW-V Cipher](#snow-v-cipher)
  - [Design Overview](#design-overview)
  - [Initialization and Key Scheduling](#initialization-and-key-scheduling)
  - [Keystream Generation](#keystream-generation)
  - [Performance Analysis](#performance-analysis-1)
- [Security Analysis](#security-analysis)
- [Usage](#usage)
- [Contributors](#contributors)
- [License](#license)

---

## Introduction
Cryptographic ciphers are essential for securing data in modern communication systems. This project implements two state-of-the-art algorithms:
1. **Rocca**: Optimized for encryption speeds exceeding 100 Gbps, suitable for 6G systems.
2. **SNOW-V**: Designed for 5G/6G systems, leveraging SIMD instructions for high-performance stream encryption.

---

## Rocca Cipher

### Overview
Rocca is an authenticated encryption algorithm designed for high-speed encryption in resource-constrained environments. It combines encryption and authentication to ensure data integrity and confidentiality.

### Algorithm Components
- **Keys**: Two 128-bit keys (`k1` and `k2`) concatenated to form a 256-bit key.
- **Nonce**: A 128-bit value to prevent replay attacks.
- **Associated Data (AD)**: Metadata for authentication.
- **Plaintext**: The data to be encrypted.
- **State**: A vector of eight 32-byte keys initialized using keys, nonce, and constants.

### Encryption Process
1. **Initialization**: The state is set using the keys, nonce, and constants.
2. **Padding**: Plaintext and associated data are padded to 256-bit blocks.
3. **Encryption**: Plaintext is encrypted in 32-byte blocks while updating the state for each block.
4. **Tag Generation**: A tag is derived from the final state for authentication.

### Performance Analysis
The following table summarizes the encryption speed for different plaintext sizes:

| Plaintext Size (bits) | Encryption Speed (Mbps) |
|------------------------|-------------------------|
| 81920                 | 61.98                  |
| 8192                  | 65.55                  |
| 1024                  | 37.81                  |
| 256                   | 16.63                  |
| 64                    | 4.45                   |

---

## SNOW-V Cipher

### Design Overview
SNOW-V is an advanced stream cipher that uses:
- **Linear Feedback Shift Registers (LFSRs)**: Two 16-cell LFSRs (LFSR-A and LFSR-B).
- **Finite State Machine (FSM)**: Three 128-bit registers updated using AES encryption rounds.

### Initialization and Key Scheduling
- Accepts a 256-bit key and a 128-bit initialization vector (IV).
- Mixes the key and IV into the LFSRs, enhancing security against brute-force attacks.

### Keystream Generation
- Generates 128 bits of keystream per cycle.
- Designed for high-throughput applications, particularly in mobile systems.

### Performance Analysis
The following table summarizes the encryption speed for different plaintext sizes:

| Plaintext Size (bits) | Encryption Speed (Mbps) |
|------------------------|-------------------------|
| 81920                 | 49.18                  |
| 8192                  | 54.65                  |
| 1024                  | 52.71                  |
| 256                   | 52.67                  |
| 64                    | 35.37                  |

---

## Security Analysis
Both Rocca and SNOW-V ensure robust security against modern cryptographic attacks:
- **Rocca**: Combines AES transformations and XOR operations to resist linear and differential cryptanalysis.
- **SNOW-V**: Leverages AES-based FSM updates and LFSR operations for enhanced security in high-throughput environments.

---

## Usage

### Prerequisites
- Python 3.7 or higher.
- Required libraries: `time`.

## Contributors
- Talkative-Banana lakshay21059@iiitd.ac.in
- Ekansh ekansh21044@iiitd.ac.in
- Sahil sahil21281@iiitd.ac.in

## License
This project is licensed under the MIT License. See the LICENSE file for details.

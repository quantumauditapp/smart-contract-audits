---
token: SpaceX xStock
ticker: SPCXX
network: ethereum
risk_score: 100
status: critical
date: 2026-06-16
---

# SpaceX xStock (SPCXX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-xstock-eth)

---

## Audit Summary

The audit of the Backed Auto Fee Token project reveals a critical concern: the implementation contract's source code is not publicly verified. This significantly hinders the ability to assess the core business logic and introduces substantial trust requirements. While the project utilizes a standard OpenZeppelin Transparent Proxy pattern with a multisig admin, the lack of transparency for the underlying token logic poses a severe risk to users.

> **Final Recommendation:** The paramount recommendation is to immediately verify the source code of the `BackedAutoFeeTokenImplementation` contract on Etherscan or a similar block explorer. This is crucial for transparency, user trust, and enabling proper security analysis. Additionally, consider implementing a timelock mechanism for all critical administrative operations, especially contract upgrades, to provide a delay period for community review and reaction. Ensure that all future implementation upgrades also have their source code publicly verified.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture leverages OpenZeppelin's upgradeable contracts (ERC20Upgradeable, OwnableUpgradeable, Initializable), which are well-audited and robust (7.1 Architecture). However, the… |
| **Governance / Economics** | 1/10 | High | The proxy administration is secured by a 2-of-3 Gnosis Safe multisig, which is a strong access control mechanism for upgrades (7.3 Access Control). However, the economic parameters and core… |
| **Upgrades** | 1/10 | High | The contract utilizes the EIP-1967 Transparent Proxy pattern with an OpenZeppelin ProxyAdmin, which is a standard and well-understood upgrade mechanism (7.7 Upgrades). The proxy admin is controlled… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-3 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | ⚠️ 1 |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 83.1% |
| **Top-3 Unlocked** | ⚠️ 97.3% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Unverified Implementation Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The source code for the `BackedAutoFeeTokenImplementation` contract (0x65c40d624af3b18c109fbf87b7deff34cdc5f19b), which contains the core logic of the token, is not publicly verified on the blockchain explorer. This means that users, auditors, and the community cannot independently verify what code is actually running on-chain, making it impossible to assess its security, functionality, or adherence to stated specifications. This introduces a fundamental trust issue and prevents any meaningful security analysis of the token's behavior (7.2 Code Security).

**Recommendation:** Immediately verify the source code of the `BackedAutoFeeTokenImplementation` contract on Etherscan (or the relevant block explorer). This is a critical step for transparency and establishing trust with users. Ensure that the verified code matches the deployed bytecode exactly.


### `H-01` — Lack of Transparency for Core Token Logic and Economic Parameters  *(Severity: High · Status: Unresolved)*

Due to the unverified implementation source code (C-01), the specific functionalities of the 'Auto Fee Token' (e.g., how fees are calculated, collected, and distributed; minting/burning capabilities; pausing mechanisms; blacklisting features) remain entirely opaque. This lack of transparency extends to critical economic parameters that could significantly impact token holders (7.4 Economic). Without visibility into the code, there is no way to confirm that the token operates as expected or that it doesn't contain hidden backdoors or malicious logic (7.5 Governance).

**Recommendation:** Beyond verifying the source code, provide comprehensive documentation detailing the token's economic model, fee mechanisms, and all administrative functionalities. Clearly outline the roles and permissions of any privileged addresses within the token contract. Regular audits of the verified code should be conducted and published.


### `M-01` — Potential Centralized Control over Token Functionality  *(Severity: Medium · Status: Unresolved)*

While the proxy admin is controlled by a multisig, the `BackedAutoFeeTokenImplementation` contract likely inherits `OwnableUpgradeable` (as indicated by the provided snippets). Without the implementation source, it is unknown whether the owner of the token's core functionalities (e.g., minting, burning, pausing, modifying fee parameters) is a single EOA, a multisig, or a timelock-controlled address (7.3 Access Control). If controlled by a single EOA, it presents a single point of failure and a significant centralization risk for critical token operations (7.8 Operations).

**Recommendation:** If the token's core functionalities are controlled by a single EOA, consider migrating ownership to a robust multisig wallet or a timelock-controlled address. Clearly document all privileged roles and their associated addresses, along with the rationale for their access levels.


### `L-01` — Absence of Timelock for Proxy Upgrades  *(Severity: Low · Status: Unresolved)*

The proxy upgrade mechanism, while controlled by a 2-of-3 Gnosis Safe multisig, does not incorporate a timelock (7.7 Upgrades). This means that once the required multisig confirmations are met, an upgrade can be executed immediately. While a multisig provides a layer of security by requiring multiple approvals, a timelock would introduce a mandatory delay, allowing users and external monitors to review proposed changes and react if a malicious or erroneous upgrade is initiated.

**Recommendation:** Consider integrating a timelock mechanism into the upgrade process. This would involve the multisig proposing an upgrade, which then enters a predefined delay period before it can be executed. This provides an additional safety net for users and the protocol.


### `I-01` — Utilization of Standard OpenZeppelin Upgradeable Libraries  *(Severity: Informational · Status: Unresolved)*

The project leverages well-audited and widely adopted OpenZeppelin Contracts Upgradeable libraries, including `ERC20Upgradeable`, `OwnableUpgradeable`, and `Initializable`. This foundation provides a strong baseline for security and adherence to established standards for upgradeable contracts and token implementations (7.1 Architecture, 7.2 Code Security). The use of these battle-tested components reduces the risk of common vulnerabilities inherent in custom implementations of these primitives.

**Recommendation:** Continue to rely on reputable and audited libraries for core functionalities. Ensure that all OpenZeppelin components are used correctly, especially regarding initialization patterns in upgradeable contracts, to avoid common proxy-related pitfalls.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x68fa...ce28`](https://etherscan.io/address/0x68fa48b1c2fe52b3d776e1953e0e782b5044ce28) |
| **Network** | Ethereum |
| **Price** | $116.9700 |
| **24h Volume** | $1.9K |
| **Liquidity** | $26.5K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3d |
| **Top-10 Holders** | 99.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 124 buys / 142 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Frequently Asked Questions

### Is SpaceX xStock a scam?

Labeling SpaceX xStock as an outright scam based solely on provided data is not definitive. While the contract is verified and ownership renounced, significantly concerning factors exist. 99.9% of the supply is controlled by the top 10 holders, indicating extreme centralization, and liquidity is not locked. These characteristics create a high potential for price manipulation or a liquidity pull. The assigned risk score of 60/100 reflects these considerable dangers, urging extreme vigilance from investors.

### Is SpaceX xStock safe to buy?

SpaceX xStock (SPCXX) carries significant risks and is not considered safe to buy based on current metrics. A critical concern is that 99.9% of the token supply is concentrated within the top 10 holders, making it highly susceptible to manipulation. Furthermore, the absence of locked liquidity means that the existing funds can be withdrawn at any time, posing a direct rug pull risk. Its overall risk score of 60/100 strongly indicates a hazardous investment profile.

### Has SpaceX xStock been audited?

The SpaceX xStock (SPCXX) smart contract is verified, making its code public and reviewable for transparency. However, 'contract verified' differs from a comprehensive security audit conducted by an independent firm. An audit involves a deeper, expert analysis to proactively identify vulnerabilities. The provided data does not confirm that such a formal audit has been performed for SPCXX.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xba8e6701ead6b06a57fc83094b0b2d25fb504d6394f6b13a17de583d50c1ebc0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-xstock-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-16*

---
token: SomniaOFT
ticker: SOMI
network: bsc
risk_score: 42
status: medium
date: 2026-09-01
---

# SomniaOFT (SOMI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/somniaoft-bsc)

---

## Audit Summary

The SomniaOFT contract implements an Omnichain Fungible Token (OFT) utilizing LayerZero V2 technology and OpenZeppelin's Ownable access control. The contract itself is minimal, primarily inheriting and delegating functionality to the well-audited LayerZero OFT library. The primary security considerations revolve around the centralized control exercised by the owner multisig over critical LayerZero configurations, the inherent reliance on external LayerZero infrastructure, and the operational complexities associated with managing cross-chain parameters. The use of a 3/5 multisig for ownership is a strong security practice that mitigates some centralization risks.

> **Final Recommendation:** Ensure the multisig controlling the SomniaOFT contract is robustly secured, with strong operational procedures for key management and transaction signing. Regularly review and audit all LayerZero configurations, especially `trustedRemote` and message library settings, to prevent misconfigurations that could lead to funds being stuck or cross-chain transactions failing. Establish comprehensive monitoring for LayerZero endpoint health and transaction statuses to quickly identify and respond to any issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The SomniaOFT contract (7.1 Architecture) is a straightforward implementation, inheriting from the battle-tested OpenZeppelin Ownable and LayerZero OFT contracts. This approach leverages well-audited… |
| **Governance / Economics** | 1/10 | High | The contract's administrative functions are protected by OpenZeppelin's Ownable pattern, with ownership assigned to a 3/5 multisig address (7.3 Access Control). This distributed control significantly… |
| **Upgrades** | 7/10 | Low | The SomniaOFT contract is not designed as an upgradeable proxy (7.7 Upgrades). Its functionality is fixed upon deployment, meaning there are no direct upgrade safety concerns for this specific… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 58.5% |
| **Top-3 Unlocked** | ⚠️ 99.1% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low_

### `M-01` — Reliance on External LayerZero Infrastructure  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The core cross-chain functionality of the SomniaOFT token is entirely dependent on the security, availability, and correct operation of the LayerZero endpoint and its associated message libraries (7.6 External). Any vulnerability, outage, or malicious activity within the LayerZero network or its specific endpoint implementations could directly impact the ability to transfer SomniaOFT tokens across chains, potentially leading to asset loss or service disruption.

**Recommendation:** Acknowledge and monitor the inherent risks associated with relying on external bridge infrastructure. Implement robust monitoring for LayerZero endpoint health, transaction finality, and any security announcements from LayerZero. Develop contingency plans for scenarios involving LayerZero outages or security incidents, such as pausing cross-chain transfers if necessary.


### `M-02` — Operational Risk from LayerZero Configuration Errors  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The owner multisig is responsible for configuring various LayerZero parameters. Incorrect configuration, such as setting an invalid `trustedRemote` address, misconfiguring `minDstGas`, or setting incompatible message library versions, could lead to cross-chain transactions failing, tokens being stuck in transit, or unexpected fee consumption (7.8 Operations). These errors, while not necessarily security vulnerabilities, can significantly impact user experience and protocol functionality.

**Recommendation:** Establish a rigorous testing and verification process for all LayerZero configuration changes before deployment to production. Maintain clear documentation of all configuration parameters and their intended values. Implement automated checks or simulations where possible to validate the correctness of new configurations. Ensure that the team managing these configurations has a deep understanding of LayerZero's operational requirements.


### `M-03` — Centralized Control over LayerZero Configurations  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Ownable` owner (a 3/5 multisig) has extensive control over critical LayerZero parameters within the `OFT` base contract. This includes the ability to set trusted remotes, message libraries, and various configuration parameters (e.g., `setTrustedRemote`, `setSendVersion`, `setReceiveVersion`, `setMinDstGas`). While a multisig mitigates some risk, a compromise or mismanagement of the multisig could lead to severe operational issues, such as disabling cross-chain transfers, routing messages through malicious endpoints, or causing funds to become stuck.

**Recommendation:** Implement robust operational security procedures for the owner multisig, including strict key management, multi-factor authentication for signers, and clear governance processes for approving configuration changes. Regularly audit all LayerZero configurations and ensure that `trustedRemote` addresses correspond to legitimate and secure endpoints. Consider implementing time-locks or additional governance checks for highly sensitive configuration changes.


### `L-01` — Constructor Parameter `_delegate` Dual Role  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_delegate` address passed to the constructor is used to initialize both the `OFT` base contract and the `Ownable` base contract. This means the same address becomes the LayerZero delegate and the contract owner. While this is a common pattern and not a direct vulnerability, it consolidates significant control under a single entity (the multisig in this case).

**Recommendation:** Ensure that the `_delegate` address is always a highly secure, multi-signature wallet or a well-governed contract. Confirm that the team understands the full scope of control granted to this address through both the `Ownable` and `OFT` roles. No code change is strictly necessary given the use of a multisig, but awareness is key.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa961...266f`](https://bscscan.com/address/0xa9616e5e23ec1582c2828b025becf3ef610e266f) |
| **Network** | BNB Chain |
| **Price** | $0.113 |
| **24h Volume** | $10.3K |
| **Liquidity** | $137.8K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 85.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3376 buys / 3056 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xbb7dcdf040346422341c7b844a18663932336606)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/somniaoft-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*

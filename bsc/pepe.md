---
token: Pepe
ticker: PEPE
network: bsc
risk_score: 49
status: medium
date: 2026-09-12
---

# Pepe (PEPE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepe-bsc)

---

## Audit Summary

The PepeToken contract is an Omnichain Fungible Token (OFT) implementation utilizing LayerZero Labs' OFTWithFee standard. The contract itself is minimal, primarily inheriting functionality from well-established and audited LayerZero libraries and OpenZeppelin's Ownable. The primary security considerations stem from the inherent centralization of control granted to the contract owner (a 5/8 multisig) over critical cross-chain parameters and the reliance on the external LayerZero endpoint. While the code quality is high and standard patterns are followed, the extensive administrative privileges introduce significant governance and economic risks.

> **Final Recommendation:** To mitigate the identified risks, it is crucial to maintain robust operational security for the owner multisig, ensuring its keys are securely managed and transactions are thoroughly reviewed. Implement strict internal procedures for setting and updating critical LayerZero parameters, especially trusted remote addresses and fee configurations, to prevent misconfigurations or malicious changes. Establish comprehensive monitoring for all cross-chain transactions and LayerZero endpoint interactions to detect anomalies promptly. Given the contract's reliance on external LayerZero infrastructure, continuous monitoring of LayerZero's security announcements and operational status is also recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical architecture (7.1 Architecture) is sound, leveraging the standard LayerZero OFT pattern for cross-chain token transfers. The code (7.2 Code Security) is minimal and primarily relies on… |
| **Governance / Economics** | 4/10 | Medium | The contract's owner (a 5/8 multisig) holds significant centralized control over critical parameters (7.5 Governance). This includes the ability to set trusted remote addresses for cross-chain… |
| **Upgrades** | 4/10 | Medium | The PepeToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This means that its logic cannot be modified after deployment. While this eliminates risks associated with upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 81.0% |
| **Top-3 Unlocked** | ⚠️ 88.1% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control Over Critical Cross-Chain Parameters  *(Severity: High · Status: Unresolved)*

The contract owner (a 5/8 multisig) possesses extensive control over critical LayerZero configurations and token transfer parameters. Functions such as `setTrustedRemote`, `setTrustedRemoteAddress`, `setFeeBP`, `setFeeWallet`, `setMinDstGas`, `setPrecrime`, and various LayerZero endpoint configurations (`setConfig`, `setSendVersion`, `setReceiveVersion`, `forceResumeReceive`) are exclusively callable by the owner. A compromise of the multisig or a malicious owner could lead to severe consequences, including redirecting cross-chain token transfers to attacker-controlled addresses, setting exorbitant fees, or blocking legitimate transactions.

**Recommendation:** While the use of a multisig mitigates single-point-of-failure, the broad scope of owner privileges remains a significant centralization risk. Implement robust operational security for the multisig, including strict key management, multi-factor authentication, and thorough review processes for all administrative transactions. Consider exploring decentralized governance mechanisms or time-locks for highly sensitive parameter changes in future iterations, if feasible within the LayerZero framework.


### `M-01` — Reliance on External LayerZero Endpoint Security  *(Severity: Medium · Status: Unresolved)*

The PepeToken contract, as an OFT, is fundamentally dependent on the security, availability, and correct functioning of the LayerZero endpoint (`lzEndpoint`). All cross-chain communication and token transfers rely on this external infrastructure (7.6 External). Any vulnerabilities, compromises, or operational issues within the LayerZero endpoint itself could directly impact the integrity and functionality of the PepeToken's cross-chain capabilities, potentially leading to loss of funds or denial of service for users.

**Recommendation:** While direct control over the LayerZero endpoint is not possible, it is crucial to monitor LayerZero's official security announcements, audits, and operational status. Maintain a robust incident response plan for scenarios involving LayerZero endpoint disruptions or compromises. Users should be aware of the inherent risks associated with relying on external bridging infrastructure.


### `L-01` — Potential for Misconfiguration of LayerZero Parameters  *(Severity: Low · Status: Unresolved)*

The owner has the ability to configure various LayerZero-specific parameters, such as `minDstGas` and `trustedRemote` addresses. Incorrectly setting these parameters, for example, by providing an insufficient `minDstGas` value, could lead to failed cross-chain transactions and wasted gas. Similarly, an incorrect `trustedRemote` address could result in tokens being bridged to an unintended or non-existent contract on a destination chain, leading to irrecoverable loss of funds.

**Recommendation:** Establish clear, documented procedures for setting and updating all LayerZero-related parameters. Implement a rigorous testing and verification process for any new configurations before deploying them to production. Ensure that `trustedRemote` addresses are double-checked against official LayerZero documentation or known deployments. Consider implementing off-chain monitoring to alert if `minDstGas` values are set too low or too high relative to typical transaction costs.


### `I-01` — No Upgradeability Mechanism  *(Severity: Informational · Status: Unresolved)*

The PepeToken contract is deployed directly and does not utilize a proxy pattern (e.g., UUPS, Transparent) for upgradeability (7.7 Upgrades). This means that the contract's logic is immutable after deployment. While this eliminates risks associated with upgrade mechanisms themselves, it implies that any future bug fixes, feature enhancements, or protocol changes would necessitate deploying an entirely new contract and migrating all existing tokens, which can be a complex and disruptive process for users and the ecosystem.

**Recommendation:** This is a design choice. If future upgradeability is desired, consider implementing a proxy pattern for new deployments. For the current contract, acknowledge the immutability and plan for potential migration strategies if significant changes become necessary.


### `I-02` — Reliance on Third-Party LayerZero Libraries  *(Severity: Informational · Status: Unresolved)*

The PepeToken contract heavily relies on external, third-party libraries from LayerZero Labs (e.g., `OFTWithFee`, `LzApp`) and OpenZeppelin (`Ownable`). The security and correctness of the entire system are contingent upon the integrity and absence of vulnerabilities within these imported contracts. While these libraries are generally well-audited and widely used, any undiscovered vulnerabilities in them could directly impact the PepeToken contract.

**Recommendation:** Regularly review security advisories and updates from LayerZero Labs and OpenZeppelin. Ensure that the deployed versions of these libraries are the most secure and up-to-date. While direct auditing of these extensive libraries is beyond the scope of this report, staying informed about their security posture is crucial.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x25d8...bb00`](https://bscscan.com/address/0x25d887ce7a35172c62febfd67a1856f20faebb00) |
| **Network** | BNB Chain |
| **Price** | $0.0000034 |
| **24h Volume** | $176.6K |
| **Liquidity** | $275.4K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 3y |
| **Top-10 Holders** | 21.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1079 buys / 1942 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xdd82975ab85e745c84e497fd75ba409ec02d4739)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepe-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*

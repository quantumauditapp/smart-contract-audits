---
token: INFINIT
ticker: IN
network: bsc
risk_score: 55
status: medium
date: 2026-09-27
---

# INFINIT (IN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/infinit-bsc)

---

## Audit Summary

The IN_Token contract, an upgradeable ERC-20 OFT, implements standard token functionalities with cross-chain capabilities via LayerZero. It utilizes OpenZeppelin and LayerZero upgradeable libraries. Key security features include a multisig for ownership and proxy administration. The primary risks identified relate to the centralized control over token supply and critical external dependencies.

> **Final Recommendation:** Ensure robust operational security for the multisig controlling both the token and the proxy administration, including secure key management and strict quorum procedures. Carefully verify all parameters, especially the `_delegate` address, during the one-time `initialize` function call to prevent misconfiguration. Acknowledge and monitor the inherent risks associated with the LayerZero endpoint, as its security and liveness are critical for cross-chain operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages well-audited OpenZeppelin and LayerZero upgradeable libraries, contributing to a solid technical foundation (7.2 Code Security). The use of Solidity 0.8.22 mitigates common… |
| **Governance / Economics** | 3/10 | High | The contract's economic model features centralized `mint` and `burn` functions, controlled by a 4/7 multisig (7.3 Access Control). While the multisig provides a strong governance mechanism, this… |
| **Upgrades** | 1/10 | High | The contract employs the Transparent Upgradeable Proxy pattern with OpenZeppelin's `initializer` functions, which is a standard and well-understood upgradeability mechanism (7.7 Upgrades). The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 4-of-7 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 1 Informational_

### `H-01` — Centralized Control over Token Supply  *(Severity: High · Status: Unresolved)*

The `mint` and `burn` functions are restricted to the contract owner, which is a 4/7 multisig. This grants significant power over the token's total supply, allowing for arbitrary inflation or deflation. While a multisig mitigates a single point of failure, it still represents a centralized authority that could impact token economics and trust assumptions (7.3 Access Control, 7.4 Economic).

**Recommendation:** Clearly communicate the implications of centralized mint/burn authority to users. Consider implementing a time-locked governance mechanism or a community-driven proposal system for significant supply changes, or explore mechanisms to cap total supply if appropriate for the token's design.


### `M-01` — Critical Initialization Parameter (`_delegate`)  *(Severity: Medium · Status: Unresolved)*

The `initialize` function takes a `_delegate` parameter which is used to set both the initial `Ownable` owner and the `OFTUpgradeable` delegate. A misconfiguration during deployment, such as providing an incorrect or compromised address, would lead to the contract being controlled by an unintended entity or becoming unmanageable. This is a critical one-time setup risk (7.8 Operations, 7.3 Access Control).

**Recommendation:** Implement a rigorous deployment checklist and multi-party verification process for the `initialize` function parameters, especially the `_delegate` address. Consider using a well-tested deployment script that logs and verifies all parameters before execution.


### `M-02` — External Dependency on LayerZero Endpoint  *(Severity: Medium · Status: Unresolved)*

The `IN_Token` contract relies on the LayerZero v2 endpoint for its cross-chain functionality. The security, liveness, and upgradeability of this external endpoint are critical to the token's operation. Any vulnerabilities, compromises, or operational issues within the LayerZero infrastructure could directly impact the token's ability to perform cross-chain transfers (7.6 External).

**Recommendation:** Monitor LayerZero's security announcements, audits, and operational status closely. Understand the risks associated with cross-chain bridges and communicate them transparently to users. Consider implementing emergency pause mechanisms if the LayerZero endpoint experiences critical issues.


### `I-01` — Multisig Operational Security  *(Severity: Informational · Status: Unresolved)*

Both the contract owner (for `mint`/`burn`) and the proxy admin (for upgrades) are controlled by a 4/7 multisig. While this is a robust access control mechanism, the security of the system ultimately depends on the operational security practices of the multisig signers (e.g., key management, quorum procedures, resistance to social engineering) (7.5 Governance, 7.8 Operations).

**Recommendation:** Ensure all multisig signers adhere to best practices for private key management, including hardware wallets, strong authentication, and secure communication channels. Regularly review and update multisig policies and procedures, and conduct periodic security awareness training for signers.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x61fa...3d50`](https://bscscan.com/address/0x61fac5f038515572d6f42d4bcb6b581642753d50) |
| **Network** | BNB Chain |
| **Price** | $0.04101 |
| **24h Volume** | $6.32M |
| **Liquidity** | $1.32M |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 89.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9212 buys / 10516 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x5bd808ab85c124f99080da5f864edcb39950ede5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/infinit-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-27*

---
token: Dexe
ticker: DEXE
network: bsc
risk_score: 76
status: critical
date: 2026-07-22
---

# Dexe (DEXE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 76/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dexe-bsc)

---

## Audit Summary

This audit report covers the provided OpenZeppelin utility libraries (`StorageSlot` and `Address`) and general observations regarding the Beacon proxy structure for the BridgeToken protocol. The core business logic for the `BridgeToken` and its `TokenImplementation` was not provided, limiting the scope of this audit. A key concern identified is the unverified administration of the Beacon contract, which controls the upgrade path for all associated proxies.

> **Final Recommendation:** It is critical to ensure that the Beacon contract's administrator is secured with robust access control mechanisms, ideally a multi-signature wallet or a time-locked governance contract. Provide the full source code for the `BridgeToken` and its `TokenImplementation` contracts, along with the Beacon contract, for a comprehensive security audit. This will allow for a thorough review of the core business logic, access control, economic model, and the complete upgradeability architecture.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The provided code consists of OpenZeppelin's `StorageSlot` and `Address` libraries (7.2 Code Security). These libraries are widely used, well-audited, and adhere to high security standards, providing… |
| **Governance / Economics** | 1/10 | High | The economic and governance aspects of the `BridgeToken`'s core functionality could not be assessed due to the absence of its source code (7.4 Economic, 7.5 Governance). However, the identified… |
| **Upgrades** | 1/10 | High | The protocol utilizes a Beacon proxy pattern, allowing for efficient upgrades of multiple proxy instances through a single Beacon contract (7.7 Upgrades). While this pattern is robust, the security… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Unverified Beacon Admin Control  *(Severity: Medium · Status: Unresolved)*

The audit notes indicate that the administrator for the Beacon contract (0xb6f6d86a8f9879a9c87f643768d9efc38c1da6e7), which dictates the implementation address for all associated proxies, could not be classified. For a Beacon proxy system, the security of the Beacon's admin is paramount. An unmanaged, single-point-of-failure, or compromised Beacon admin could lead to unauthorized upgrades, potentially deploying malicious contract logic and compromising user funds or protocol integrity.

**Recommendation:** Provide the source code for the Beacon contract and clarify its administrative control mechanisms. It is strongly recommended that the Beacon's admin be secured by a robust multi-signature wallet (e.g., Gnosis Safe) or a time-locked governance contract to prevent single points of failure and provide a delay for critical changes.


### `L-01` — Core Contract Logic Not Provided for Audit  *(Severity: Low · Status: Unresolved)*

The primary business logic for the `BridgeToken` (proxy) and its `TokenImplementation` (implementation) contracts was not provided for review. This audit is therefore limited to the provided OpenZeppelin libraries and general observations about the proxy structure. A comprehensive security assessment of the protocol's specific functionalities, access control, economic model, and potential vulnerabilities (e.g., reentrancy, integer overflows) cannot be performed without the full source code.

**Recommendation:** Provide the complete source code for all contracts comprising the BridgeToken protocol, including the `BridgeToken` proxy, `TokenImplementation`, and the Beacon contract, for a full and thorough security audit. This will enable a detailed analysis of the entire system's security posture.


### `I-01` — Standard Library Usage  *(Severity: Informational · Status: Unresolved)*

The provided contract code utilizes well-audited and widely adopted OpenZeppelin libraries (`StorageSlot.sol` and `Address.sol`). These libraries are known for their high quality, security, and adherence to best practices in smart contract development. Their inclusion contributes positively to the overall code reliability.

**Recommendation:** Continue to leverage well-vetted and community-audited libraries like OpenZeppelin to reduce the risk of introducing common vulnerabilities. Ensure that the specific versions used are up-to-date and free from known exploits.


### `I-02` — Beacon Proxy Pattern Identified  *(Severity: Informational · Status: Unresolved)*

The contract at 0x6e88056e8376ae7709496ba64d37fa2f8015ce3e is identified as a Beacon proxy, delegating its logic to an implementation contract (0x7f8c5e730121657e17e452c5a1ba3fa1ef96f22a) via a Beacon contract (0xb6f6d86a8f9879a9c87f643768d9efc38c1da6e7). This pattern allows multiple proxies to share and upgrade their implementation logic through a single Beacon, promoting efficiency and consistency.

**Recommendation:** Ensure that the Beacon proxy pattern is fully understood and correctly implemented across all associated contracts. Pay close attention to the security of the Beacon contract itself, as it is a central point of control for upgrades.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6e88...ce3e`](https://bscscan.com/address/0x6e88056e8376ae7709496ba64d37fa2f8015ce3e) |
| **Network** | BNB Chain |
| **Price** | $0.5841 |
| **24h Volume** | $6.9K |
| **Liquidity** | $3.9K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 2y |
| **Top-10 Holders** | 96.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 279 buys / 559 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x23ab35fac8a7ff11f0fe197df68e8ee52e415f2a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dexe-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*

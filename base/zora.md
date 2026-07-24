---
token: Zora
ticker: ZORA
network: base
risk_score: 41
status: medium
date: 2026-07-22
---

# Zora (ZORA) — Smart Contract Security Analysis | Base

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zora-base)

---

## Audit Summary

The Zora token contract is an ERC20 token with voting and permit functionalities, built upon OpenZeppelin's battle-tested libraries. The contract utilizes an immutable `initializerAccount` for a one-time initial minting of the entire token supply and setting of the contract URI. While the architecture is straightforward and leverages robust components, the centralized control over initial supply distribution and metadata setting by a single account presents a high trust requirement. The contract is not designed for proxy upgrades, using `Initializable` solely for single-call setup.

> **Final Recommendation:** It is recommended to enhance the security posture by distributing critical initial control. Consider using a multi-signature wallet for the `initializerAccount` to mitigate the risk associated with a single point of failure for the initial token distribution and metadata setting. Additionally, implement event emissions for all significant state changes, such as the setting of the `_contractURI`, to improve transparency and on-chain verifiability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract (7.1 Architecture) is a standard ERC20 token inheriting from OpenZeppelin's ERC20, ERC20Permit, ERC20Votes, and Initializable, which are well-audited components. Custom logic for… |
| **Governance / Economics** | 1/10 | High | The `initializerAccount` (7.4 Economic) holds significant power, being solely responsible for minting the entire token supply and setting the permanent `_contractURI` during the `initialize` call.… |
| **Upgrades** | 6/10 | Medium | The contract utilizes the `Initializable` base contract (7.7 Upgrades) to ensure the `initialize` function can only be called once. However, this contract is not designed as an upgradeable proxy.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 65.5% |
| **Top-3 Unlocked** | ⚠️ 81.1% |

## Security Findings

_🟠 1 High · 🟢 2 Low · ⚪ 2 Informational_

### `H-01` — Centralized Initial Minting and URI Setting  *(Severity: High · Status: Unresolved)*

The `initialize` function, which is responsible for minting the entire token supply and setting the permanent `_contractURI`, can only be called by the `immutable initializerAccount`. This grants significant, centralized power to a single external account for the initial setup of the token's core properties. If this account were compromised or malicious, the entire initial token distribution and metadata could be adversely affected.

**Recommendation:** Consider using a multi-signature wallet for the `initializerAccount` to distribute trust and reduce the risk of a single point of failure. This would require multiple approvals for the critical `initialize` call, enhancing security.


### `L-01` — Missing Event for Contract URI Setting  *(Severity: Low · Status: Unresolved)*

The `_contractURI` is a crucial piece of token metadata set during initialization, but no event is emitted to log this action on-chain. While the `contractURI()` function allows retrieval, an event provides a transparent, immutable, and easily verifiable historical record of when and what URI was set, which is beneficial for off-chain indexing and monitoring.

**Recommendation:** Emit an event, such as `event ContractURISet(string indexed contractURI)`, within the `initialize` function immediately after `_contractURI` is set. This improves transparency and auditability.


### `L-02` — Potential for High Gas Usage in `initialize` with Large Arrays  *(Severity: Low · Status: Unresolved)*

The `initialize` function iterates through the `tos` and `amounts` arrays to mint tokens. If these arrays contain an extremely large number of elements, the transaction's gas cost could exceed the block gas limit, preventing the successful execution of the initialization. While unlikely for typical initial distributions, it's a design consideration for very large-scale token launches.

**Recommendation:** Ensure that the expected number of recipients and amounts for the initial distribution will not cause the transaction to exceed the block gas limit. If a very large distribution is anticipated, consider breaking it into multiple transactions (if the design allows) or using an alternative distribution mechanism that handles large batches more efficiently.


### `I-01` — Use of `Initializable` without Proxy Pattern  *(Severity: Informational · Status: Unresolved)*

The contract inherits from OpenZeppelin's `Initializable` but is not part of a proxy upgrade system. While `Initializable` correctly prevents re-initialization of the `initialize` function, its primary purpose in OpenZeppelin is for upgradeable proxy contracts. This usage is technically correct for ensuring a single-call initialization, but it might lead to confusion regarding the contract's upgradeability if not clearly documented.

**Recommendation:** Clearly document the intent behind using `Initializable` if the contract is not intended to be upgradeable via a proxy. This clarifies that `Initializable` is used solely for secure, one-time setup and not for future contract upgrades.


### `I-02` — High Solidity Compiler Version (0.8.28)  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with Solidity 0.8.28, which is a very recent version. While this benefits from the latest compiler optimizations and security features (e.g., default checked arithmetic), it also means it has had less time to be battle-tested in production environments compared to slightly older, more established stable versions (e.g., 0.8.20).

**Recommendation:** Ensure thorough testing across various scenarios and consider the trade-offs of using the absolute latest compiler version for production deployments. While generally safe, newer versions might occasionally introduce subtle, undiscovered compiler-specific behaviors.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1111...fc69`](https://basescan.org/address/0x1111111111166b7fe7bd91427724b487980afc69) |
| **Network** | Base |
| **Price** | $0.006404 |
| **24h Volume** | $75.6K |
| **Liquidity** | $153.2K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 55.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2366 buys / 1276 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xedc625b74537ee3a10874f53d170e9c17a906b9c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zora-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*

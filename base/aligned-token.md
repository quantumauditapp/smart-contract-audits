---
token: Aligned Token
ticker: ALIGN
network: base
risk_score: 56
status: medium
date: 2026-09-14
---

# Aligned Token (ALIGN) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aligned-token-base)

---

## Audit Summary

The OptimismMintableERC20 contract serves as a standard ERC-20 token with minting and burning capabilities restricted to a designated bridge address. The contract is well-structured, utilizes OpenZeppelin libraries, and employs immutable variables for critical addresses and decimals. Identified issues are minor, primarily related to interface consistency and code redundancy, with no critical or high-severity vulnerabilities found.

> **Final Recommendation:** It is recommended to address the identified interface mismatch to ensure full compliance and clarity for external integrations. While redundant functions do not pose a direct security risk, consolidating them can improve code efficiency and reduce deployment costs. Emphasize robust security measures for the `BRIDGE` contract, as its compromise would directly impact the integrity of this token's supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates strong technical security (7.2 Code Security) by leveraging OpenZeppelin's ERC20 implementation and Solidity 0.8.15's default checked arithmetic. Access control (7.3 Access… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) of this token relies entirely on the `BRIDGE` address for supply control, as it is the sole entity capable of minting and burning tokens. This design is inherent to… |
| **Upgrades** | 3/10 | High | The contract is not designed as an upgradeable proxy (7.7 Upgrades). All critical parameters are set as immutable in the constructor, meaning its logic cannot be changed post-deployment. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 79.5% |
| **Top-3 Unlocked** | ⚠️ 95.9% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Interface Mismatch for `bridge()` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `IOptimismMintableERC20` interface declares the `bridge()` function as `external returns (address);`, implying it might be a state-changing or non-view function. However, the `OptimismMintableERC20` implementation correctly defines it as `public view returns (address)`. While the implementation is functionally correct for a getter, this mismatch in the interface definition could lead to confusion or unexpected behavior if external tools or contracts strictly adhere to the interface's non-view declaration.

**Recommendation:** Update the `IOptimismMintableERC20` interface to declare `function bridge() external view returns (address);` to accurately reflect the `view` nature of the function in the implementation.


### `L-01` — Redundant Getter Functions  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes multiple functions that return the same immutable addresses: `l1Token()` and `remoteToken()` both return `REMOTE_TOKEN`; `l2Bridge()` and `bridge()` both return `BRIDGE`. While not a security vulnerability, this redundancy adds unnecessary code complexity and slightly increases deployment gas costs.

**Recommendation:** Consolidate redundant getter functions. For example, remove `l1Token()` and `l2Bridge()`, relying solely on `remoteToken()` and `bridge()` respectively, or vice-versa, ensuring consistency with the primary interface names.


### `I-01` — Centralized Control by Bridge Address  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` and `burn` functionalities are exclusively controlled by the `BRIDGE` address via the `onlyBridge` modifier. This design is fundamental to the cross-chain bridging mechanism, where the L2 token supply is managed by an L1 bridge. However, it means the security and integrity of the entire token supply on L2 heavily relies on the security of the `BRIDGE` contract. A compromise of the `BRIDGE` would allow arbitrary minting or burning, potentially devaluing the token.

**Recommendation:** This is an inherent design choice for mintable bridge tokens. Ensure the `BRIDGE` contract itself is highly secured, thoroughly audited, and follows robust operational security practices to mitigate the risk of its compromise.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x53f3...0a8d`](https://basescan.org/address/0x53f39e5c53ee40bbc3da97c3b47bd2968d110a8d) |
| **Network** | Base |
| **Price** | $0.005905 |
| **24h Volume** | $41.4K |
| **Liquidity** | $131.4K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 89.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 224 buys / 435 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x0f56aeba06f65e2790c5b6687f5c3128b7456f76)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aligned-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*

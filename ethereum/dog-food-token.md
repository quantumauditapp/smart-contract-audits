---
token: Dog Food Token
ticker: OISHII
network: ethereum
risk_score: 47
status: medium
date: 2026-09-04
---

# Dog Food Token (OISHII) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dog-food-token-eth)

---

## Audit Summary

The audit of the EtherVista Token contract identified a significant design limitation in the `approve` function, which, when enabled, restricts token approvals to a single hardcoded router address. This severely impacts the token's interoperability with other DeFi protocols. Minor issues include the use of `tx.origin` for initial minting and a lack of standard extensibility hooks.

> **Final Recommendation:** It is strongly recommended to reconsider the `vistaOnly` functionality within the `approve` function. If the intention is to allow broader DeFi integration, this restriction should be removed or made configurable by a trusted entity. If the restriction is essential, ensure robust mechanisms are in place to update the router address if the factory changes or is compromised. Additionally, for future contracts, avoid using `tx.origin` and instead use `_msgSender()` for any address-related operations, even for initial minting, to adhere to best practices.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements a standard ERC-20 token with custom error handling, which is a positive security practice. It utilizes `unchecked` blocks for gas efficiency where appropriate. However, a… |
| **Governance / Economics** | 1/10 | High | The token's economic model is a standard fixed-supply ERC-20, minted entirely at deployment. There are no complex economic mechanisms or governance features within this contract. The primary economic… |
| **Upgrades** | 7/10 | Low | This contract is not designed to be upgradeable, meaning its logic is immutable once deployed. This eliminates risks associated with upgrade mechanisms, such as proxy pattern vulnerabilities or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — UNCX Locker |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Highly Restrictive `approve` Functionality with Hardcoded Dependency  *(Severity: High · Status: Unresolved)*

The `approve` function, when the `vistaOnly` flag is set to `true`, restricts approvals exclusively to the router address obtained from a hardcoded `IEtherVistaFactory` instance (`0x9a27cb5ae0B2cEe0bb71f9A85C0D60f3920757B4`). This design choice severely limits the token's utility, preventing it from interacting with other DeFi protocols that require `approve` calls to different spenders (e.g., lending platforms, other AMMs, staking contracts). Furthermore, the hardcoded `factory` address means the token's functionality is permanently tied to a single external contract. If that factory contract is compromised, upgraded, or ceases to exist, or if the router address it returns becomes invalid,…

**Recommendation:** Reconsider the necessity and implications of the `vistaOnly` flag. If broader DeFi interoperability is desired, this restriction should be removed. If the restriction is critical, implement a mechanism (e.g., an owner-controlled function) to update the `factory` address or the allowed `router` address, rather than hardcoding it, to mitigate risks associated with external dependency failures.


### `L-01` — Use of `tx.origin` for Initial Minting  *(Severity: Low · Status: Unresolved)*

The constructor uses `tx.origin` to mint the initial token supply to the deployer. While this is not a critical access control vulnerability in this specific context (as it's for initial supply and not for ongoing permissions), `tx.origin` is generally discouraged in Solidity. It can be susceptible to phishing attacks where a malicious contract could trick a user into signing a transaction that appears legitimate but actually grants permissions or transfers assets to the attacker, if `tx.origin` were used for critical access control. For initial minting, the risk is lower but it deviates from best practices. (7.2 Code Security)

**Recommendation:** For future contracts, it is best practice to use `_msgSender()` (which resolves to `msg.sender`) instead of `tx.origin` for any address-related operations, including initial minting, to align with secure coding standards and prevent potential `tx.origin` related attack vectors in more complex scenarios.


### `I-01` — Lack of Standard Extensibility Hooks  *(Severity: Informational · Status: Unresolved)*

The `ERC20` implementation does not include common extensibility hooks like `_beforeTokenTransfer` or `_afterTokenTransfer`, which are typically found in widely used ERC-20 libraries (e.g., OpenZeppelin). While not a direct vulnerability, this design choice limits the ability to add custom logic (e.g., fee mechanisms, blacklisting, compliance checks, or tax functions) in the future without modifying the core `_transfer` logic. This could necessitate a new token deployment if such features become necessary, increasing operational overhead. (7.1 Architecture)

**Recommendation:** Consider incorporating standard extensibility hooks in future ERC-20 implementations to allow for easier integration of custom logic and future-proofing without requiring a full redeployment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa1b0...7023`](https://etherscan.io/address/0xa1b014878d47c0836ed79163ddec55985adb7023) |
| **Network** | Ethereum |
| **Price** | $0.001135 |
| **24h Volume** | $37.8K |
| **Liquidity** | $38.2K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 99.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 128 buys / 99 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x59382d9cae33f7252a10573435a4fba8aecc45f8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dog-food-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*

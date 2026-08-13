---
token: Ark Of Panda
ticker: AOP
network: bsc
risk_score: 54
status: high
date: 2026-08-13
---

# Ark Of Panda (AOP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ark-of-panda-bsc)

---

## Audit Summary

The AOPToken contract implements a standard ERC20 token with an Ownable access control pattern and a capped maximum supply. The contract leverages well-tested OpenZeppelin patterns for its core ERC20 functionality. Key features include owner-controlled minting up to a defined `maxSupply`. The primary risks identified relate to the centralized control inherent in the Ownable pattern and a minor inefficiency in the `mint` function's supply check.

> **Final Recommendation:** It is recommended to implement multi-signature control for critical administrative functions, especially for the `mint` function and `transferOwnership`, to mitigate the single point of failure risk associated with the `Ownable` pattern. Additionally, consider refining the `mint` function to perform the `maxSupply` check prior to executing state changes for improved gas efficiency and clarity. Ensure the project's documentation clearly communicates the implications of the large `maxSupply` and the owner's minting capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The AOPToken contract is built upon robust OpenZeppelin ERC20 and Ownable implementations, ensuring a solid foundation for its core functionality (7.1 Architecture, 7.2 Code Security). The use of… |
| **Governance / Economics** | 4/10 | Medium | The contract employs an `Ownable` pattern, granting the deployer (owner) significant control, including the ability to mint tokens up to a `maxSupply` (7.3 Access Control, 7.5 Governance). This… |
| **Upgrades** | 6/10 | Medium | The AOPToken contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard, non-upgradeable implementation. Therefore, there are no specific upgrade safety issues to address. Any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control via Ownable Pattern  *(Severity: High · Status: Unresolved)*

The contract uses the `Ownable` pattern, granting a single external address (the owner) exclusive control over critical functions such as `mint` and `transferOwnership`. If the owner's private key is compromised, a malicious actor could mint the entire `maxSupply` of tokens, leading to severe economic consequences for the token holders. This represents a significant single point of failure (7.3 Access Control, 7.5 Governance).

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) as the contract owner to distribute control among multiple trusted parties. This significantly reduces the risk of a single point of compromise. For less critical operations, consider implementing a time-locked governance mechanism.


### `M-01` — `maxSupply` Check After `_mint` Operation  *(Severity: Medium · Status: Unresolved)*

In the `mint` function, the `maxSupply` check (`if (totalSupply() > maxSupply)`) occurs after the `_mint` internal function has already updated the `_totalSupply` and `_balances` state variables. While the transaction will revert if `maxSupply` is exceeded, this approach is less gas-efficient as it performs state changes that are then discarded. It is generally better practice to validate conditions that would cause a revert *before* modifying state (7.2 Code Security, 7.4 Economic).

**Recommendation:** Move the `maxSupply` check to occur before the `_mint` call. For example, add `require(totalSupply() + amount_ <= maxSupply, 'AOPToken: mint exceeds max supply');` before `_mint(to_, amount_);` to prevent unnecessary state changes and reverts.


### `L-01` — Very Large `maxSupply` Value  *(Severity: Low · Status: Unresolved)*

The `maxSupply` is set to 2,000,000,000 ether (2 * 10^27), which is an extremely large number. While this is a design choice and not a technical vulnerability, such a high maximum supply, combined with owner-controlled minting, implies a significant potential for token inflation if the owner decides to mint a substantial portion of the supply. This could impact the token's value and market dynamics (7.4 Economic).

**Recommendation:** Ensure that the project's economic model and whitepaper clearly articulate the rationale behind such a large `maxSupply` and the owner's minting capabilities. Transparency regarding potential inflation scenarios is crucial for investor confidence. If possible, consider if a smaller, more controlled `maxSupply` would better align with the project's long-term vision.


### `I-01` — Inconsistent Custom Error Usage  *(Severity: Informational · Status: Unresolved)*

The contract defines a custom error `AOPTokenError` and uses it for the `maxSupply` check. However, other `require` statements throughout the contract (including inherited OpenZeppelin functions) use traditional string messages for reverts. Adopting a consistent error handling strategy, either using custom errors or string messages exclusively, can improve code readability and potentially reduce gas costs for reverts (7.2 Code Security).

**Recommendation:** Consider refactoring all revert conditions to use custom errors for consistency and potential gas optimization benefits (as custom errors can be cheaper than string reverts in certain scenarios). Alternatively, remove the custom error and use consistent string messages.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd5df...16c7`](https://bscscan.com/address/0xd5df4d260d7a0145f655bcbf3b398076f21016c7) |
| **Network** | BNB Chain |
| **Price** | $0.02971 |
| **24h Volume** | $6.87M |
| **Liquidity** | $1.12M |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 89.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11602 buys / 11584 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xca3f029a70d5d90000e614afd29e5c833f33cea5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ark-of-panda-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*

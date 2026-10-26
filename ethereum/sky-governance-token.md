---
token: SKY Governance Token
ticker: SKY
network: ethereum
risk_score: 40
status: medium
date: 2026-09-01
---

# SKY Governance Token (SKY) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sky-governance-token-eth)

---

## Audit Summary

The Sky token contract implements an ERC-20-like token with EIP-2612 permit functionality and a custom `wards` access control system. The audit identified a high-severity front-running vulnerability in the `permit` function and significant centralization risks related to token supply management and access control. While the code quality is generally good, these issues pose considerable security and economic risks.

> **Final Recommendation:** Prioritize addressing the `permit` function's front-running vulnerability by reordering the nonce increment. Evaluate the project's long-term vision regarding decentralization; consider implementing a multi-signature wallet for `wards` management and exploring a decentralized governance framework for critical functions like `mint` and `burn` to mitigate centralization risks and enhance community trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical practices, including robust EIP-712 and EIP-1271 signature validation and careful use of `unchecked` blocks after necessary checks (7.2). However, a… |
| **Governance / Economics** | 3/10 | High | The contract employs a centralized `wards` system for access control, where the deployer initially holds all administrative power and can manage other authorized users (7.3). This system grants a… |
| **Upgrades** | 3/10 | High | The contract is not designed with upgradeability in mind, meaning its logic is immutable once deployed (7.7). This eliminates risks associated with upgrade mechanisms, such as proxy implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 39.1% |
| **Top-3 Unlocked** | ⚠️ 81.3% |

## Security Findings

_🟡 4 Medium · ⚪ 1 Informational_

### `M-01` — Centralized Access Control (Wards System)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses a `wards` mapping and an `auth` modifier for access control. The deployer is initially the only authorized address and can grant or revoke authorization to others using `rely` and `deny`. This creates a single point of failure: if the controlling addresses are compromised, malicious actors could gain full control over the token's administrative functions, including minting new tokens and managing other authorized users (7.3).

**Recommendation:** Consider implementing a multi-signature scheme for the `wards` management functions (`rely`, `deny`) to distribute control and reduce the risk associated with a single point of failure.


### `M-02` — Lack of Decentralized Governance  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract lacks a robust, decentralized governance mechanism. All administrative decisions, including the ability to mint/burn tokens and manage authorized users, are concentrated in the hands of the `wards` (7.5). This design choice, while simple, may not align with the principles of decentralization often associated with blockchain projects and could lead to community distrust or perceived unfairness.

**Recommendation:** Explore integrating a decentralized governance framework (e.g., Compound's Governor Bravo, OpenZeppelin's Governor) to allow token holders to propose and vote on significant protocol changes and administrative actions. This would enhance transparency and community involvement.


### `M-03` — `permit` Function Front-Running Vulnerability  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `permit` function increments the `nonce` for the `owner` *before* validating the signature (`unchecked { nonce = nonces[owner]++; }`). This allows an attacker to front-run a legitimate `permit` transaction by simply calling `permit` with the same `owner` address (even with an valid signature or different parameters). The attacker's transaction would increment the `nonce`, causing the legitimate `permit` transaction to fail due to an incorrect `nonce` value in the signed message. This effectively allows an attacker to grief users attempting to use the `permit` functionality (7.2).

**Recommendation:** The `nonce` increment should occur *after* the signature validation and *before* the state change (i.e., `allowance` update). A common pattern is to increment the nonce only after a successful signature verification.


### `M-04` — Centralized Control Over Token Supply (Mint/Burn)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` and `burn` functions are protected by the `auth` modifier, which relies on the `wards` mapping. The initial deployer is the sole ward, and they can add or remove other wards via `rely` and `deny`. This grants a small set of authorized addresses (initially just the deployer) complete control over the token's total supply. This centralized control introduces a significant economic risk, as these addresses can arbitrarily inflate or deflate the supply, potentially devaluing existing tokens or manipulating market dynamics (7.4, 7.3).

**Recommendation:** Implement a more decentralized governance mechanism for critical functions like `mint` and `burn`, such as a time-locked multi-signature wallet or a community-driven DAO. If centralized control is intended, clearly document this risk and ensure robust operational security for the controlling addresses.


### `I-01` — Theoretical `totalSupply` or Balance Overflow in `mint`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` function, while using `unchecked` blocks for `balanceOf[to] = balanceOf[to] + value` and `totalSupply = totalSupply + value`, does not explicitly check for potential overflows if `balanceOf[to]` or `totalSupply` were to approach `type(uint252).max`. In a scenario where `totalSupply` or an individual `balanceOf` is already extremely high (near `type(uint256).max`), a subsequent `mint` operation could theoretically cause an overflow, leading to a wrap-around to zero or a small number (7.2). This is a theoretical edge case for standard ERC-20 tokens, as `type(uint256).max` is a very large number.

**Recommendation:** While highly unlikely to occur in practice for typical token economics, consider adding explicit checks (`require(balanceOf[to] + value >= balanceOf[to], "Overflow")` or `require(totalSupply + value >= totalSupply, "Overflow")`) within the `mint` function if the token's design anticipates extremely large supplies or individual balances that could approach `type(uint256).max`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5607...9279`](https://etherscan.io/address/0x56072c95faa701256059aa122697b133aded9279) |
| **Network** | Ethereum |
| **Price** | $0.06876 |
| **24h Volume** | $59.1K |
| **Liquidity** | $7.75M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 90.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 64 buys / 74 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x13dffad596ddfe401253f257f7568679149149615b8de0470b0736b8df2d555b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sky-governance-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*

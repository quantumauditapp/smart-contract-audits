---
token: Nockchain
ticker: NOCK
network: base
risk_score: 52
status: high
date: 2026-06-10
---

# Nockchain (NOCK) — Smart Contract Security Analysis | Base

> **Risk Score: 52/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nockchain-base)

---

## Audit Summary

The Nock contract is an ERC-20 token designed for Nockchain integration, featuring minting by a designated 'inbox' contract and burning for withdrawals. It utilizes OpenZeppelin's Ownable and ERC20 implementations, contributing to a solid foundation. Key findings include a high reliance on the security of the external IMessageInbox contract, centralized minting without a supply cap, and potential reentrancy concerns with external calls during burn operations. The contract is explicitly non-upgradeable, which eliminates upgrade-related risks but also prevents future modifications.

> **Final Recommendation:** Prioritize a comprehensive security audit of the `IMessageInbox` contract, as its integrity is paramount to the Nock token's security. Implement robust security measures for the `IMessageInbox` and its owner, such as multi-signature wallets and time-locks, especially given the lack of a token supply cap. Review the necessity of the external call within the `burn` function and consider reentrancy guards if the `IMessageInbox` contract is not fully trusted or could have reentrant behavior. Ensure all integrations are fully aware of and correctly handle the 16-decimal precision of the Nock token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The Nock contract leverages battle-tested OpenZeppelin libraries (ERC20, Ownable), providing a strong base for code security (7.2). The logic for minting and burning is straightforward, with… |
| **Governance / Economics** | 4/10 | Medium | The contract establishes clear access control (7.3) with an `Ownable` pattern, allowing the owner to update the critical `inbox` address. This provides a single point of control for managing the… |
| **Upgrades** | 4/10 | Medium | The Nock contract is explicitly designed to be non-upgradeable, as stated in its documentation: "This contract is NOT upgradeable to ensure immutability of the token." This design choice eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 51.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Reliance on External `IMessageInbox` Security  *(Severity: High · Status: Unresolved)*

The `Nock` token contract heavily relies on the security and correct behavior of the external `IMessageInbox` contract (7.6). The `inbox` address is the sole minter of `Nock` tokens and is called during every `burn` operation via `notifyBurn()`. A compromise or malfunction of `IMessageInbox` could lead to unauthorized token minting, denial of service for withdrawals, or other adverse effects, directly impacting the token's integrity and value.

**Recommendation:** Conduct a comprehensive security audit of the `IMessageInbox` contract and its associated off-chain logic. Ensure robust access control, input validation, and reentrancy protection within `IMessageInbox`, especially for functions interacting with `Nock`. Implement strong governance and operational security for the `IMessageInbox` contract's ownership and deployment.


### `M-01` — Centralized Minting and Lack of Supply Cap  *(Severity: Medium · Status: Unresolved)*

The `Nock` token has no explicit supply cap (the `cap()` function returns 0), and all minting is exclusively controlled by the `inbox` address (7.4). While this design centralizes control for specific operational reasons, it introduces a significant centralization risk. If the `inbox` contract or its controlling entity is compromised, an arbitrary amount of tokens could be minted, leading to severe token dilution and loss of value for existing holders.

**Recommendation:** Evaluate the necessity of an uncapped supply. If a cap is not feasible, implement robust security measures for the `IMessageInbox` contract and its owner, such as a multi-signature wallet, time-locks for critical operations, or a transparent governance mechanism. Consider adding a configurable supply cap if the protocol design allows for it.


### `M-02` — Potential Reentrancy in `burn` via External Call  *(Severity: Medium · Status: Unresolved)*

The `burn` function makes an external call to `IMessageInbox(inbox).notifyBurn()` after performing the token burn (7.2). Although the `_burn` operation occurs before the external call, which mitigates direct reentrancy on the `balanceOf` check for the burning user, an untrusted or malicious `IMessageInbox` contract could potentially re-enter the `Nock` contract in other ways or execute unexpected logic that affects the overall system state or other users. This violates the Checks-Effects-Interactions pattern.

**Recommendation:** While the direct reentrancy on the `burn` amount is mitigated, it is best practice to strictly follow the Checks-Effects-Interactions pattern. If `notifyBurn` is not intended to modify state or call back into `Nock`, consider adding a reentrancy guard to the `burn` function or ensuring `IMessageInbox` is non-reentrant. Alternatively, move the external call before state changes if possible, or use a pull-based mechanism.


### `L-01` — Owner's Ability to Change `inbox` Address  *(Severity: Low · Status: Unresolved)*

The `Ownable` contract pattern grants the contract owner the ability to update the `inbox` address via the `updateInbox` function (7.3, 7.5). Since the `inbox` address is the sole minter of `Nock` tokens, a malicious or compromised owner could transfer minting control to an attacker-controlled address, leading to unauthorized token issuance. This represents a single point of failure for a critical function.

**Recommendation:** Consider implementing a multi-signature wallet for the contract owner to reduce the risk of a single point of compromise. Additionally, a time-lock mechanism could be introduced for the `updateInbox` function, allowing users to react to a potentially malicious change before it takes effect.


### `I-01` — Non-Standard Decimals Value  *(Severity: Informational · Status: Unresolved)*

The `Nock` token overrides the standard ERC20 `decimals()` function to return 16 instead of the typical 18. While explicitly stated as 'Nockchain alignment,' this non-standard value can lead to integration issues, display errors in wallets or exchanges, and potential user confusion if not handled correctly by all interacting systems (7.4).

**Recommendation:** Ensure all front-end applications, exchanges, and integrated protocols are fully aware of and correctly handle the 16-decimal precision for `Nock` tokens. Clear and prominent documentation should be provided to prevent misinterpretation and ensure consistent display across platforms.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9b5e...1722`](https://basescan.org/address/0x9b5e262cf9bb04869ab40b19af91d2dc85761722) |
| **Network** | Base |
| **Price** | $0.01619 |
| **24h Volume** | $417.6K |
| **Liquidity** | $808.4K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 23.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1875 buys / 1606 sells |

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

## Frequently Asked Questions

### Is Nockchain a scam?

Based on available data, labeling Nockchain definitively as a scam is not possible without further context. However, critical vulnerabilities exist. The owner retains control, and liquidity is not locked, which are common characteristics seen in projects that later prove malicious. While the contract is verified, these factors contribute to its high-risk score and warrant extreme investor caution regarding potential malicious actions.

### Is Nockchain safe to buy?

Nockchain (NOCK) carries a high-risk score of 51/100, indicating it is not inherently safe for investment. Key risk factors include the contract owner retaining control, which could lead to unexpected changes or manipulation. Additionally, the liquidity is not locked, exposing investors to potential rug pulls where funds supporting the token's value are withdrawn. These significant risks should be carefully considered.

### Has Nockchain been audited?

The Nockchain contract is verified, meaning its code is publicly available for review on the blockchain. This enhances transparency. However, verification is not the same as a formal security audit by an independent firm. An audit rigorously assesses code for deeper vulnerabilities and adherence to best practices, which is not indicated by verification alone.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x85f1aa3a70fedd1c52705c15baed143e675cd626)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nockchain-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

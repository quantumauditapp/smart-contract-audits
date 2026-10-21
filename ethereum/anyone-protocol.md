---
token: ANyONe Protocol
ticker: ANYONE
network: ethereum
risk_score: 61
status: medium
date: 2026-09-05
---

# ANyONe Protocol (ANYONE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anyone-protocol-eth)

---

## Audit Summary

The AnyoneProtocolToken contract is an ERC20 token with `Ownable` access control, incorporating anti-bot mechanisms and a launch sequence. The contract utilizes OpenZeppelin libraries for standard functionalities, enhancing code security. However, significant centralization of control under the owner introduces a high economic risk, particularly regarding potential for rug pull or manipulation. Technical risks include gas limit concerns for batch operations and the use of `tx.origin` for bot detection. The contract is not upgradeable.

> **Final Recommendation:** To enhance the security and decentralization of the ANyONe Protocol, consider implementing mechanisms to reduce the single point of failure associated with the owner's extensive privileges. Explore options for multi-signature ownership or time-locked control for critical functions to mitigate rug pull risks. For batch operations, implement pagination or size limits to prevent potential gas limit issues. Review the `tx.origin` usage for bot detection and consider more robust, contract-based anti-bot strategies.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical practices by inheriting from OpenZeppelin's `ERC20` and `Ownable` contracts and utilizing `SafeERC20` for external token interactions (7.2 Code Security). The… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with the `Ownable` pattern granting the deployer extensive control over critical functions (7.3 Access Control, 7.5 Governance). The owner can… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable, as it does not implement any proxy pattern (7.7 Upgrades). This means its logic is immutable once deployed. Consequently, there are no upgrade-specific… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control and Potential for Rug Pull  *(Severity: High · Status: Unresolved)*

The contract grants significant power to the owner, including the ability to `excludeFromLimits` for any address, set/unset bots, and control the token launch. While these features are intended for project management and anti-bot measures, they also introduce a high degree of centralization. A malicious owner could exploit these privileges, for example, by excluding their own addresses from trading limits while others are subject to them, or by manipulating the AMM pair setup, potentially leading to a rug pull if liquidity is not adequately secured. This poses a significant economic risk (7.3 Access Control, 7.4 Economic).

**Recommendation:** Consider implementing a multi-signature wallet for ownership of critical functions or introducing a time-lock mechanism for sensitive operations. Explore options to decentralize control over key parameters, such as AMM pair settings or limit exclusions, possibly through a community governance model or by hardcoding immutable parameters post-launch. Ensure liquidity is locked or burned to prevent rug pull scenarios.


### `M-01` — Gas Limit Risk in Batch Operations  *(Severity: Medium · Status: Unresolved)*

Functions like `excludeFromLimits` and `setBots` iterate through an array of addresses. If the `accounts` array contains a large number of addresses, these operations could exceed the block gas limit, leading to a denial of service for these specific functions. While the owner controls the input, this design pattern can be problematic in high-volume scenarios or if the owner needs to process many addresses at once (7.2 Code Security).

**Recommendation:** Implement pagination for batch operations, allowing the owner to process addresses in smaller, manageable chunks. Alternatively, introduce a maximum array size limit to prevent transactions from exceeding the block gas limit. Consider an event-driven or pull-based mechanism for large-scale updates if feasible.


### `M-02` — `tx.origin` Usage for Anti-Bot Measures  *(Severity: Medium · Status: Unresolved)*

The `_beforeTokenTransfer` function uses `tx.origin` as part of its anti-bot logic (`require(tx.origin == from \|\| tx.origin == sender \|\| !isBot[tx.origin], "AnyoneProtocolToken: Bot detected.");`). While this specific use case aims to prevent bots initiated by an EOA marked as a bot, `tx.origin` is generally discouraged due to potential phishing vulnerabilities where a user might interact with a malicious contract that then calls this contract, making the `tx.origin` check pass even if the intermediate contract is malicious. In this context, it's less about phishing and more about the robustness of the anti-bot mechanism against sophisticated bot setups that might use intermediate contracts…

**Recommendation:** While the current usage is for anti-bot, consider if `msg.sender` checks alone or a more sophisticated bot detection mechanism would be sufficient and more robust. If `tx.origin` is deemed critical for the current anti-bot strategy, ensure the limitations are understood and accepted, and consider adding additional layers of bot detection.


### `L-01` — Low-Level Call in `withdrawStuckTokens`  *(Severity: Low · Status: Unresolved)*

The `withdrawStuckTokens` function uses a low-level `call{value: amount}("")` for native token withdrawals. While a `require(success)` check is present, and the recipient is the `owner` (an EOA), generally, interactions with external contracts should be handled with reentrancy guards if state changes occur after the call. In this specific case, no critical state changes occur after the call, making the reentrancy risk low, but it's a pattern worth noting (7.2 Code Security).

**Recommendation:** For simple native token transfers to an EOA, `transfer()` or `send()` are generally preferred as they have a fixed gas stipend, reducing reentrancy attack surface. If `call` is necessary for specific reasons (e.g., forwarding more gas), ensure no critical state changes occur after the call, or implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`).


### `I-01` — Hardcoded Address in Constructor  *(Severity: Informational · Status: Unresolved)*

The constructor hardcodes a specific address (`0x61fFE014bA17989E743c5F6cB21bF9697530B21e`) to be excluded from limits. While this might be intentional for a specific operational address, hardcoding addresses can reduce flexibility and make future changes or deployments to different environments more cumbersome. It also requires careful verification that the hardcoded address is correct and intended (7.1 Architecture).

**Recommendation:** If the hardcoded address is intended to be a fixed protocol address, document its purpose clearly. For greater flexibility, consider passing such addresses as constructor arguments or allowing the owner to set them post-deployment via an `onlyOwner` function, if appropriate for the protocol's design.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfeac...c0f9`](https://etherscan.io/address/0xfeac2eae96899709a43e252b6b92971d32f9c0f9) |
| **Network** | Ethereum |
| **Price** | $0.149 |
| **24h Volume** | $351.5K |
| **Liquidity** | $707.1K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 2y |
| **Top-10 Holders** | 48.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 612 buys / 343 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc593fe9193b745447e86b45ea0bf62565ee030cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anyone-protocol-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-05*

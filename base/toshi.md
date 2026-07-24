---
token: Toshi
ticker: TOSHI
network: base
risk_score: 5
status: low
date: 2026-07-18
---

# Toshi (TOSHI) — Smart Contract Security Analysis | Base

> **Risk Score: 5/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/toshi-base)

---

## Audit Summary

The ToshiToken contract is an ERC20 token implementation based on OpenZeppelin Contracts v4.x. The provided code snippet indicates a standard, well-tested foundation. No critical or high-severity vulnerabilities were identified. Minor informational findings relate to standard ERC20 characteristics and a non-critical pragma usage.

> **Final Recommendation:** The ToshiToken contract is a robust implementation of the ERC20 standard, leveraging OpenZeppelin's audited libraries. It is recommended to ensure that the owner address is secured with multi-signature wallets or robust access controls to mitigate the single point of failure inherent in the Ownable pattern. Additionally, users interacting with the `approve` function should be educated on the known ERC20 race condition to prevent potential front-running issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The ToshiToken contract is built upon battle-tested OpenZeppelin ERC20 and Ownable implementations, which significantly reduces the likelihood of common technical vulnerabilities (7.2 Code Security).… |
| **Governance / Economics** | 6/10 | Medium | The contract implements a standard ERC20 token with no complex economic models or governance mechanisms (7.5 Governance). Ownership is centralized via OpenZeppelin's Ownable pattern (7.3 Access… |
| **Upgrades** | 8/10 | Low | The provided contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard, non-upgradeable implementation. Therefore, upgrade safety concerns are not applicable to this specific… |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — Potential for Token Lock if Custom Logic Were Present  *(Severity: Low · Status: Unresolved)*

While the provided code is a standard ERC20 implementation, any contract that holds tokens and does not include a mechanism for withdrawing arbitrary ERC20 tokens (e.g., a `recoverERC20` function) risks locking tokens sent to it mistakenly or from unsupported protocols. This is a general consideration for contracts holding assets.

**Recommendation:** For contracts intended to hold tokens, consider implementing a `recoverERC20` function, callable only by the owner, to retrieve accidentally sent or stuck tokens. This enhances operational flexibility (7.8 Operations) without compromising core functionality.


### `I-01` — Use of `pragma experimental ABIEncoderV2`  *(Severity: Informational · Status: Unresolved)*

The contract includes `pragma experimental ABIEncoderV2;`. While not a vulnerability, `ABIEncoderV2` has been standard since Solidity 0.8.0 and is typically not required to be explicitly enabled in 0.8.17. Its presence might indicate legacy code patterns or specific complex data structures not fully visible in the provided snippet.

**Recommendation:** Review if `ABIEncoderV2` is strictly necessary for the contract's functionality. If not, it can be removed to simplify the pragma declarations. This is a minor code quality point.


### `I-02` — Centralized Ownership  *(Severity: Informational · Status: Unresolved)*

The contract utilizes OpenZeppelin's `Ownable` pattern, which grants a single address (the owner) exclusive control over certain administrative functions (7.3 Access Control). This design introduces a single point of failure, as a compromise of the owner's private key could lead to unauthorized actions.

**Recommendation:** For enhanced security and decentralization, consider transitioning ownership to a multi-signature wallet (e.g., Gnosis Safe) or a robust governance mechanism. This mitigates the risk associated with a single point of failure.


### `I-03` — ERC20 `approve` Race Condition  *(Severity: Informational · Status: Unresolved)*

The ERC20 `approve` function is susceptible to a known race condition. If a user increases their allowance for a spender, a malicious actor could front-run this transaction, spend the original allowance, and then spend the newly increased allowance before the user's second transaction confirms. This is a characteristic of the ERC20 standard itself, as noted in the OpenZeppelin `IERC20` interface comments.

**Recommendation:** Educate users about this inherent ERC20 limitation. Recommend using `increaseAllowance` and `decreaseAllowance` functions (if implemented in the full ERC20 contract) or setting the allowance to zero before setting a new value to mitigate this risk. This is a user-side operational concern (7.8 Operations).

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xac1b...b2b4`](https://basescan.org/address/0xac1bd2486aaf3b5c0fc3fd868558b082a531b2b4) |
| **Network** | Base |
| **Price** | $0.0001104 |
| **24h Volume** | $39.2K |
| **Liquidity** | $972.4K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 38.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 758 buys / 411 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x4b0aaf3ebb163dd45f663b38b6d93f6093ebc2d3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/toshi-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-18*

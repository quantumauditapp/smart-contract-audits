---
token: Book of Ethereum
ticker: BOOE
network: ethereum
risk_score: 0
status: low
date: 2026-09-22
---

# Book of Ethereum (BOOE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/book-of-ethereum-eth)

---

## Audit Summary

The audit of the provided ERC20 token contract revealed critical vulnerabilities related to unchecked arithmetic operations within core token transfer and minting functions. These issues could lead to severe consequences, including token supply manipulation, incorrect user balances, and a broken token invariant. While the contract attempts to use OpenZeppelin's Ownable, the custom ERC20 implementation introduces significant risks.

> **Final Recommendation:** It is strongly recommended to replace the custom ERC20 implementation with a battle-tested and audited standard, such as OpenZeppelin's ERC20, to eliminate critical arithmetic vulnerabilities. If a custom implementation is necessary, all arithmetic operations must be carefully reviewed to ensure proper overflow/underflow handling, either by relying on Solidity 0.8+ default checks or by explicitly using `SafeMath` consistently. Additionally, ensure robust access control for minting and burning functions in the `BookOfEth` contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture is a custom ERC20 implementation, which deviates from battle-tested OpenZeppelin standards, introducing significant risk (7.1 Architecture). Critical code security flaws… |
| **Governance / Economics** | 10/10 | Low | The economic model of the token is a standard ERC20 with minting and burning capabilities. The primary economic risk stems from the critical technical vulnerabilities that could lead to arbitrary… |
| **Upgrades** | 10/10 | Low | The provided contract is a standard, non-upgradeable ERC20 token implementation. There are no proxy patterns or upgrade mechanisms implemented, which simplifies the upgrade safety analysis (7.7… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 99.7% — Null Address, TeamFinance |
| **Top-1 Unlocked Holder** | 0.3% |

## Security Findings

_🟡 3 Medium · ⚪ 1 Informational_

### `M-01` — Redundant SafeMath Library  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SafeMath` library is included in the contract, but the `ERC20` implementation directly uses native arithmetic operators, often within `unchecked` blocks, rather than calling `SafeMath` functions. In Solidity 0.8+, arithmetic operations automatically revert on overflow/underflow unless explicitly placed in an `unchecked` block. The presence of `SafeMath` without its use suggests a potential misunderstanding of Solidity's arithmetic safety features or an incomplete refactor, leading to unnecessary bytecode and potential confusion for future developers.

**Recommendation:** Either fully integrate `SafeMath` for all arithmetic operations (if targeting older Solidity versions or specific `unchecked` behavior is not desired) or remove the `SafeMath` library entirely if relying on Solidity 0.8+'s default overflow checks and `unchecked` blocks where appropriate. For Solidity 0.8+, it's generally recommended to rely on the default checks and only use `unchecked` for specific, proven-safe operations.


### `M-02` — Unchecked Arithmetic in Token Transfers and Minting  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_transfer` function uses `unchecked` blocks for `_balances[to] += amount;` and the `_mint` function uses `unchecked` for `_balances[account] += amount;`. This means that if `_balances[to]` or `_balances[account]` plus `amount` exceeds `type(uint256).max`, the value will wrap around to a small number instead of reverting. This can lead to incorrect user balances, token supply manipulation, and potential loss of funds for users or arbitrary token creation by an attacker if they can control the `amount` or `to` address in specific scenarios. This directly violates the integrity of the token's accounting.

**Recommendation:** Remove the `unchecked` blocks from addition operations in `_transfer` and `_mint` functions. Solidity 0.8+ by default checks for overflow/underflow, so removing `unchecked` will ensure these operations revert on overflow, maintaining token integrity. Alternatively, implement explicit overflow checks before the addition if `unchecked` is desired for gas optimization in other contexts.


### `M-03` — Inconsistent Unchecked Arithmetic for Total Supply  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `_mint` function, `_totalSupply += amount;` is *not* within an `unchecked` block, meaning it will revert on overflow. However, `_balances[account] += amount;` *is* within an `unchecked` block, meaning it will wrap around on overflow. This inconsistency can lead to a state where `_totalSupply` does not accurately reflect the sum of all token balances, breaking a fundamental invariant of ERC20 tokens. If `_balances[account]` overflows and wraps around while `_totalSupply` reverts, the token's accounting becomes corrupted, potentially leading to denial of service for minting or incorrect total supply reporting.

**Recommendation:** Ensure consistent arithmetic handling for `_totalSupply` and individual `_balances`. If `unchecked` is used for `_balances` additions, it should also be used for `_totalSupply` additions, or vice-versa. The safest approach is to remove `unchecked` for all additions, allowing Solidity's default overflow checks to protect both `_totalSupply` and `_balances`.


### `I-01` — Missing Context Contract Definition  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ERC20` contract inherits from `Context`, which provides the `_msgSender()` function. However, the source code for the `Context` contract was not provided in the audit scope. While it is highly probable that this refers to the standard OpenZeppelin `Context` contract, its absence means a full verification of its implementation and security cannot be performed.

**Recommendation:** For a complete audit, ensure all dependent contract source codes are provided. If using OpenZeppelin contracts, explicitly state the version used.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x289f...40a6`](https://etherscan.io/address/0x289ff00235d2b98b0145ff5d4435d3e92f9540a6) |
| **Network** | Ethereum |
| **Price** | $0.04184 |
| **24h Volume** | $56.3K |
| **Liquidity** | $553.7K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 35.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 92 buys / 71 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xdeba8fd61c1c87b6321a501ebb19e61e610421bf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/book-of-ethereum-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*

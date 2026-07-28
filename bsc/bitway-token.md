---
token: Bitway Token
ticker: BTW
network: bsc
risk_score: 54
status: high
date: 2026-07-27
---

# Bitway Token (BTW) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitway-token-bsc)

---

## Audit Summary

The BitwayToken contract implements an ERC20 token with custom transfer restrictions based on a timestamp and a whitelist. The contract utilizes OpenZeppelin's Ownable and ERC20Permit. A significant finding is the owner's ability to indefinitely extend the transfer lockup period, posing a high centralization risk. Other findings include a nuanced whitelist application for minting vs. burning, and minor code quality issues. The owner is a multisig, which is a positive security practice for critical operations.

> **Final Recommendation:** It is strongly recommended to address the high-severity issue regarding the owner's ability to indefinitely extend the transfer lockup period. This could involve redesigning the `setTransferAllowedTimestamp` function to ensure the `ETA` mechanism consistently limits the owner's power, or by implementing a timelock for such critical changes. Additionally, clearly document the whitelist behavior for minting and burning to manage user expectations. Consider removing unused imports to streamline the codebase.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The BitwayToken contract is built upon well-audited OpenZeppelin libraries (ERC20, Ownable, ERC20Permit), which contributes to a solid foundation (7.2 Code Security). The custom `_update` logic… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of centralization, with the owner having significant control over token transferability (7.3 Access Control). Specifically, the owner can indefinitely extend the… |
| **Upgrades** | 6/10 | Medium | The BitwayToken contract is not designed with an upgrade mechanism (7.7 Upgrades). This means its logic is immutable once deployed, eliminating risks associated with proxy patterns or upgradeability… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Owner Can Indefinitely Extend Transfer Lockup Period  *(Severity: High · Status: Unresolved)*

The `setTransferAllowedTimestamp` function's logic for `ETA` (Estimated Time of Arrival) does not consistently restrict the owner's ability to extend the `transferAllowedTimestamp`. If the current `transferAllowedTimestamp` is still in the future (`transferAllowedTimestamp > block.timestamp`), the owner can set a `newTimestamp` arbitrarily far into the future without any `ETA` constraint. This allows the owner to indefinitely postpone the lifting of transfer restrictions for non-whitelisted users, effectively freezing token liquidity at will.

**Recommendation:** Modify the `setTransferAllowedTimestamp` function to ensure that the `ETA` mechanism or a similar constraint applies consistently, regardless of whether the current `transferAllowedTimestamp` is in the past or future. For example, always enforce a maximum extension period or introduce a timelock for changes that extend the lockup. Consider a governance mechanism or a fixed, non-extendable lockup period if decentralization is a goal.


### `M-01` — Inconsistent Whitelist Application for Minting and Burning  *(Severity: Medium · Status: Unresolved)*

The `_update` function, which enforces the transfer lockup and whitelist, contains a conditional check: `if (from != address(0)) { require(whitelist[from], "Not allowed"); }`. This means that when `from` is `address(0)` (as in `_mint` operations), the whitelist check is bypassed. However, for `burn` operations, where `from` is `_msgSender()`, the whitelist check *is* applied. This design choice means that during the restricted period, tokens can be minted to any address, but burning tokens requires the burner to be whitelisted. While potentially intentional, this inconsistency could lead to user confusion or unexpected behavior if not clearly documented.

**Recommendation:** Clearly document the specific behavior of the whitelist for both minting and burning operations in the contract's NatSpec and external documentation. If this behavior is not intentional, adjust the `_update` logic to apply the whitelist consistently or as desired for all `from` addresses, or consider if `burn` should also bypass the whitelist if `_mint` does.


### `L-01` — Unused OpenZeppelin Pausable Import  *(Severity: Low · Status: Unresolved)*

The `Pausable` contract from OpenZeppelin is imported in `BitwayToken.sol` but is not inherited or used anywhere within the contract. This results in unnecessary code being included in the contract's dependencies.

**Recommendation:** Remove the unused `import {Pausable} from "@openzeppelin/contracts/utils/Pausable.sol";` statement to reduce contract size and improve code clarity.


### `I-01` — Complex and Potentially Misleading ETA Logic  *(Severity: Informational · Status: Unresolved)*

The `ETA` (Estimated Time of Arrival) logic within the `setTransferAllowedTimestamp` function is somewhat complex, involving conditional checks based on `transferAllowedTimestamp > block.timestamp` and `ETA == 0`. This complexity, combined with the high-severity issue of potential bypass, makes the function harder to reason about and increases the risk of misinterpretation or future vulnerabilities.

**Recommendation:** Refactor the `setTransferAllowedTimestamp` function to simplify the `ETA` logic. Consider using clearer variable names, adding comments to explain complex conditions, or breaking down the logic into smaller, more manageable parts. Ensure the intended behavior of `ETA` is explicitly and unambiguously enforced.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4440...acaa`](https://bscscan.com/address/0x444045b0ee1ee319a660a5e3d604ca0ffa35acaa) |
| **Network** | BNB Chain |
| **Price** | $0.09705 |
| **24h Volume** | $160.0K |
| **Liquidity** | $30.2K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 98.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 908 buys / 653 sells |

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

## Frequently Asked Questions

### Is Bitway Token a scam?

Based on automated analysis, Bitway Token scores 61/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Bitway Token safe to buy?

Our scanner flagged a risk score of 61/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Bitway Token been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x94a177b18c83123e6b6202191dcdd092e5638fcb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bitway-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*

---
token: Upscreener
ticker: UPS
network: bsc
risk_score: 3
status: low
date: 2026-10-11
---

# Upscreener (UPS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 3/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/upscreener-bsc)

---

## Audit Summary

The UpscreenerToken contract is an ERC-20 token implementation. A key security characteristic is that the contract's ownership has been renounced on-chain. This means all functions previously restricted to the owner are now permanently disabled, including those that could modify transfer fees, limits, or initiate token swaps. While some minor historical code patterns were identified, they are within these dormant functions and pose no active risk.

> **Final Recommendation:** The UpscreenerToken contract exhibits a strong security posture primarily due to its renounced ownership, which has permanently disabled all privileged administrative and economic control functions. Token holders can be confident that parameters such as transfer fees and limits cannot be altered. While a minor rounding issue was identified in a dormant internal function, it poses no active threat. For future contract development, always prioritize multiplication before division to prevent potential rounding errors, and ensure comprehensive testing of all mathematical operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The UpscreenerToken contract implements the ERC-20 standard with a ReentrancyGuard, demonstrating a solid foundation for token operations (7.1 Architecture). The core transfer logic (`_transfer`) is… |
| **Governance / Economics** | 10/10 | Low | A significant strength of the UpscreenerToken contract is its renounced ownership (7.3 Access Control). This means that all privileged functions, such as `setTaxes`, `setShares`, `setSwapEnabled`… |
| **Upgrades** | 10/10 | Low | The UpscreenerToken contract is a standard, non-upgradeable ERC-20 implementation (7.7 Upgrades). There are no proxy patterns or upgrade mechanisms present, which simplifies the contract's lifecycle… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 28.0% |
| **LP Locked** | 98.9% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.0% |

## Security Findings

_🟢 1 Low · ⚪ 8 Informational_

### `CD-01` — Minor Rounding Loss in Dormant Internal Distribution  *(Severity: Low · Status: Unresolved)*

The internal `_swapAndDistribute` function, which handles the distribution of tokens, performs a division operation before a multiplication. This common Solidity pattern can lead to very small, negligible rounding losses during calculations. However, this function is only callable indirectly via `manualDistribute`, which is an owner-restricted function. Since ownership is renounced, this function is dormant and cannot be executed, meaning this potential rounding loss poses no active risk.

**Recommendation:** While this issue is currently inactive due to renounced ownership, for future smart contract development, it is a best practice to perform multiplication operations before division to minimize potential rounding errors and ensure maximum precision in calculations.


### `CP-05` — Dormant Control Over Transfer Switches  *(Severity: Informational · Status: Unresolved)*

The contract previously contained functions like `setSwapEnabled` and `manualDistribute` that could enable or disable certain transfer mechanisms or initiate internal token swaps. However, because the contract's ownership has been permanently renounced, these functions are now inactive and cannot be called by anyone, meaning they pose no current risk to token transfers.

**Recommendation:** No action is required for token holders, as the renounced ownership ensures these control switches are permanently disabled and cannot be manipulated.


### `CP-07` — Dormant Control Over Transfer Fees  *(Severity: Informational · Status: Unresolved)*

Functions such as `setTaxes` and `setShares` were designed to allow the contract owner to adjust the fees applied to token transfers. With the contract's ownership renounced, these functions are now permanently disabled. This means that the current transfer fees are fixed and cannot be changed by any external party.

**Recommendation:** No action is required for token holders, as the renounced ownership ensures that transfer fees cannot be altered.


### `CP-08` — Dormant Control Over Transfer and Wallet Limits  *(Severity: Informational · Status: Unresolved)*

The contract included functions like `setSwapThreshold` and `setMaxSwapAmount` which could modify limits on how many tokens could be swapped or transferred at once. Since ownership is renounced, these limits are now fixed and cannot be changed by any external party, providing stability to the token's operational parameters.

**Recommendation:** No action is required for token holders, as the renounced ownership ensures these limits are permanently fixed and cannot be changed.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 75.3% of supply. Of that, 50.0% burned, 9.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.4% in wallets, 3.6% in other contracts. 8,781 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Upscreener (UPS), rank #4996. 8,781 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

98.9% of the pool's LP is burned or time-locked. 28.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 70.9% is locked in PinkLock02 until 04 Apr 2027 (175 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 1.0% is held, unlocked, by the token's owner/deployer (0x49bf…48e2) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $81K (DexScreener, all pools). 24h trading volume $44K (CoinGecko, all markets, daily snapshot). 24h trading volume $49K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $81K of DEX liquidity across 4 pools. Launch: 190 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xae5a...ba01`](https://bscscan.com/address/0xae5a409773b9a7dd0ae94ff437ac213d8fafba01) |
| **Network** | BNB Chain |
| **Price** | $0.044 |
| **24h Volume** | $48.5K |
| **Liquidity** | $80.7K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 75.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 595 buys / 606 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc17236ba8107de131a6a7e380cf857fae9696919)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/upscreener-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*

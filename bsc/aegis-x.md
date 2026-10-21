---
token: AEGIS X
ticker: AGX
network: bsc
risk_score: 57
status: medium
date: 2026-09-15
---

# AEGIS X (AGX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aegis-x-bsc)

---

## Audit Summary

The AegisXToken contract implements an ERC20 token with advanced defense mechanisms against price drops and large sell-offs, including dynamic sell taxes and a crash fuse. The contract leverages OpenZeppelin libraries for standard functionalities and access control. While the architecture incorporates several protective features, a critical vulnerability related to oracle manipulation from the PancakeSwap V2 pair was identified, which could undermine the core defense mechanisms. Additionally, significant centralization of control and potential economic instability due to high defense taxes pose considerable risks.

> **Final Recommendation:** Prioritize the implementation of a robust, decentralized oracle solution to replace the current spot price feed from PancakeSwap V2, as this is a critical vulnerability that undermines the protocol's core defense mechanisms. Strengthen governance by considering timelocks for critical parameter changes and ensuring the `governance` address is controlled by a secure, transparent, and resilient entity. Thoroughly model the economic impact of the high defense tax to ensure it achieves its intended effect without inadvertently destabilizing the token's market dynamics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract demonstrates a structured approach, utilizing OpenZeppelin libraries for ERC20 and Ownable functionalities (7.1 Architecture). The custom `_update` logic for transfers involving the… |
| **Governance / Economics** | 5/10 | Medium | The protocol's access control is managed by an `owner` (a 20/32 multisig) and a `governance` address, with the `owner` able to set the `governance` (7.3 Access Control). The `governance` role holds… |
| **Upgrades** | 4/10 | Medium | The contract is not designed as an upgradeable proxy (7.7 Upgrades). This eliminates risks associated with upgradeability patterns, such as proxy implementation mismatches or storage collisions.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Critical: Oracle Manipulation via Spot Price from AMM  *(Severity: Critical · Status: Unresolved)*

The contract relies on `IPancakePair.getReserves()` to determine the token's price and pool reserves in functions like `_getPoolPrice()`, `_poolReserves()`, `_snapshotPrice()`, `_checkDefenseFuse()`, and `_recordBlockSell()`. Spot prices from AMM pairs are highly susceptible to manipulation within a single block using flash loans or large swaps. An attacker could temporarily skew the reported price or reserves to bypass high sell taxes, trigger defense mechanisms incorrectly, or manipulate the `snapshotPrice` to their advantage, leading to significant financial loss or protocol instability.

**Recommendation:** Implement a time-weighted average price (TWAP) oracle or integrate with a robust, decentralized oracle solution (e.g., Chainlink) that aggregates data from multiple sources and is resistant to single-block manipulations. This is crucial for all price-sensitive operations, especially those triggering defense mechanisms or calculating taxes.


### `H-01` — High: Centralized Control over Critical Parameters  *(Severity: High · Status: Unresolved)*

The `governance` address has extensive control over critical protocol parameters, including `sellRatio`, `extraSellBP`, `crashThresholdBP`, `feeReceiver`, `rbs`, `transferStatus`, and the ability to whitelist addresses. While the `owner` (a 20/32 multisig) can update the `governance` address, the `governance` role itself, if compromised or misused, could severely impact the protocol's integrity and user funds. This high degree of centralization introduces a single point of failure for operational security.

**Recommendation:** Ensure the `governance` address is controlled by a robust, multi-signature wallet with a high threshold or a well-designed decentralized autonomous organization (DAO). Consider implementing timelocks for changes to critical parameters to provide transparency and allow community review before changes become effective, mitigating risks from hasty or malicious actions.


### `M-01` — Medium: Economic Instability Risk from High Defense Tax  *(Severity: Medium · Status: Unresolved)*

The `extraSellBP` is set to 3000 (30%), which is applied as a sell tax when the `crashFuseActive` or `blockSellLimitExceeded` conditions are met. While intended as a defense mechanism against rapid price depreciation, such a high tax can create strong disincentives for legitimate sellers. This could exacerbate sell-offs during periods of stress, potentially leading to a 'death spiral' where users rush to sell before the tax applies, or avoid selling into the pool entirely, undermining the token's liquidity and stability.

**Recommendation:** Conduct thorough economic modeling and simulations to assess the impact of the 30% `extraSellBP` under various market conditions. Consider if this magnitude of tax is sustainable or if it might lead to unintended adverse user behavior. Explore alternative or dynamically adjustable tax mechanisms that provide defense without excessively penalizing legitimate market activity.


### `L-01` — Low: Whitelist Bypass for DEAD Address During Disabled Transfers  *(Severity: Low · Status: Unresolved)*

In the `_update` function, when `_from == targetPool` (a buy from the pool), the condition `if (!transferStatus && (_to != DEAD && !whitelist[_to])) revert Disabled();` allows transfers to the `DEAD` address even if `transferStatus` is `false` and the recipient is not whitelisted. While `DEAD` is a burn address, this specific bypass means tokens can always be burned from the pool, even when other transfers are intentionally restricted. This might not align with the intended behavior of a 'disabled' transfer state.

**Recommendation:** Clarify if allowing transfers to the `DEAD` address when `transferStatus` is `false` is an intended feature. If not, consider removing the `_to != DEAD` condition from the `revert Disabled()` check to ensure consistency with the `transferStatus` setting.


### `I-01` — Informational: Lack of Comprehensive Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

The contract lacks a general emergency pause mechanism that could halt all transfers or critical functions. The existing `transferStatus` only affects buys from the `targetPool` for non-whitelisted users. In the event of an unforeseen vulnerability or exploit affecting other parts of the contract, the `governance` or `owner` would not have a direct, immediate way to halt all operations to prevent further damage or drain of funds.

**Recommendation:** Consider implementing a more comprehensive pause mechanism, such as inheriting from OpenZeppelin's `Pausable` contract. This would allow the `governance` or a designated emergency role to temporarily halt critical operations in an emergency, providing a crucial safety switch for unforeseen circumstances.


### `I-02` — Informational: Zero Cooldown for Price Snapshot  *(Severity: Informational · Status: Unresolved)*

The `BALANCE_COOLDOWN_SECONDS` constant is set to `0`, which means the `_snapshotPrice()` function can be called in consecutive blocks without any delay. While this might be intentional for immediate price updates, it could potentially allow an attacker to quickly re-snapshot a manipulated price if they can control the timing of calls to this function, especially in conjunction with a flash loan attack.

**Recommendation:** Review the rationale for setting `BALANCE_COOLDOWN_SECONDS` to `0`. If `_snapshotPrice()` is critical for defense mechanisms, consider introducing a short, non-zero cooldown period. While this wouldn't fully mitigate flash loan attacks, it could make rapid, repeated manipulation attempts more difficult or costly for an attacker.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe766...a077`](https://bscscan.com/address/0xe766023f5a0fa6ce91b9f98d327771437dfca077) |
| **Network** | BNB Chain |
| **Price** | $55.0790 |
| **24h Volume** | $3.05M |
| **Liquidity** | $49.59M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 99.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6030 buys / 3382 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x73ee72b8cc2c7ea032d8051e1cfa740a2db84331)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aegis-x-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*

---
token: 币安人
ticker: 币安人
network: bsc
risk_score: 52
status: medium
date: 2026-10-31
---

# 币安人 (币安人) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-8246d3-bsc)

---

## Audit Summary

The BinanceHumanToken is a standard ERC-20 implementation with added administrative controls. The contract allows a designated 'minter' address to mint new tokens, block specific addresses from transferring, and toggle global transfer restrictions. While the core ERC-20 logic is standard, the centralization of power in the 'minter' role introduces significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the 'minter' role possesses significant power to dilute supply and restrict liquidity. It is strongly recommended to transition the 'minter' role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key.

Additionally, consider implementing a timelock mechanism for sensitive administrative functions like 'setPoolBlocked' or 'mint' to provide transparency and a window for the community to react to significant changes in token economics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC-20 logic, ensuring reliable token transfers and allowance management. 7.1 Architecture is modular, separating administrative logic from standard… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the 'minter' role. The minter can arbitrarily increase the total supply, which directly impacts the value of existing holdings.… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, with the contract logic being immutable post-deployment. This eliminates risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.7% (≈ permanent lock) |
| **LP Locked** | 99.7% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'minter' address has the authority to call the mint() function, which creates new tokens and increases the total supply. This action dilutes the value of existing tokens held by all users.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or a governance-controlled contract to prevent unilateral supply inflation.


### `CP-05` — Global Transfer Control Switch  *(Severity: Medium · Status: Unresolved)*

The 'minter' can call disableBlocks() to toggle a global switch that impacts transfer functionality. This allows the administrator to halt all token movements or sales at their discretion.

**Recommendation:** Remove the global transfer switch or implement a timelock to ensure that any decision to halt trading is transparent and community-approved.


### `CP-06` — Address Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The 'minter' can use setPoolBlocked() to add specific addresses to a blacklist. Blacklisted addresses are prevented from transferring or selling their tokens, effectively freezing their assets.

**Recommendation:** Limit the use of blacklisting to specific, well-defined regulatory requirements and ensure the process is transparent and auditable.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 35.9% of supply. Of that, 22.0% burned, 7.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.6% in wallets, 1.3% in other contracts. 3,443 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,443 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.7% of the pool's LP is burned or time-locked. 99.7% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.3% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $122K (DexScreener, all pools). 24h trading volume $2.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $122K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x039d...806f`](https://bscscan.com/address/0x039de4c967d71a05d308f8dd4b1fd4330973806f) |
| **Network** | BNB Chain |
| **Price** | $0.00000081 |
| **24h Volume** | $2.23M |
| **Liquidity** | $122.1K |
| **Volume / Liquidity** | 18.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 35.9% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 14329 buys / 13153 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xf7f7ccedaeb1fb131e2b5bb0790b51b5ad3b1260)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-8246d3-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*

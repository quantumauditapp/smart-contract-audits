---
token: YFI
ticker: YFI
network: bsc
risk_score: 44
status: medium
date: 2026-11-05
---

# YFI (YFI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yfi-bsc)

---

## Audit Summary

The YFI contract implements a custom minting mechanism tied to Binance Agent IDs and automated liquidity provision. While ownership has been renounced, the contract contains centralized control mechanisms over trading status that were active during the minting phase. The architecture is standard for a liquidity-bootstrapping token, though it lacks standard ERC-20 metadata functions.

> **Final Recommendation:** The protocol is currently in a stable, immutable state due to the renouncement of ownership. Users should be aware that the lack of standard ERC-20 functions (totalSupply, balanceOf) may prevent the token from displaying correctly in standard wallets or interacting with some DeFi protocols. No further action is required for the current contract state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a custom minting flow that interacts with PancakeSwap routers to automate liquidity. 7.1 Architecture is centralized around a minting phase, 7.2 Code Security is standard for… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic parameters are fixed by the minting logic and the hardcoded liquidity provision. 7.5 Governance is effectively non-existent as ownership has been renounced. The economic model relies on… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy and lacks upgradeability patterns. The logic is immutable, ensuring that the current transfer rules cannot be altered post-renouncement.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 97.8% (≈ permanent lock) |
| **LP Locked** | 97.8% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CP-05` — Centralized Control Over Trading Status  *(Severity: Medium · Status: Unresolved)*

The contract contains a 'tradingOpen' switch that dictates whether token transfers are permitted. This switch could be toggled by the owner via 'openTradingEarly' or automatically upon reaching the minting limit in the 'receive' function. While ownership is now renounced, this mechanism represents a centralized point of failure during the initial deployment phase.

**Recommendation:** Since ownership is renounced, this risk is mitigated. For future deployments, ensure that trading is enabled automatically or via a decentralized mechanism to avoid reliance on a single privileged address.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 27.9% of supply. Of that, 14.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.3% in wallets, 2.4% in other contracts. 305 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

305 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

97.8% of the pool's LP is burned or time-locked. 97.8% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 2.2% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $229K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $11K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0f93...b190`](https://bscscan.com/address/0x0f93636f10fbb4820f2c2f241d167c287041b190) |
| **Network** | BNB Chain |
| **Price** | $32.5000 |
| **24h Volume** | $229.3K |
| **Liquidity** | $10.6K |
| **Volume / Liquidity** | 21.6× |
| **Token Age** | 22h |
| **Top-10 Holders** | 27.9% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 3002 buys / 2287 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5645958d3b60af8a666702557cb485709d9cdc5c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yfi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*

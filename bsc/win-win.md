---
token: Win-win
ticker: WIN-WIN
network: bsc
risk_score: 84
status: high
date: 2026-11-03
---

# Win-win (WIN-WIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/win-win-bsc)

---

## Audit Summary

PandaToken is a dividend-bearing token with complex fee and reward distribution logic. While ownership has been renounced, preventing further administrative changes, the contract contains critical vulnerabilities regarding asset recovery and potential unauthorized fund movement. The architecture relies on internal self-calls to manage state, which increases complexity and potential for logic errors.

> **Final Recommendation:** The protocol should immediately address the critical and high-severity findings related to asset recovery and unauthorized token movement. Given that ownership is renounced, these functions cannot be disabled or patched, posing a permanent risk to the contract's treasury.

Users should exercise extreme caution as the current implementation allows for the potential drainage of assets through the recovery functions. Future iterations should remove arbitrary asset recovery capabilities and implement strictly defined, non-custodial reward mechanisms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a standard ERC-20 interface with custom tax and reward logic. 7.1 Architecture: The design uses a complex reward distribution system with internal batch processing. 7.2 Code… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The token utilizes buy/sell taxes and dividend distribution. 7.5 Governance: Ownership is renounced, meaning no further changes to economic parameters can be made. The protocol is now… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract is not upgradeable. 7.8 Operations: Operational risk is minimized by the renounced ownership, preventing rug-pulls via administrative functions. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 9 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The functions _pullSwapCurrency and settleRewardAccount utilize transferFrom to move tokens from arbitrary addresses. This allows the contract to pull tokens from any user who has previously approved the contract, potentially leading to unauthorized fund depletion.

**Recommendation:** Restrict token movement to only those funds explicitly owned by the contract or authorized via a secure, limited-scope allowance mechanism.


### `CD-02` — Arbitrary ETH/Asset Transfer  *(Severity: High · Status: Unresolved)*

The _recoverAsset function allows for the transfer of arbitrary tokens to an address influenced by the caller. Since this function is reachable by non-privileged users, it poses a significant risk of asset theft.

**Recommendation:** Remove the _recoverAsset function or restrict it to a multi-signature wallet or a time-locked governance contract.


### `CP-05` — Dormant Transfer Switch  *(Severity: Informational · Status: Unresolved)*

The contract contains switches (inSwap, processingRewards) that control transfer logic. These were previously controlled by the owner, but since ownership is renounced, these settings are now effectively locked in their current state.

**Recommendation:** No action required as ownership is renounced, but verify that the current state is optimal for long-term operation.


### `CP-07` — Dormant Fee Configuration  *(Severity: Informational · Status: Unresolved)*

Functions like completeCustoms allow for the modification of transaction fees. These functions are now inaccessible due to the renouncement of ownership.

**Recommendation:** None; the immutability of these fees is now guaranteed by the renounced ownership.


### `CP-08` — Dormant Limit Configuration  *(Severity: Informational · Status: Unresolved)*

Various functions control transaction and wallet limits. These are now locked and cannot be modified by any address.

**Recommendation:** None; the immutability of these limits is now guaranteed by the renounced ownership.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 13.0% of supply. Of that, 11.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.5% in wallets, 1.6% in other contracts. 15,079 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

15,079 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 13 Nov 2026 (10 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $228K (DexScreener, all pools). 24h trading volume $3.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4% on sell. Market: $228K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2ff0...6c49`](https://bscscan.com/address/0x2ff0fdfff7ff9867e92dbb7f242258cb68fb6c49) |
| **Network** | BNB Chain |
| **Price** | $0.09507 |
| **24h Volume** | $3.69M |
| **Liquidity** | $227.7K |
| **Volume / Liquidity** | 16.2× |
| **Token Age** | 13h |
| **Top-10 Holders** | 13.0% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 19085 buys / 17305 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0bad163253d6bb3c9292060d94627a7d4189aae7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/win-win-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

---
token: launch cat
ticker: LAUNCHCAT
network: solana
risk_score: 22
status: low
date: 2026-10-25
---

# launch cat (LAUNCHCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/launch-cat-sol)

---

## Audit Summary

The LAUNCHCAT token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. However, the token is flagged as high-risk by a third-party registry due to the creator's history of rug-pulling, and the trading volume exhibits strong indicators of wash trading. Holder concentration data is unavailable, and metadata remains mutable.

> **Final Recommendation:** Investors should exercise extreme caution due to the third-party registry risk flag regarding the developer's history. Monitor the token's metadata for unexpected changes and verify that the liquidity remains locked in the specified on-chain vault.

Before interacting, verify the current metadata state on-chain and cross-reference the token's performance against historical volume trends to identify potential artificial trading activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply stability and preventing account freezing (7.3 Access Control).… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully locked in a DEX locker, preventing creator withdrawal (7.4 Economic). However, the volume-to-liquidity ratio of 40.45 suggests significant wash trading (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The token metadata is currently mutable, allowing for potential changes to the name or symbol (7.7 Upgrades). There are no upgradeable transfer hooks or fees (7.7 Upgrades). The mint and freeze… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · ⚪ 6 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history.

**Recommendation:** Do not interact with this token.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume is 40.45x the liquidity, a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for potential liquidity manipulation when evaluating market depth.


### `H-02` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $27,978. Slippage will be severe for large positions.

**Recommendation:** Avoid large trades that may result in significant price impact.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $37K of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4yzkM1...QxXx`](https://solscan.io/account/4yzkM1ts8avWd1EXDcayWWWxu8oEKVBECRAT8qNnQxXx) |
| **Network** | Solana |
| **Price** | $0.0001521 |
| **24h Volume** | $1.09M |
| **Liquidity** | $35.2K |
| **Volume / Liquidity** | 31.1× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10246 buys / 7369 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/hjluvfnu7q4wvsacubm7ezhkh887ktaytg71hnrh9pg3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/launch-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*

---
token: Daisuke-Doo
ticker: DAISUKE
network: solana
risk_score: 38
status: medium
date: 2026-11-02
---

# Daisuke-Doo (DAISUKE) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/daisuke-doo-sol)

---

## Audit Summary

The Daisuke-Doo token utilizes the Token-2022 program with all administrative authorities revoked, preventing minting or freezing of assets. The primary risks identified are very low liquidity and a high volume-to-liquidity ratio, which suggests potential wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Potential participants should exercise caution due to the low liquidity environment, which may lead to significant slippage during trades. Monitor the token's trading volume relative to liquidity to avoid interacting with artificially inflated markets.

Verify that no future extensions are added by checking the mint account state on-chain. Given the lack of holder distribution data, avoid large market orders that could be impacted by low depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the spl-token-2022 program. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic factors show high risk due to $5,122 in liquidity. 7.6 External data indicates a volume/liquidity ratio of 74.24, signaling potential wash trading. 7.5 Governance is decentralized as… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not support proxy-style logic. Metadata is immutable, and no upgradable extensions are configured, ensuring long-term state consistency. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $5,122. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth before executing large trades.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 74.24x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as trading activity may not reflect organic market demand.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $386K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 5 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3oEMST...pump`](https://solscan.io/account/3oEMST7PYBrJs6KcXddeuqaSsLYs8qZpEPWaUGdgpump) |
| **Network** | Solana |
| **Price** | $0.00001863 |
| **24h Volume** | $348.0K |
| **Liquidity** | $9.9K |
| **Volume / Liquidity** | 35.1× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5751 buys / 4231 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9tp11219nwqfaghqnoyk8aigewj8grddkqx41bikvpku)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/daisuke-doo-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*

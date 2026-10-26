---
token: frog lord
ticker: FROG
network: solana
risk_score: 29
status: low
date: 2026-10-26
---

# frog lord (FROG) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/frog-lord-sol)

---

## Audit Summary

The frog lord (FROG) token is a standard SPL-2022 mint with both mint and freeze authorities successfully revoked. The primary risks identified are the mutable metadata and a high volume-to-liquidity ratio suggesting potential wash trading. All third-party risk registry data was available and reported no adverse flags.

> **Final Recommendation:** Investors should monitor the token's metadata for unexpected changes given its mutable status. Due to the high volume-to-liquidity ratio, users should exercise caution regarding potential price volatility and artificial trading volume.

Verify the current metadata state via a block explorer to ensure branding matches expectations. Given the lack of mint/freeze authorities, the supply and transfer mechanics are immutable, providing a baseline level of security for holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program. 7.1 Architecture is standard, with no transfer hooks or permanent delegates configured. 7.3 Access Control is robust as both mint and freeze authorities… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows 45.67% concentration among the top 10 holders. 7.6 External market data indicates a volume/liquidity ratio of 25.66, which is a high signal for wash trading. Liquidity is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints, but 7.5 Governance is impacted by the metadata mutability. The token metadata is currently mutable, allowing for potential branding changes. No other… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Raydium Lock |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 7 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 25.66, which exceeds the 20x threshold, indicating potential wash trading activity.

**Recommendation:** Exercise caution when trading; volume may not reflect genuine market demand.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the original creator.

**Recommendation:** Verify metadata against official sources before interacting with the token.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.7% of supply. Of that, 23.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.0% in wallets, 0.0% in other contracts. 373 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

373 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $345K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (frog). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7tRWoX...nveW`](https://solscan.io/account/7tRWoXAnFchdqtXLiVeZpqQU4WuiJJSdRy1isLPJnveW) |
| **Network** | Solana |
| **Price** | $0.00002961 |
| **24h Volume** | $344.7K |
| **Liquidity** | $15.1K |
| **Volume / Liquidity** | 22.8× |
| **Token Age** | 16h |
| **Top-10 Holders** | 45.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3647 buys / 2964 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cs3jw39zavgvxomx9jzvavedhhwkxvml5nfdrsswexvp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/frog-lord-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*

---
token: Elon Coin
ticker: ELON
network: solana
risk_score: 21
status: low
date: 2026-11-07
---

# Elon Coin (ELON) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/elon-coin-sol-2066)

---

## Audit Summary

Elon Coin is a standard SPL token with both mint and freeze authorities successfully revoked. The project exhibits high trading volume relative to liquidity, though the majority of liquidity is permanently locked. Holder distribution data is currently unavailable, and metadata remains mutable.

> **Final Recommendation:** Monitor the token metadata for any unexpected changes given the mutable status. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity and slippage during high-volume periods.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control). The… |
| **Governance / Economics** | 7/10 | Low | Liquidity is robustly managed with 99.9% of the pool permanently locked (7.4 Economic). The volume/liquidity ratio of 18.27 indicates active trading, though holder concentration data is unavailable… |
| **Upgrades** | 10/10 | Low | The token metadata is currently mutable, allowing for potential changes to the name or symbol (7.7 Upgrades). No other upgradeable parameters exist for this mint (7.6 External). Users should verify… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the owner at any time.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.8% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 0.2% is held, unlocked, by 1 address(es) other than the pool's creator.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $35K (DexScreener, all pools). 24h trading volume $719K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (elon). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $35K of DEX liquidity across 2 pools. Launch: 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7ijABd...BAGS`](https://solscan.io/account/7ijABdKd6FP9ptZpTBhYeJRGPB9C2HczYqVUd7HEBAGS) |
| **Network** | Solana |
| **Price** | $0.000175 |
| **24h Volume** | $699.7K |
| **Liquidity** | $34.5K |
| **Volume / Liquidity** | 20.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6008 buys / 4109 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5mnjv5kzqqwe54h263fimjwugt8tcukadrxkxewzsmsd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/elon-coin-sol-2066)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*

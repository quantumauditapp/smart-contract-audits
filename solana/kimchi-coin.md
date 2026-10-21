---
token: Kimchi Coin
ticker: KIMCHI
network: solana
risk_score: 13
status: low
date: 2026-10-21
---

# Kimchi Coin (KIMCHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kimchi-coin-sol)

---

## Audit Summary

Kimchi Coin is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong baseline security for token supply and transferability. However, the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, and third-party registry data indicates high holder correlation. Holder distribution data was unavailable for this analysis.

> **Final Recommendation:** Investors should monitor the token's trading activity, as the high volume-to-liquidity ratio may indicate artificial market activity. Verify the current holder distribution via block explorers to ensure that the high holder correlation flagged by third-party registries does not pose a systemic risk to liquidity.

Perform independent checks on the mint address to confirm that authority revocation remains in effect. Avoid relying on high-volume metrics as a proxy for organic demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the SPL program… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by 100% of liquidity being burned, preventing pool creator withdrawal. 7.6 External signals indicate a volume-to-liquidity ratio of 26.00, which exceeds the 20.0… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is a fixed-program SPL asset. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is static and cannot be altered by… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 26.00, which exceeds the 20.0 threshold, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting trading volume as a sign of organic interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $287K (DexScreener, all pools). 24h trading volume $7.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $287K of DEX liquidity across 6 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7thgKg...pump`](https://solscan.io/account/7thgKgtK1rp1UtLpWUZEuu9vakedTMoZzuyps6RGpump) |
| **Network** | Solana |
| **Price** | $0.009589 |
| **24h Volume** | $7.74M |
| **Liquidity** | $287.2K |
| **Volume / Liquidity** | 27.0× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 58769 buys / 23972 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ayq1hkkkq6oitjcnbdeyuo9ahho6flaxjuybmlbvvpzd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kimchi-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

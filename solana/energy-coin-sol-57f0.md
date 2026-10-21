---
token: Energy Coin
ticker: ENERGY
network: solana
risk_score: 56
status: medium
date: 2026-10-21
---

# Energy Coin (ENERGY) — Smart Contract Security Analysis | Solana

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/energy-coin-sol-57f0)

---

## Audit Summary

Energy Coin is a Token-2022 asset with revoked mint and freeze authorities, mitigating primary centralization risks. However, the token exhibits high holder concentration, suspicious trading volume, and is flagged as a copycat by third-party registries. All liquidity is locked, providing a stable foundation for trading despite the high-risk market signals.

> **Final Recommendation:** Investors should exercise caution due to the high holder concentration and suspicious volume-to-liquidity ratio, which are indicative of artificial market activity. Verify the token metadata on-chain to ensure it matches the expected branding, as the mutable metadata flag allows for post-launch changes.

Monitor the top 10 holder wallets for coordinated sell-offs, as their combined 80% stake poses a significant risk to price stability. Given the 'copycat' classification from third-party registries, perform independent due diligence on the project's legitimacy before committing capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control (7.3) is robust as both mint and freeze authorities are revoked. The contract includes a 100 bps transfer fee (7.4… |
| **Governance / Economics** | 7/10 | Low | Holder concentration (7.4) is high, with the top 10 holders controlling 80.01% of the supply. Trading activity shows a volume/liquidity ratio of 34.66, suggesting potential wash trading (7.6… |
| **Upgrades** | 8/10 | Low | The token metadata is mutable (7.8), allowing for potential branding changes. While the transfer fee is upgradable (7.7), the transfer hook is not. There are no upgradeable proxy patterns as this is… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟠 3 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell control 80.01% of the total supply. Coordinated sell-offs by these entities could result in extreme price volatility.

**Recommendation:** Monitor top holder wallet activity for signs of distribution or coordinated dumping.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 34.66, which exceeds the 20x threshold, indicating potentially artificial trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics as a sign of organic interest.


### `H-03` — Flagged High-Risk by Third-Party Registry  *(Severity: High · Status: Unresolved)*

The token is classified as a 'Copycat' by an independent third-party risk registry.

**Recommendation:** Verify the project's authenticity against official channels.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the authority at any time.

**Recommendation:** Verify metadata against official project sources before interacting.


### `L-01` — Upgradable Transfer Fee  *(Severity: Low · Status: Unresolved)*

The transfer fee of 100 bps is currently set but remains upgradable, allowing for potential future adjustments to the fee structure.

**Recommendation:** Monitor for changes in transfer fee parameters via on-chain events.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.0% of supply. What remains: 25.5% in wallets, 54.5% in other contracts. 82 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

82 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 80% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $73K (DexScreener, all pools). 24h trading volume $2.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $73K of DEX liquidity across 7 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Wr8xaw...STNK`](https://solscan.io/account/Wr8xawXWMMBD6eWXPrf2t9kZzVwaMHLCJDRYc8zSTNK) |
| **Network** | Solana |
| **Price** | $0.000362 |
| **24h Volume** | $2.16M |
| **Liquidity** | $58.3K |
| **Volume / Liquidity** | 37.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | 80.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12312 buys / 10019 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5hkrlrxtervpkoajguct1wrjtnckadfjgyn8wtlcqd13)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/energy-coin-sol-57f0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

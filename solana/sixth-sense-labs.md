---
token: Sixth Sense Labs
ticker: SENSE
network: solana
risk_score: 20
status: low
date: 2026-10-29
---

# Sixth Sense Labs (SENSE) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sixth-sense-labs-sol)

---

## Audit Summary

The Sixth Sense Labs (SENSE) token is a Token-2022 asset with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. While liquidity is fully locked, the token exhibits a high volume-to-liquidity ratio, suggesting potential artificial trading activity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high ratio is driven by organic interest or artificial activity. Given the metadata mutability, verify the token's branding and official links through trusted, independent channels before interacting with the asset.

Verify the current on-chain state of the mint and freeze authorities via a block explorer to ensure they remain null. As holder concentration data was unavailable, exercise caution regarding potential whale activity that could impact market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program, providing advanced extensions. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are revoked. 7.2 Code Security is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis reveals $48,956 in liquidity, which is 100% locked, mitigating withdrawal risks. However, 7.6 External market data shows a volume/liquidity ratio of 38.76, exceeding the 20x… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense. The metadata is mutable, allowing for potential branding updates, which is a standard configuration for this token type. |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 38.76, which exceeds the 20x threshold, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when evaluating market demand; perform independent analysis of trade history to identify potential wash-trading patterns.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable, allowing the issuer to change branding post-launch.

**Recommendation:** Verify the token's metadata against official project documentation before trusting the branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $46K (DexScreener, all pools). 24h trading volume $2.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $46K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Gydpvg...mfun`](https://solscan.io/account/GydpvgKppv8a4gGQqAQsyQJxtQN4S6Ym9gKxjnN3mfun) |
| **Network** | Solana |
| **Price** | $0.0001859 |
| **24h Volume** | $1.89M |
| **Liquidity** | $43.0K |
| **Volume / Liquidity** | 43.9× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10090 buys / 8188 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gtl872vumrwnc34asqlzctih8co2fcwd9zpkzy2y1lqc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sixth-sense-labs-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

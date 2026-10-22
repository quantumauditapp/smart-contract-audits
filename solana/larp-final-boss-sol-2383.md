---
token: Larp Final Boss
ticker: KIMCHI
network: solana
risk_score: 53
status: medium
date: 2026-10-22
---

# Larp Final Boss (KIMCHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/larp-final-boss-sol-2383)

---

## Audit Summary

The Larp Final Boss token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, mitigating rug-pull risks, though the high volume-to-liquidity ratio suggests potential wash trading. Holder concentration data is unavailable, and metadata remains mutable.

> **Final Recommendation:** Investors should monitor the token's metadata for unexpected changes and be cautious of the high volume-to-liquidity ratio, which may indicate artificial market activity. 

Verify the current transfer fee on-chain before executing large trades, as the fee is subject to change by the fee authority.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is built on the Token-2022 program, ensuring modern extension support. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust, as both mint and… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $41,785 in liquidity, which is fully locked in an LP locker. 7.5 Governance is decentralized due to authority revocation. However, the 43.75 volume/liquidity ratio… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense. Metadata is mutable, allowing for potential branding changes. The transfer fee configuration is currently upgradable, providing… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 43.75, which exceeds the 20x threshold, indicating potential wash trading.

**Recommendation:** Exercise caution when relying on volume metrics for liquidity assessment.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the owner.

**Recommendation:** Verify metadata against official sources before interacting.


### `L-01` — Upgradable Transfer Fee  *(Severity: Low · Status: Unresolved)*

The transfer fee is currently set to 100 bps but remains upgradable by the fee authority.

**Recommendation:** Check the current fee configuration prior to trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GdXGPx...STNK`](https://solscan.io/account/GdXGPxzSVXabVKBAd61oPd87zsaBEzn2N5df3PSFSTNK) |
| **Network** | Solana |
| **Price** | $0.0001703 |
| **24h Volume** | $1.74M |
| **Liquidity** | $40.3K |
| **Volume / Liquidity** | 43.1× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12898 buys / 11535 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ej8fuu7nz1q9muko5wpl16vbgg2iqglfdptv1rpg4r7m)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/larp-final-boss-sol-2383)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*

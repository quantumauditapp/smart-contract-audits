---
token: KingPad
ticker: KING
network: solana
risk_score: 27
status: low
date: 2026-10-29
---

# KingPad (KING) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kingpad-sol)

---

## Audit Summary

KingPad (KING) is an SPL Token-2022 asset with both mint and freeze authorities successfully revoked. The liquidity is fully locked, and no adverse flags were reported by third-party registries. The primary risk factor is the mutable metadata and moderate holder concentration.

> **Final Recommendation:** Investors should monitor the token metadata for unexpected changes given the mutable status. While liquidity is locked, the holder concentration suggests that large sell orders from top wallets could significantly impact market price.

Verify the current metadata on-chain before making significant trades. No further action is required regarding authority management as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, ensuring robust standard compliance. 7.1 Architecture and 7.2 Code Security are verified through the native program's immutable logic. 7.3 Access… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by 100% locked liquidity, preventing rug-pull scenarios via pool withdrawal. 7.5 Governance is influenced by a 56.30% concentration among the top 10 holders, which… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense; however, the token metadata remains mutable. This allows for potential changes to the token name or symbol. All other authority-related… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Raydium Lock |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 56.30% of the total supply. Coordinated sell-offs by these entities could cause significant price volatility.

**Recommendation:** Monitor top holder wallet activity for large divestment patterns.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the current owner of the metadata authority.

**Recommendation:** Verify the token branding against official sources before interacting.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.3% of supply. What remains: 26.0% in wallets, 30.3% in other contracts. 134 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

134 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $45K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 2 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GMXf4j...2xsu`](https://solscan.io/account/GMXf4jmhR4hEeAjqq543oi4w2VVLd21fmKrn2gpQ2xsu) |
| **Network** | Solana |
| **Price** | $0.00003687 |
| **24h Volume** | $45.5K |
| **Liquidity** | $16.2K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 2d |
| **Top-10 Holders** | 56.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 507 buys / 324 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gqjpkgx1azo4atbuuwyvx4yyys4bf4hnaa2y8mmmuftz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kingpad-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

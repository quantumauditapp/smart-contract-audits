---
token: ᑓହꚡई
ticker: ᑓହꚡई
network: solana
risk_score: 29
status: low
date: 2026-11-03
---

# ᑓହꚡई (ᑓହꚡई) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-5b99cb-sol)

---

## Audit Summary

The token utilizes the Token-2022 program with a 5% transfer fee and mutable metadata. Mint and freeze authorities are successfully revoked, and all liquidity is permanently locked. Holder concentration data is unavailable, limiting the ability to assess whale risk.

> **Final Recommendation:** Investors should account for the 5% transfer fee when calculating entry and exit points, as this significantly reduces effective yield. Verify the token metadata on-chain before interacting to ensure the branding matches current expectations.

Monitor the token for any changes in metadata status. As holder concentration data is unavailable, exercise caution regarding potential price volatility from large, undisclosed wallets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program. 7.1 Architecture is standard for SPL tokens, with 7.3 Access Control confirmed by the revocation of both mint and freeze authorities. 7.2 Code… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic analysis shows a 5% transfer fee, which materially impacts trading costs. 7.5 Governance and holder concentration metrics are currently unavailable due to data limitations. 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints, but metadata mutability remains a factor. The token metadata is currently mutable, allowing for potential changes to branding. No other upgradeable… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | 5.0% (immutable) |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — High Transfer Fee  *(Severity: High · Status: Unresolved)*

Every transfer incurs a 5% (500 bps) fee, which is deducted from the transaction amount.

**Recommendation:** Account for the 5% fee in all swap and arbitrage calculations to avoid unexpected losses.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata is mutable, meaning the name, symbol, or image can be altered by the authority at any time.

**Recommendation:** Verify the token metadata against official sources before trusting the branding.


### `L-01` — Data Completeness Limitation  *(Severity: Low · Status: Unresolved)*

Holder concentration data is currently unavailable, preventing a full assessment of supply distribution.

**Recommendation:** Monitor on-chain activity for large, concentrated sell-offs that could indicate whale influence.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $86K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $21K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HAp8U1...cash`](https://solscan.io/account/HAp8U1SB7bDGMa81AQom1ee6AR5iSFFTi57MEbTzcash) |
| **Network** | Solana |
| **Price** | $0.00006981 |
| **24h Volume** | $85.8K |
| **Liquidity** | $21.1K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 766 buys / 518 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3vyuqtihuzudlbgnctuawytvpsv2qs7yce3epyzqecru)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-5b99cb-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

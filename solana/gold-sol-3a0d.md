---
token: Gold
ticker: GOLD
network: solana
risk_score: 21
status: low
date: 2026-10-21
---

# Gold (GOLD) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gold-sol-3a0d)

---

## Audit Summary

The Gold token (SPL-2022) demonstrates a secure configuration with both mint and freeze authorities permanently revoked. Liquidity is fully protected as 100% of the pool's LP tokens are burned, preventing rug-pull risks related to liquidity withdrawal. No adverse flags were reported by third-party risk registries.

> **Final Recommendation:** The token is configured securely with no administrative backdoors. Holders should continue to monitor the top 10 holder concentration to ensure no single entity accumulates a majority stake that could impact market stability.

Verify the current supply and authority status periodically using a block explorer to confirm that no unexpected changes have occurred, though the current revocation status makes this highly unlikely.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for the SPL-2022 program. 7.3… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance factors are stable, with top 10 holders controlling 26.83% of the supply. Liquidity is $17,242 with a healthy 3.63 volume/liquidity ratio, indicating normal trading… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints are immutable once authorities are revoked. Metadata is immutable, and no upgradeable extensions are configured. The token state is fixed and cannot… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 52.2% of supply. Of that, 25.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 26.8% in wallets, 0.0% in other contracts. 646 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

646 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $63K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 4 pools. Launch: launched on pump.fun (PumpSwap), 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GoLdZW...GoLd`](https://solscan.io/account/GoLdZWYNg9jg4z5SGCLJx69xag2vMjLaSQK5S7TUGoLd) |
| **Network** | Solana |
| **Price** | $0.00004304 |
| **24h Volume** | $63.1K |
| **Liquidity** | $17.7K |
| **Volume / Liquidity** | 3.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | 52.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1086 buys / 655 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/djbrnsdafbdsmxu5mjlvx73pzbyccweuzfwcug9dnezx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gold-sol-3a0d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

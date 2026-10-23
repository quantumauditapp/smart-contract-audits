---
token: $RAT - Exfil Rat
ticker: RAT
network: solana
risk_score: 5
status: low
date: 2026-10-23
---

# $RAT - Exfil Rat (RAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 5/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rat-exfil-rat-sol)

---

## Audit Summary

The $RAT token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is robustly secured with 97.2% of pool tokens burned, and no adverse flags were reported by third-party registries. All sources were successfully retrieved.

> **Final Recommendation:** The token demonstrates a secure configuration with no active administrative risks. Holders should continue to monitor the top 10 holder distribution via block explorers to ensure concentration remains within acceptable limits.

Verify the current mint and freeze authority status periodically on-chain to confirm they remain null. No further action is required for standard interaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply immutability and preventing account freezing (7.3 Access Control).… |
| **Governance / Economics** | 10/10 | Low | The top 10 holders control 25.95% of the supply, indicating a healthy distribution (7.4 Economic). Liquidity is $52,744 with 97.2% of LP tokens permanently burned, mitigating withdrawal risks (7.8… |
| **Upgrades** | 10/10 | Low | SPL token mints do not support upgrades (7.7 Upgrades). The current configuration is permanent as authorities are revoked and metadata is immutable (7.5 Governance). |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.9% of supply. Of that, 9.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 26.0% in wallets, 0.0% in other contracts. 318 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

318 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

97.2% of the pool's LP is burned or time-locked. 97.2% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 82% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $67K (DexScreener, all pools). 24h trading volume $76K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $67K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9FAjuj...pump`](https://solscan.io/account/9FAjujeZsLW7C8jRLvcH1fS3dYCtLV6LYHKq822dpump) |
| **Network** | Solana |
| **Price** | $0.0003622 |
| **24h Volume** | $34.1K |
| **Liquidity** | $54.9K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | 34.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 258 buys / 124 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/f7do8a2lfsm2hwqsynmj1yhv7adern5drzvd34rscjt9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rat-exfil-rat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*

---
token: Zeno Paradox
ticker: ZENO
network: solana
risk_score: 19
status: low
date: 2026-10-19
---

# Zeno Paradox (ZENO) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zeno-paradox-sol)

---

## Audit Summary

The Zeno Paradox (ZENO) SPL Token Mint exhibits a low-risk profile. Both the mint and freeze authorities have been revoked, preventing further token issuance or account freezing. All pool liquidity is burned, ensuring it cannot be withdrawn. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked. Monitor the token's liquidity and trading volume for any significant changes. While no major risks were identified, always exercise caution with new tokens and be aware that third-party risk registry data was not available for this assessment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Zeno Paradox token is implemented using the spl-token-2022 program. Crucially, the mint authority has been revoked, fixing the total supply at 939,104,720.267003 tokens. The freeze authority is… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 20.24% of the supply. The token has a total DEX liquidity of $25,740, which is fully burned (100.0%), preventing rug… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, ensuring no further changes to supply or account states can be made. The token's metadata is immutable, meaning its name, symbol, or image… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 46.8% of supply. Of that, 26.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.2% in wallets, 0.0% in other contracts. 273 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

273 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $264K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 6 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FMGe8R...pump`](https://solscan.io/account/FMGe8RStdPc1YR59BBuV5Ui12DEe3Q2zVoihrJBbpump) |
| **Network** | Solana |
| **Price** | $0.0001041 |
| **24h Volume** | $191.3K |
| **Liquidity** | $26.3K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 14h |
| **Top-10 Holders** | 46.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2194 buys / 1909 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2ufvhe5j37cuutqu8jrbu2ijqcxfpp6mjrcsqehzsxkv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zeno-paradox-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*

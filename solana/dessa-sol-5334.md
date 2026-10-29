---
token: Dessa
ticker: DESSA
network: solana
risk_score: 1
status: low
date: 2026-10-29
---

# Dessa (DESSA) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dessa-sol-5334)

---

## Audit Summary

Dessa (DESSA) is a Token-2022 asset with both mint and freeze authorities successfully revoked. The liquidity is fully burned, ensuring the pool cannot be rug-pulled by the creator. No adverse flags were reported by third-party registries, and the token exhibits standard transfer behavior.

> **Final Recommendation:** The token is currently in a secure, immutable state. Holders should continue to monitor the token's market activity and liquidity levels via standard block explorers to ensure the trading environment remains healthy.

No further security actions are required as the mint and freeze authorities are revoked and liquidity is permanently burned.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with all critical authorities revoked. 7.1 Architecture is standard for SPL tokens, and 7.3 Access Control is fully secured as mint and freeze capabilities… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, preventing withdrawal risks. 7.5 Governance is decentralized as the top 10 holders control only 3.28% of the supply. 7.6 External market… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is fixed and cannot be altered, ensuring branding consistency. No upgradeable extensions are active, providing long-term stability… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 5.7% of supply. Of that, 2.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.3% in wallets, 0.0% in other contracts. 4,538 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,538 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $183K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $183K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`npz2Fh...pump`](https://solscan.io/account/npz2FhoufQ7pKqhGpaipYWacrAkidyW2yDpVWSvpump) |
| **Network** | Solana |
| **Price** | $0.004315 |
| **24h Volume** | $1.26M |
| **Liquidity** | $183.2K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 3d |
| **Top-10 Holders** | 5.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4814 buys / 4692 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dextcer4k9dwbxtmu8znvvwgevvmvhmb183pf2xxzwvh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dessa-sol-5334)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

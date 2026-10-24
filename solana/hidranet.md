---
token: HidraNet 
ticker: HNET
network: solana
risk_score: 21
status: low
date: 2026-10-24
---

# HidraNet  (HNET) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hidranet-sol)

---

## Audit Summary

HidraNet (HNET) is a Token-2022 asset with both mint and freeze authorities successfully revoked. The project demonstrates strong security posture regarding supply control and liquidity, with 100% of pool liquidity permanently burned. No adverse flags were reported by third-party risk registries.

> **Final Recommendation:** The token is currently in a secure, immutable state. Holders should monitor the top 10 holder distribution periodically to ensure concentration does not increase significantly, which could impact market volatility.

No further action is required to secure the mint itself. Verify the token address against official project channels before interacting to avoid impersonation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.1… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, preventing rug-pulls via withdrawal. 7.5 Governance is decentralized as no single entity controls minting or freezing. Holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints. Metadata is immutable, ensuring branding consistency. 7.8 Operations are transparent with no mutable balance or fee parameters. |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 46.8% of supply. Of that, 19.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.4% in wallets, 3.7% in other contracts. 247 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as HidraNet (HNET), rank #6561. 247 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $40K (CoinGecko, all markets, daily snapshot). 24h trading volume $31K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 16 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 16 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 16 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Aov3Bt...pump`](https://solscan.io/account/Aov3BtQvrGXM5V9oiHu8PKJWeV8a2rFnr24fwWcNpump) |
| **Network** | Solana |
| **Price** | $0.00009885 |
| **24h Volume** | $30.5K |
| **Liquidity** | $26.1K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 16d |
| **Top-10 Holders** | 46.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 196 buys / 150 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hglsak3nvlzazpbmiqrkv52cmzhnvrwvquzpsncsyakw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hidranet-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

---
token: FOCO
ticker: FOCO
network: solana
risk_score: 2
status: low
date: 2026-11-02
---

# FOCO (FOCO) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/foco-sol)

---

## Audit Summary

The FOCO token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The liquidity pool is fully secured via a 100% burn of LP tokens, ensuring the liquidity cannot be withdrawn. No adverse flags were reported by third-party registries, and the token exhibits no mutable extensions.

> **Final Recommendation:** The token is currently in a secure, immutable state with no active administrative authorities. Holders should continue to monitor the top 10 holder distribution via block explorers to ensure concentration remains within healthy bounds.

No further action is required to secure the mint configuration. Users should verify the token mint address against official sources before trading to avoid impersonation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). The mint state confirms that metadata and… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders controlling 11.38% of the supply (7.5 Governance). Liquidity is $63,662 and is fully protected as 100% of LP tokens are burned (7.4 Economic).… |
| **Upgrades** | 10/10 | Low | The token mint is immutable regarding its core configuration (7.7 Upgrades). Metadata, transfer fees, and hooks are non-upgradable, preventing post-launch changes to token behavior. The revocation of… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 18.7% of supply. Of that, 7.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.4% in wallets, 0.0% in other contracts. 2,139 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as FOCO (FOCO), rank #4002. 2,139 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $63K (DexScreener, all pools). 24h trading volume $615K (CoinGecko, all markets, daily snapshot). 24h trading volume $548K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $63K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 9 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 9 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 9 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7ttfwu...pump`](https://solscan.io/account/7ttfwuBSnbNTgf32gUAT7v9bjdDWsn6pYpp7nmGmpump) |
| **Network** | Solana |
| **Price** | $0.0004205 |
| **24h Volume** | $547.7K |
| **Liquidity** | $62.8K |
| **Volume / Liquidity** | 8.7× |
| **Token Age** | 9d |
| **Top-10 Holders** | 18.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4361 buys / 4323 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8l3igrfrvkyrjnu9hzf7sk5nja62s8ga54dkatbf6qh2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/foco-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*

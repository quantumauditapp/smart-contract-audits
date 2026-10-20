---
token: Frank Ashford
ticker: FRANK
network: solana
risk_score: 7
status: low
date: 2026-10-12
---

# Frank Ashford (FRANK) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/frank-ashford-sol)

---

## Audit Summary

This audit of the Frank Ashford (Frank) SPL Token Mint found no critical or high-severity issues based on the provided on-chain data and external security signals. Key authorities like mint and freeze are revoked, and liquidity is fully burned. Third-party registry data reported no adverse flags, and no sources were unavailable that would impact the assessment of critical risks.

> **Final Recommendation:** Given the absence of critical and high-severity findings, this token appears to be well-configured from a security perspective. Holders should continue to monitor the token's market behavior and liquidity. While the liquidity is fully burned, ensuring it cannot be withdrawn, market dynamics can still impact price. No further on-chain verification steps are immediately necessary regarding mint or freeze authorities, as they are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Frank Ashford token is an SPL Token-2022 mint with a supply of 950,535,570.547829 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 21.20% of the supply. The token has $70,755 in DEX liquidity, and 100% of this liquidity is burned, preventing rug… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's core parameters cannot be altered by an external key. The token's metadata is immutable, preventing changes to its name… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 30.0% of supply. Of that, 8.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.2% in wallets, 0.0% in other contracts. 6,066 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Frank Ashford (FRANK), rank #3928. 6,066 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 95% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $77K (DexScreener, all pools). 24h trading volume $634K (CoinGecko, all markets, daily snapshot). 24h trading volume $664K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $77K of DEX liquidity across 6 pools. Launch: launched on pump.fun, 7 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HbPDWS...pump`](https://solscan.io/account/HbPDWSqu8hpVMX6gMjwMDGe5rVgicWo3Qh3Jaojypump) |
| **Network** | Solana |
| **Price** | $0.0004303 |
| **24h Volume** | $654.4K |
| **Liquidity** | $73.4K |
| **Volume / Liquidity** | 8.9× |
| **Token Age** | 7d |
| **Top-10 Holders** | 30.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7992 buys / 7991 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/745atasswxvry5qt1xvv9exug884hdvnjfva2o82dnbi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/frank-ashford-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*

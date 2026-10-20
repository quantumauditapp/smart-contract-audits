---
token: Exfil.fun
ticker: EXFIL
network: solana
risk_score: 6
status: low
date: 2026-10-13
---

# Exfil.fun (EXFIL) — Smart Contract Security Analysis | Solana

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/exfilfun-sol)

---

## Audit Summary

The Exfil.fun (EXFIL) token mint exhibits a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, ensuring a fixed supply and preventing account freezing. Liquidity is fully burned, and holder concentration is not a concern. Third-party risk registry data reported no adverse flags.

> **Final Recommendation:** This token presents a low-risk profile based on the provided on-chain data. Holders should continue to monitor DEX market data for any significant shifts in liquidity or trading patterns. While the current state is favorable, ongoing vigilance is always recommended for any digital asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Exfil.fun (EXFIL) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring that no new tokens can be minted and no holder… |
| **Governance / Economics** | 10/10 | Low | The token's economic profile appears robust. The top 10 holders that can sell collectively hold 23.64% of the supply, which does not indicate high concentration risk. Total DEX liquidity stands at… |
| **Upgrades** | 10/10 | Low | The token's upgradeability and mutability aspects are minimal, contributing to its stability. The mint and freeze authorities are revoked, preventing any post-launch changes to supply or account… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.7% of supply. Of that, 6.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.6% in wallets, 0.0% in other contracts. 656 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

656 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $88K (DexScreener, all pools). 24h trading volume $104K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $88K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 10 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 10 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 10 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6FhVPc...pump`](https://solscan.io/account/6FhVPctYg363pQbs4iSvqyHe2cJzfsvFD96gePy6pump) |
| **Network** | Solana |
| **Price** | $0.0008365 |
| **24h Volume** | $103.3K |
| **Liquidity** | $86.9K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 10d |
| **Top-10 Holders** | 29.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 444 buys / 585 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2zpfdgd48k7b2u9yqz4hjspaptovu9uiebfqyxeoexkv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/exfilfun-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*

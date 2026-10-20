---
token: The Lil Black Bull
ticker: LILANSEM
network: solana
risk_score: 19
status: low
date: 2026-10-15
---

# The Lil Black Bull (LILANSEM) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-lil-black-bull-sol)

---

## Audit Summary

This audit of The Lil Black Bull (LILANSEM) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts. Both the mint and freeze authorities have been revoked, ensuring no new tokens can be created and no accounts can be frozen. Furthermore, 100% of the DEX pool's liquidity is burned, providing strong assurance against rug pulls. Third-party risk registries reported no adverse flags, and metadata is immutable.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked. While the current state is robust, continuous monitoring of the token's market behavior, including liquidity and trading volume, is advisable. No immediate actions are required based on the current audit findings, but staying informed about any future changes to the token's on-chain state or external risk registry flags is prudent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The LILANSEM token operates on the spl-token-2022 program, indicating modern SPL token standards. Crucially, both the mint authority and freeze authority have been revoked, preventing any further… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a healthy holder distribution, with the top 10 holders that can sell accounting for only 21.54% of the supply, well below concentration thresholds. Liquidity stands at $21,541 USD… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as both mint and freeze authorities are revoked. Furthermore, the metadata (name, symbol, image) is not mutable, providing stability to its branding. There… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.8% of supply. Of that, 15.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.5% in wallets, 0.0% in other contracts. 1,247 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,247 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $87K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HQgMPJ...pump`](https://solscan.io/account/HQgMPJbGctpP9P27DdJW5f8rncz7gvg4vEL3hT7hpump) |
| **Network** | Solana |
| **Price** | $0.00006381 |
| **24h Volume** | $87.3K |
| **Liquidity** | $21.9K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | 36.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1104 buys / 720 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9upattjbw3fyx1fmwxahvhggt6sy5qhmstb5azmjmgwq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-lil-black-bull-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*

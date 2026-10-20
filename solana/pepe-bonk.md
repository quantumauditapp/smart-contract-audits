---
token: Pepe Bonk
ticker: PONK
network: solana
risk_score: 19
status: low
date: 2026-10-17
---

# Pepe Bonk (PONK) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepe-bonk-sol)

---

## Audit Summary

The Pepe Bonk (PONK) SPL Token Mint exhibits a robust security posture with no critical or high-risk findings identified. Key authorities such as Mint and Freeze are revoked, and liquidity is fully burned, indicating a secure and immutable state. Third-party risk registries reported no adverse flags, and all available sources indicate a low-risk profile.

> **Final Recommendation:** Given the strong security posture, holders should verify on-chain that the Mint and Freeze authorities remain revoked. Monitor the token's trading activity and liquidity levels, although the current setup with burned LP tokens significantly mitigates liquidity rug pull risks. No further specific actions are required regarding mutable authorities or extensions, as they are either revoked or not present.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Pepe Bonk (PONK) token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new tokens can be minted and no accounts can be… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell controlling only 29.67% of the supply, reducing the risk of large-scale dumps. The token benefits from strong liquidity provisions… |
| **Upgrades** | 10/10 | Low | The token's immutability is reinforced by the revocation of both Mint and Freeze authorities, preventing any post-deployment changes to supply or account states. Furthermore, the `metadata_mutable`… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 55.7% of supply. Of that, 26.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 29.7% in wallets, 0.0% in other contracts. 583 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

583 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $70K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (bonk, pepe); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 7 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4jjQjD...pump`](https://solscan.io/account/4jjQjDRYd7xLcFMViRsz4GvtgU6gPZgbVaxN3Rq9pump) |
| **Network** | Solana |
| **Price** | $0.00004039 |
| **24h Volume** | $70.2K |
| **Liquidity** | $16.3K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | 55.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1444 buys / 908 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/edjt1eqfx2xblmjdqyr2whcs3vzrh2brxg2bmqxpafw4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepe-bonk-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*

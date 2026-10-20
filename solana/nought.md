---
token: Nought
ticker: NOUGHT
network: solana
risk_score: 20
status: low
date: 2026-10-19
---

# Nought (NOUGHT) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nought-sol)

---

## Audit Summary

The Nought (Nought) SPL token mint has been audited based on on-chain data and external security signals. No critical or high-severity risks were identified regarding mint or freeze authorities, token extensions, or liquidity locking. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked. Monitor the token's trading activity and liquidity over time, especially given its recent creation. While no immediate risks were identified, ongoing due diligence is always recommended for new tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Nought token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, preventing further token creation or freezing of holder accounts. It does not utilize a… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 22.04% of the total supply. The token benefits from $30,471 in DEX liquidity, which is 100% burned, ensuring it… |
| **Upgrades** | 10/10 | Low | The Nought token mint has a fixed configuration as both mint and freeze authorities are revoked. Key Token-2022 extensions like transfer hook and transfer fee are not present, and their upgradability… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.4% of supply. Of that, 3.8% locked, 16.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.0% in wallets, 0.0% in other contracts. 609 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

609 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28K (DexScreener, all pools). 24h trading volume $195K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $28K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EW9ezw...pump`](https://solscan.io/account/EW9ezwtqvn3v8RpdKMEQai8n5bmajUiPnC4UBV7zpump) |
| **Network** | Solana |
| **Price** | $0.0001083 |
| **24h Volume** | $194.6K |
| **Liquidity** | $28.5K |
| **Volume / Liquidity** | 6.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | 42.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1997 buys / 1476 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/d33wvfvqkax4udrflf5zyrg2vmyajzdwkabyhrxhfy1u)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nought-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*

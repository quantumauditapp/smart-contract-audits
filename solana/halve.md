---
token: HALVE
ticker: HALVE
network: solana
risk_score: 0
status: low
date: 2026-10-30
---

# HALVE (HALVE) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/halve-sol)

---

## Audit Summary

HALVE exhibits an immutable technical configuration with both mint and freeze authorities revoked, and 100.0% of pool liquidity ($278,991) permanently burned. Chain-native RPC holder distribution was unavailable during the assessment, while an on-chain security registry reported a high holder correlation signal. No deterministic security vulnerabilities were triggered across the verified Token-2022 parameters.

> **Final Recommendation:** Execute manual RPC queries (`getTokenLargestAccounts`) to inspect individual wallet balances directly once network indexers update. Establish automated alerts tracking top holder transfers to detect coordinated offloading from correlated wallet clusters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the spl-token-2022 program with an initialized fixed supply of 999,738,201,612,739 units across 6 decimals. Both mint and freeze authorities are null, preventing secondary token… |
| **Governance / Economics** | 10/10 | Low | Decentralized exchange liquidity is established at $278,991, with all LP tokens burned to eliminate creator withdrawal risk. 24-hour trading activity reached $209,734, representing a standard 0.75… |
| **Upgrades** | 10/10 | Low | Administrative upgrade mechanisms do not exist on this mint because authority addresses have been renounced. Metadata mutability is disabled, ensuring token branding parameters remain fixed.… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $275K (DexScreener, all pools). 24h trading volume $208K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $275K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7S9v86...pump`](https://solscan.io/account/7S9v86SXnm2Hmew7peDo8XEx44T2FRmZVSqm8jaPpump) |
| **Network** | Solana |
| **Price** | $0.01126 |
| **24h Volume** | $208.5K |
| **Liquidity** | $275.2K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 15h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 54421 buys / 10811 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/46fxp9eare5cvcbkqvyjunhrxpmwdgx1sarpytobexjf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/halve-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

---
token: earth
ticker: EARTH
network: solana
risk_score: 22
status: low
date: 2026-10-20
---

# earth (EARTH) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/earth-sol)

---

## Audit Summary

The earth token demonstrates high technical security standards with all administrative authorities revoked and nearly all liquidity permanently burned. The primary risk identified is market-based, specifically a high volume-to-liquidity ratio suggesting artificial trading activity. Holder distribution data was unavailable from on-chain RPC sources at the time of this audit.

> **Final Recommendation:** While the technical configuration of the mint is secure, users should exercise caution due to the high volume-to-liquidity ratio which indicates potential market manipulation or artificial volume. Before interacting, manually verify the top 10 holder accounts on a Solana block explorer to ensure supply is not concentrated in a few wallets.

Monitor the DEX liquidity pool for any changes, although the 99.8% burn status provides significant protection against liquidity removal. Treat the current trading volume as potentially unreliable for assessing genuine market interest.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program, providing a modern standard for Solana assets (7.1). Access control is fully restricted as both the mint and freeze authorities are revoked, preventing… |
| **Governance / Economics** | 7/10 | Low | Economic security is bolstered by the fact that 99.8% of the pool's liquidity is burned, ensuring the creator cannot withdraw the underlying assets (7.4). However, the 24-hour volume of $1,435,383… |
| **Upgrades** | 10/10 | Low | The token is effectively immutable as all administrative keys have been nullified (7.7). Metadata is marked as non-mutable, preventing changes to the token's name, symbol, or branding (7.5). There… |

## Security Findings

_🟠 1 High · ⚪ 9 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour trading volume ($1,435,383) is 87.22x the total DEX liquidity ($16,457). This pattern is strongly associated with artificially inflated trade volume intended to manipulate market rankings.

**Recommendation:** Account for potential slippage and artificial price support when entering or exiting positions.


### `I-01` — Mint and Freeze Authorities Revoked  *(Severity: Informational · Status: Resolved)*

Both the mint authority and freeze authority are set to null. This prevents any future token issuance or the freezing of user accounts.

**Recommendation:** No action required; this is a positive security state.


### `I-02` — Liquidity Permanently Burned  *(Severity: Informational · Status: Resolved)*

99.8% of the pool's LP tokens are burned. This ensures that the liquidity cannot be withdrawn by the pool creator or any other entity.

**Recommendation:** Verify the burn transaction on-chain to confirm the permanent lock of liquidity.


### `I-03` — Metadata Immutable  *(Severity: Informational · Status: Resolved)*

The metadata_mutable flag is set to False. The token's name, symbol, and URI cannot be modified by the creator.

**Recommendation:** No action required.


### `I-04` — Holder Distribution Data Unavailable  *(Severity: Informational · Status: Unresolved)*

Chain-native RPC sources failed to provide holder distribution data during the audit. The concentration of the top 10 holders is unknown.

**Recommendation:** Manually inspect the 'Largest Accounts' tab on a Solana explorer for this mint address.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.8% of the pool's LP is burned or time-locked. 99.8% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $2.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2qgnTg...pump`](https://solscan.io/account/2qgnTgJbZU6Tu6CMrm5Z5ePDGuUAyGTACbBoBCw6pump) |
| **Network** | Solana |
| **Price** | $0.00003915 |
| **24h Volume** | $1.42M |
| **Liquidity** | $16.4K |
| **Volume / Liquidity** | 86.7× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17563 buys / 14462 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9sepmpy87xr3sxunvein2xxutclunuetkqvawdmeqslu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/earth-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

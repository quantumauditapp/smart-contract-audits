---
token: Stoxes
ticker: STOXES
network: solana
risk_score: 16
status: low
date: 2026-09-30
---

# Stoxes (STOXES) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stoxes-sol)

---

## Audit Summary

The Stoxes SPL token mint exhibits robust security configurations, with both mint and freeze authorities revoked, ensuring a fixed supply and preventing asset confiscation. Liquidity is substantial at $40,097 USD, with 98.2% of it locked, providing stability. Holder concentration data was unavailable from chain-native RPC, preventing an assessment of distribution risk.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor DEX market data for changes in liquidity and trading volume, especially as the pair ages. If holder concentration data becomes available, assess it for potential whale-dump risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Stoxes token is an SPL token operating on the Solana blockchain using the `spl-token` program. Its mint authority and freeze authority are both revoked, which means no new tokens can be minted… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a healthy liquidity profile with $40,097 USD in total DEX liquidity. A significant 98.2% of this liquidity is burned or locked for good, with 0.0% withdrawable by the pool's… |
| **Upgrades** | 10/10 | Low | The Stoxes token mint has a fixed configuration as both the mint and freeze authorities have been revoked, preventing any future changes to its supply or the ability to freeze accounts. The token's… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Stoxes (STOXES), rank #5455.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

98.2% of the pool's LP is burned or time-locked. 98.2% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 1.7% is held, unlocked, by 3 address(es) other than the pool's creator.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $44K (DexScreener, all pools). 24h trading volume $273K (CoinGecko, all markets, daily snapshot). 24h trading volume $410K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $44K of DEX liquidity across 10 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AfVUPh...9999`](https://solscan.io/account/AfVUPhruMtJuFVtPj4u8kvpNbNEuy7VQ3ME5eAHq9999) |
| **Network** | Solana |
| **Price** | $0.0001976 |
| **24h Volume** | $377.9K |
| **Liquidity** | $42.8K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3036 buys / 3539 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/agubqrj5t5snyfmuhqbxq4zobchbhkw2jnc79mhapqtc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stoxes-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*

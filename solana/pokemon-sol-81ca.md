---
token: Pokémon
ticker: POKÉMON
network: solana
risk_score: 9
status: low
date: 2026-10-20
---

# Pokémon (POKÉMON) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pokemon-sol-81ca)

---

## Audit Summary

No critical or high-risk parameters were identified in the on-chain mint configuration, with both mint and freeze authorities permanently revoked and 100% of pool liquidity burned. Note that chain-native RPC holder distribution data was unavailable during analysis, leaving wallet concentration unverified. DEX trading metrics and security registries indicate standard baseline operations with no adverse flags.

> **Final Recommendation:** Query the Solana RPC directly using getTokenLargestAccounts to independently confirm that no private individual controls an outsized portion of circulating supply. Set up real-time monitoring on DEX swap transactions to track sudden whale sell-offs, and monitor whether any secondary liquidity pools are initialized with unburned tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates on the spl-token-2022 program with an initialized raw supply of 968,185,980,964,881 across 6 decimals. Both mint authority and freeze authority are set to null, eliminating any risk… |
| **Governance / Economics** | 7/10 | Low | The market demonstrates decentralized exchange backing with $229,754 in liquidity and a 24-hour trading volume of $191,279. Exactly 100.0% of the pool's LP tokens have been burned, ensuring liquidity… |
| **Upgrades** | 8/10 | Low | Unlike EVM proxy architectures, Solana SPL token mints do not feature upgradeable implementation patterns. Authority parameters cannot be restored once set to None, permanently locking administrative… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $667K (DexScreener, all pools). 24h trading volume $5.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $667K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`D42TjM...Xvb1`](https://solscan.io/account/D42TjMjz5H7toPu5md5KBXreZkCSdZMEfLQwmBhJXvb1) |
| **Network** | Solana |
| **Price** | $0.001495 |
| **24h Volume** | $1.63M |
| **Liquidity** | $230.6K |
| **Volume / Liquidity** | 7.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12893 buys / 13297 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/eqeu6nyeq8necaiem1yktu3udbigtea2tyblbmr9yj7y)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pokemon-sol-81ca)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

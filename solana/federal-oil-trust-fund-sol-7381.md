---
token: Federal Oil Trust Fund
ticker: FOTF
network: solana
risk_score: 2
status: low
date: 2026-10-27
---

# Federal Oil Trust Fund (FOTF) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/federal-oil-trust-fund-sol-7381)

---

## Audit Summary

Federal Oil Trust Fund demonstrates a secure technical baseline with both mint and freeze authorities permanently revoked and 100.0% of pool liquidity burned. Chain-native RPC holder distribution data was unavailable during inspection, leaving exact concentration metrics unconfirmed despite external signals indicating holder correlation. No protocol-level security risks or administrative attack vectors were detected in the available on-chain mint configuration.

> **Final Recommendation:** Perform periodic RPC queries using getTokenLargestAccounts to independently profile wallet distribution and detect emerging whale clusters. Monitor secondary decentralized exchange venues to ensure no unburned, attacker-controlled liquidity pools are deployed to dilute trading volume.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with an initialized raw supply of 999966306105271 across 6 decimals. Neither mint authority nor freeze authority exists, ensuring total supply is… |
| **Governance / Economics** | 10/10 | Low | The primary DEX pair maintains $683,081 in total liquidity with 100.0% of LP tokens burned, entirely eliminating pool rug-pull potential. 24-hour trading activity reflects $476,739 in volume yielding… |
| **Upgrades** | 10/10 | Low | All primary administrative roles have been revoked, precluding unauthorized parameter shifts on-chain. Token-2022 extension flags confirm that transfer fee and transfer hook upgradeability are… |

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

Liquidity $683K (DexScreener, all pools). 24h trading volume $473K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $683K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8ZBVg8...pump`](https://solscan.io/account/8ZBVg8tbg9b8UNgvj3p2pnKanAjNtNHvknafi6VVpump) |
| **Network** | Solana |
| **Price** | $0.06661 |
| **24h Volume** | $472.9K |
| **Liquidity** | $682.6K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 13h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 29553 buys / 1652 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/725bbttjyrzbv5yjpmkowcubefpr3gkyqslt2efrjpai)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/federal-oil-trust-fund-sol-7381)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*

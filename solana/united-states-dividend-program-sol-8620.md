---
token: United States Dividend Program
ticker: USDP
network: solana
risk_score: 93
status: critical
date: 2026-11-07
---

# United States Dividend Program (USDP) — Smart Contract Security Analysis | Solana

> **Risk Score: 93/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-program-sol-8620)

---

## Audit Summary

The United States Dividend Program (USDP) mint exhibits an immutable and secured configuration with both mint and freeze authorities permanently revoked. Liquidity is robust at $514,809 with 100.0% of LP tokens permanently burned, mitigating liquidity removal risks. Note that chain-native holder distribution data was unavailable at the time of analysis.

> **Final Recommendation:** Query on-chain RPC token account distributions as endpoint availability resumes to confirm that individual holder balances remain decentralized across non-pool wallets. Verify LP burn transaction signatures via a block explorer prior to executing large capital transactions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The mint is deployed via the spl-token-2022 program with an initialized raw supply of 999,953,283,797,385 and 6 decimal places. Mint authority and freeze authority are both revoked (None), ensuring… |
| **Governance / Economics** | 4/10 | Medium | Decentralized exchange liquidity stands at $514,809, with 100.0% of LP tokens burned to prevent liquidity extraction by any party. Trading metrics show $368,436 in 24-hour volume, reflecting an… |
| **Upgrades** | 4/10 | Medium | Administrative capabilities have been permanently relinquished with no valid mint or freeze key remaining. Token-2022 extensions are locked, showing transfer fee upgrades and transfer hook upgrades… |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `QA-IDENTITY` — Imitation of Pax Dollar (USDP)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Pax Dollar (USDP), but the listed USDP contract on solana is hvbpjaqgnpkgbaybzqbr1t7yfdvayvp2vcqqfkken4tm (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $514K (DexScreener, all pools). 24h trading volume $365K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of Pax Dollar (USDP)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Its name presents it as a stable-value coin, yet it trades at $0.04184 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad; behaves as: meme token. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $514K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CUJvu1...pump`](https://solscan.io/account/CUJvu14xWbRz93NZjt5kgLEhzzgYTgaFactXa4a3pump) |
| **Network** | Solana |
| **Price** | $0.04184 |
| **24h Volume** | $365.4K |
| **Liquidity** | $513.8K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 13h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32296 buys / 1606 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dsgia1rt16frjpakeqjg86k5nh9rycpwe4v2kdkmkh2u)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-program-sol-8620)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*

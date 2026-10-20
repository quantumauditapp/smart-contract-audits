---
token: Anonymous Shib
ticker: ZSHIB 
network: solana
risk_score: 16
status: low
date: 2026-09-30
---

# Anonymous Shib (ZSHIB ) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anonymous-shib-sol)

---

## Audit Summary

The Anonymous Shib (ZSHIB) token is an SPL Token-2022 mint with its mint and freeze authorities revoked, ensuring a fixed supply and unfreezable accounts. A low-severity risk is present due to mutable metadata, allowing changes to the token's branding. Holder distribution data was unavailable from chain-native RPC.

> **Final Recommendation:** Before interacting with the token, verify the current metadata on-chain to ensure it aligns with expected branding. Monitor for any changes to the token's name, symbol, or image that could indicate a rebranding or malicious intent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Anonymous Shib (ZSHIB) token is an SPL Token-2022 mint with its mint authority and freeze authority both revoked, ensuring a fixed supply and preventing any account freezing. It implements a… |
| **Governance / Economics** | 9/10 | Low | The token has a total DEX liquidity of $32,796, which is above the very low liquidity threshold. Crucially, 100.0% of the pool's liquidity is locked for good in Raydium's LP locker, preventing rug… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's core parameters like supply and account freeze status cannot be altered. While the token leverages the Token-2022… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | 3.0% (immutable) |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch. This is indicated by the 'metadata_mutable: True' flag.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Anonymous Shib (ZSHIB).

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $168K (CoinGecko, all markets, daily snapshot). 24h trading volume $183K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6nSM2H...eKN4`](https://solscan.io/account/6nSM2HxvaetyDrUYjjAUKwgWGi8CGjmboLee7wcHeKN4) |
| **Network** | Solana |
| **Price** | $0.0001584 |
| **24h Volume** | $182.8K |
| **Liquidity** | $32.0K |
| **Volume / Liquidity** | 5.7× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1145 buys / 1148 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/guiuquy3kekuewkktvaqqcwjzp3hnhd64vdrisrvmf3b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anonymous-shib-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*

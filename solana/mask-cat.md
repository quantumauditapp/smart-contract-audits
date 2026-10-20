---
token: Mask Cat
ticker: MASKCAT
network: solana
risk_score: 37
status: medium
date: 2026-10-03
---

# Mask Cat (MASKCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mask-cat-sol)

---

## Audit Summary

The Mask Cat (MASKCAT) SPL Token Mint is configured with revoked mint and freeze authorities, indicating a fixed supply and unfreezable accounts. However, the token's metadata remains mutable, allowing changes to its name, symbol, or image post-launch. Holder concentration data was unavailable from chain-native RPC, preventing a full assessment of distribution risk.

> **Final Recommendation:** Holders should monitor the token's metadata for any unexpected changes to its branding. While core authorities are revoked, the mutable metadata could lead to confusion if altered. Verify the token's branding against official sources before relying on its displayed name or symbol.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Mask Cat token is an SPL Token-2022 mint with both mint and freeze authorities revoked, ensuring no new tokens can be created and no accounts can be frozen. It features a 3.00% transfer fee… |
| **Governance / Economics** | 8/10 | Low | The token has $159,942 in DEX liquidity, with 100.0% of the pool's liquidity locked for good, preventing rug pulls from liquidity withdrawal. The 24-hour volume is $961,042, resulting in a… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's core parameters related to supply and account control cannot be changed. While the transfer fee is upgradable, the… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 3.0% · upgradeable |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata is mutable. This means the token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 84% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $191K (DexScreener, all pools). 24h trading volume $1.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $191K of DEX liquidity across 9 pools. Launch: 6 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GZw7Lx...Rekp`](https://solscan.io/account/GZw7LxHtQKSQ1YsGnpNH7SovnBF8X6poYgavHwrmRekp) |
| **Network** | Solana |
| **Price** | $0.001355 |
| **24h Volume** | $942.7K |
| **Liquidity** | $161.1K |
| **Volume / Liquidity** | 5.9× |
| **Token Age** | 6d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4826 buys / 2960 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/g7qktr9lr3pf44kp6alkw8sexigdxbg2jajtzrtukk15)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mask-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*

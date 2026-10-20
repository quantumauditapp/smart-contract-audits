---
token: ninjacat
ticker: NINJACAT
network: solana
risk_score: 42
status: medium
date: 2026-10-09
---

# ninjacat (NINJACAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ninjacat-sol)

---

## Audit Summary

This SPL Token Mint exhibits a robust security posture with critical authorities like Mint and Freeze revoked, and 100% of its liquidity locked. The primary concern identified is the mutability of the token's metadata, which allows for post-launch changes to branding. Third-party risk registries reported no adverse flags for this token.

> **Final Recommendation:** Holders should monitor for any changes to the token's metadata, such as its name or symbol, to ensure it aligns with their expectations. While the transfer fee is currently 1.00%, its upgradable nature means it could be adjusted in the future, which should be verified on-chain if holding long-term.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, preventing further token creation or freezing of holder accounts. A 1.00%… |
| **Governance / Economics** | 8/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 28.03% of the total supply. The token benefits from substantial liquidity, with $153,625 in DEX pools, and 100.0% of… |
| **Upgrades** | 8/10 | Low | The Mint and Freeze authorities are permanently revoked, ensuring no new tokens can be minted and no accounts can be frozen. While the transfer hook is not upgradable, the transfer fee is upgradable… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟢 1 Low · ⚪ 7 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by 'metadata_mutable: True'.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.0% of supply. What remains: 24.4% in wallets, 3.6% in other contracts. 1,923 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as ninjacat (NINJACAT), market cap $2M, rank #2327. 1,923 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 76% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $200K (DexScreener, all pools). 24h trading volume $2.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $200K of DEX liquidity across 7 pools. Launch: 21 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 21 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 21 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9CPfv7...k147`](https://solscan.io/account/9CPfv7rc6vxBd3jtovmZtf5Zy8bdvssv8c4BwzbGk147) |
| **Network** | Solana |
| **Price** | $0.001835 |
| **24h Volume** | $1.50M |
| **Liquidity** | $151.9K |
| **Volume / Liquidity** | 9.9× |
| **Token Age** | 21d |
| **Top-10 Holders** | 28.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4491 buys / 3998 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hsj3umgn1hpvvhy3kqi1v3kmasxfdsgevvwsxp5majzw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ninjacat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*

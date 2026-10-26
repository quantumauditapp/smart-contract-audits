---
token: StonkMarket
ticker: STM
network: solana
risk_score: 19
status: low
date: 2026-10-26
---

# StonkMarket (STM) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonkmarket-sol)

---

## Audit Summary

The StonkMarket (STM) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, the liquidity is fully locked, mitigating rug-pull risks. Third-party risk registry data indicates no adverse flags.

> **Final Recommendation:** Investors should monitor the token's metadata for unexpected changes given the mutable status. Due to the high volume-to-liquidity ratio, users should exercise caution regarding slippage and potential artificial volume inflation when executing trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring robust standard compliance. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is optimal as both mint… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show 29.95% concentration among the top 10 holders, which is within safe bounds. 7.6 External market data reveals a volume/liquidity ratio of 20.69, indicating potential wash… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense. Metadata is mutable, allowing for potential branding changes. No other mutable extensions are present. |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 7 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 20.69, exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when evaluating market demand; verify trade volume sources.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata is mutable, meaning the name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 30.0% of supply. What remains: 17.0% in wallets, 13.0% in other contracts. 1,090 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,090 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $51K (DexScreener, all pools). 24h trading volume $893K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $51K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8gnyYy...xrn5`](https://solscan.io/account/8gnyYyngFtzPP6K9YRQ8a7kZWKQ5tzu5N2D23Rafxrn5) |
| **Network** | Solana |
| **Price** | $0.000262 |
| **24h Volume** | $865.5K |
| **Liquidity** | $47.1K |
| **Volume / Liquidity** | 18.4× |
| **Token Age** | 3h |
| **Top-10 Holders** | 30.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11057 buys / 7582 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/azx4s55rjm2w4gjf3jz3kvdcrmbwn4jr1upcvfpvllwz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonkmarket-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*

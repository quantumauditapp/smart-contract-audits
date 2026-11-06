---
token: Anonymous Cats
ticker: ZCATS
network: solana
risk_score: 49
status: medium
date: 2026-11-06
---

# Anonymous Cats (ZCATS) — Smart Contract Security Analysis | Solana

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anonymous-cats-sol)

---

## Audit Summary

The Anonymous Cats (ZCATS) token is a Token-2022 asset with both mint and freeze authorities successfully revoked. Liquidity is fully locked, and no adverse flags were reported by third-party registries. Holder concentration data was unavailable, and metadata remains mutable.

> **Final Recommendation:** Investors should monitor the token's metadata for unexpected changes, as it is currently mutable. Since holder concentration data is unavailable, users should exercise caution regarding potential price volatility and perform their own analysis of on-chain transaction history before committing significant capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the SPL Token-2022 program, which supports advanced extensions. 7.1 Architecture is standard for SPL mints, with 7.2 Code Security relying on the audited Token-2022 program. 7.3… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show $42,166 in liquidity, which is fully locked in a Raydium locker. 7.5 Governance is decentralized due to revoked authorities. While the volume/liquidity ratio is 14.79, the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to the mint itself, but the token metadata is mutable. The transfer fee configuration is also upgradable, allowing for future adjustments to the 100 bps fee. Users… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the owner at any time.

**Recommendation:** Verify metadata against official project channels before trusting the token's branding.


### `L-01` — Upgradable Transfer Fee  *(Severity: Low · Status: Unresolved)*

The transfer fee configuration is marked as upgradable, meaning the fee percentage could be adjusted in the future.

**Recommendation:** Monitor the token's extension configuration for changes to the transfer fee rate.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 79% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $40K (DexScreener, all pools). 24h trading volume $524K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $40K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CAMJCW...4dVq`](https://solscan.io/account/CAMJCW5oNwSKtVbaS3GSqjwZ75MXKmgYgs7Bemui4dVq) |
| **Network** | Solana |
| **Price** | $0.0001528 |
| **24h Volume** | $501.3K |
| **Liquidity** | $31.6K |
| **Volume / Liquidity** | 15.9× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5860 buys / 4418 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2k5cyxlichjuzqzs4aq7t62bzzva6f21pnbqntsrpgev)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anonymous-cats-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*

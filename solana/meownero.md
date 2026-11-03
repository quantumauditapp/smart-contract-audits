---
token: MEOWNERO
ticker: MEOWNERO
network: solana
risk_score: 44
status: medium
date: 2026-11-03
---

# MEOWNERO (MEOWNERO) — Smart Contract Security Analysis | Solana

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meownero-sol)

---

## Audit Summary

MEOWNERO is a Token-2022 asset with both mint and freeze authorities successfully revoked. The protocol demonstrates strong liquidity security with 99.8% of pool funds permanently locked. Holder concentration data is currently unavailable, and metadata remains mutable.

> **Final Recommendation:** Investors should account for the 3% transfer fee when calculating swap slippage and expected returns. Monitor the token's metadata periodically to ensure branding remains consistent with official project communications.

Verify the current transfer fee configuration on-chain via the token mint account to ensure it has not been adjusted. As holder concentration data was unavailable, users should exercise caution regarding potential whale activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program, incorporating a 300 bps (3.00%) transfer fee. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust, as both… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors include a 3% transfer fee applied to all transactions. 7.6 External liquidity is healthy at $52,170, with 99.8% of the pool locked, mitigating withdrawal risks. 7.5 Governance… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are limited to metadata and transfer fee parameters. While the transfer fee is upgradable, the mint and freeze authorities are permanently revoked, preventing supply inflation or account… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 3.0% · upgradeable |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Transfer Fee Upgradable  *(Severity: Medium · Status: Unresolved)*

The transfer fee (currently 300 bps) is marked as upgradable, allowing the fee authority to modify the cost of transfers at any time.

**Recommendation:** Monitor the fee authority's actions and verify the fee rate before executing large trades.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable, meaning it can be altered by the metadata authority post-launch.

**Recommendation:** Verify the token's metadata against official project sources before interacting.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.8% of the pool's LP is burned or time-locked. 99.8% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. 0.2% is held, unlocked, by 1 address(es) other than the pool's creator.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $47K (DexScreener, all pools). 24h trading volume $268K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $47K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6gnB2H...TWa7`](https://solscan.io/account/6gnB2H2hbTVvKUWCzNuqjWY8Rod6EVBmfHi7YxZpTWa7) |
| **Network** | Solana |
| **Price** | $0.0003217 |
| **24h Volume** | $267.4K |
| **Liquidity** | $46.7K |
| **Volume / Liquidity** | 5.7× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2305 buys / 1800 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9vjkgqsgkcpg3rygmat9grc6eotvdmmucd4oearjvogd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meownero-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

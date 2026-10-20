---
token: NoxApp
ticker: NOX
network: solana
risk_score: 46
status: medium
date: 2026-10-20
---

# NoxApp (NOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/noxapp-sol)

---

## Audit Summary

NoxApp (NOX) is a Token-2022 asset with revoked mint and freeze authorities, mitigating central control risks. The token exhibits high wash-trading signals and mutable metadata, while holder distribution data remains unavailable. Third-party risk registry data shows no adverse flags.

> **Final Recommendation:** Investors should monitor the metadata for unexpected changes and account for the 1% transfer fee in all trading calculations. Given the high volume-to-liquidity ratio, exercise caution regarding potential price volatility and artificial volume.

Verify the current metadata state on-chain periodically. Since holder concentration data is unavailable, avoid large positions that may be subject to liquidity constraints or sudden market shifts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the SPL Token-2022 program. 7.1 Architecture is standard for SPL mints, with 7.3 Access Control confirmed by the revocation of both mint and freeze authorities. 7.2 Code Security… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show $51,910 in liquidity, which is fully locked in a Raydium LP locker. 7.6 External data indicates a volume/liquidity ratio of 23.68, suggesting potential wash trading. 7.5… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are limited to metadata and transfer fee parameters. Metadata is currently mutable, allowing for potential branding changes. The transfer fee is also upgradable, though the mint and… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 23.68, exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when evaluating market demand based on volume metrics.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable, allowing the issuer to change branding post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Upgradable Transfer Fee  *(Severity: Low · Status: Unresolved)*

The transfer fee is currently set to 100 bps (1.00%) and remains upgradable by the fee authority.

**Recommendation:** Monitor the token's transfer fee configuration before executing large transactions.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $53K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $53K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Hht3oz...Aq4z`](https://solscan.io/account/Hht3ozgbgvBsoD6h1fgDzfrViWvf5tQuLqJcUptwAq4z) |
| **Network** | Solana |
| **Price** | $0.000338 |
| **24h Volume** | $1.21M |
| **Liquidity** | $52.6K |
| **Volume / Liquidity** | 23.0× |
| **Token Age** | 22h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4821 buys / 3357 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ebyelgck1ypbtd2zh9jebjgnruhctbxftm9nuo66yyjw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/noxapp-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

---
token: SUPERSTONK
ticker: SUPER
network: solana
risk_score: 13
status: low
date: 2026-10-29
---

# SUPERSTONK (SUPER) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/superstonk-sol)

---

## Audit Summary

The SUPERSTONK token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, and no adverse flags were reported by third-party registries. Holder concentration data was unavailable, preventing a full assessment of supply distribution risks.

> **Final Recommendation:** Investors should monitor the token's metadata for any unexpected changes, as the metadata remains mutable. Since holder concentration data is currently unavailable, users should exercise caution regarding potential price volatility caused by large individual holders.

Verify the current metadata state using a block explorer to ensure it matches the expected branding. No further on-chain actions are required regarding authority management as the mint and freeze functions are already permanently disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, which supports advanced extensions. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance factors are supported by 100% locked liquidity, preventing rug-pulls via liquidity withdrawal. 7.6 External market data shows a volume/liquidity ratio of 5.91… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable in the traditional sense for SPL mints. Metadata is currently mutable, allowing for potential updates to the token name, symbol, or image. Users should verify branding… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is currently mutable and can be changed by the owner of the metadata update authority.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $76K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`wpitx7...sxqj`](https://solscan.io/account/wpitx7rqwvcEcfKo7jAQ63HQ1VardD1JkK6zrBbsxqj) |
| **Network** | Solana |
| **Price** | $0.0000167 |
| **24h Volume** | $76.1K |
| **Liquidity** | $10.9K |
| **Volume / Liquidity** | 7.0× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 841 buys / 702 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fjnushdkvunjbgw8daqr5g6zft1xmgonl8i4cztzfyyl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/superstonk-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

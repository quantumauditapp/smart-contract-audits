---
token: Auralith
ticker: AURA
network: polygon
risk_score: 42
status: medium
date: 2026-10-20
---

# Auralith (AURA) — Smart Contract Security Analysis | Polygon

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/auralith-poly)

---

## Audit Summary

The Auralith contract is a standard ERC-20 token with burn capabilities. Ownership has been renounced, preventing further administrative changes to the contract's core settings. However, a governance-controlled minting function remains active, which poses a centralization risk regarding token supply inflation.

> **Final Recommendation:** To mitigate the centralization risk, it is recommended to transition the governance role to a multi-signature wallet or a decentralized DAO structure. This ensures that any future minting events require consensus rather than a single point of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin ERC-20 implementations, ensuring robust and battle-tested code. 7.1 Architecture is clean and follows standard patterns. 7.2 Code Security is high due to… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic risks are centered on the minting capability held by the governance address. 7.5 Governance is centralized, as the minting authority is not restricted by a timelock or multi-sig… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable. 7.8 Operations are stable due to the renounced ownership of administrative functions. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows a designated governance address to create an unlimited number of new tokens. This can be used to dilute the value of existing holdings at any time.

**Recommendation:** Implement a hard cap on the total supply or transition the governance role to a multi-signature wallet to require community approval for any new minting events.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 30.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 69.4% in other contracts. 2,711 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,711 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.5M (DexScreener, all pools). 24h trading volume $119K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 5% on sell. Market: $1.5M of DEX liquidity across 1 pools. Launch: 116 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd9d1...91e0`](https://polygonscan.com/address/0xd9d12f43918363cea1c0b62d16f1f81b8eae91e0) |
| **Network** | Polygon |
| **Price** | $0.2334 |
| **24h Volume** | $118.6K |
| **Liquidity** | $1.49M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 5.0% |
| **24h Transactions** | 104 buys / 178 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0xe013abdcf414672062321a846d800f13fca26dd1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/auralith-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

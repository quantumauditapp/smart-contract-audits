---
token: AS Token
ticker: AS
network: polygon
risk_score: 54
status: medium
date: 2026-10-20
---

# AS Token (AS) — Smart Contract Security Analysis | Polygon

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/as-token-poly)

---

## Audit Summary

The AS token is a standard ERC-20 implementation with integrated access control and fee management. The protocol relies on centralized administrative roles to manage supply and transfer parameters. While the code is clean and follows standard patterns, the high degree of centralization poses a risk to token holders.

> **Final Recommendation:** The protocol should consider implementing a timelock for sensitive administrative functions like minting or fee adjustments to provide transparency and protection for token holders. Additionally, transitioning to a multi-signature wallet for the default admin role would mitigate the risk of a single point of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes standard OpenZeppelin libraries for ERC-20 and AccessControl, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is implemented via roles… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The ability to mint tokens and adjust fees allows administrators to significantly impact token value. There are no on-chain governance… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not currently implemented as the contract is not a proxy. 7.8 Operations are straightforward, relying on standard ERC-20 functionality. No complex upgrade logic exists to introduce… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint function allows a privileged vault address to create new tokens at will, which can dilute the value of existing holdings. This function is restricted to the vault role.

**Recommendation:** Implement a hard cap on the total supply or require a multi-signature approval process for minting events to protect token holders from unexpected dilution.


### `CP-07` — Administrative Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The setRatio function allows administrators to change transfer fees dynamically. This grants the controller the ability to significantly alter the cost of moving tokens.

**Recommendation:** Set a maximum fee limit in the contract to prevent administrators from setting confiscatory fee rates, and document the fee policy clearly for users.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $6.7M (DexScreener, all pools). 24h trading volume $151K (CoinGecko, all markets, daily snapshot). 24h trading volume $130K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $27.90 on 2025-08-05; the price is now 99.3335% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 94.9% of supply. Of that, 6.6% burned, 6.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 82.2% in other contracts. 405,849 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AKAS (AS). 405,849 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 0% on buy, 3% on sell. Market: $6.7M of DEX liquidity across 3 pools. Launch: 495 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6a92...b26e`](https://polygonscan.com/address/0x6a92b1e99de09f71cd96bc91f934826d96b8b26e) |
| **Network** | Polygon |
| **Price** | $0.184 |
| **24h Volume** | $130.4K |
| **Liquidity** | $6.68M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.9% of supply |
| **Buy / Sell Tax** | 0.0% / 3.0% |
| **24h Transactions** | 7014 buys / 3168 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x1a9221261dc445d773e66075b9e9e52f40e15ab1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/as-token-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

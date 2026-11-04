---
token: FintechAI Ecosystem
ticker: FNAE
network: bsc
risk_score: 55
status: medium
date: 2026-11-04
---

# FintechAI Ecosystem (FNAE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fintechai-ecosystem-bsc)

---

## Audit Summary

The protocol implements a standard ERC-20 token with additional minting capabilities and administrative controls. While the core token logic follows established standards, the presence of centralized minting and transfer-blocking mechanisms introduces significant trust requirements for token holders. Coverage includes 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.4 Economic, 7.5 Governance, 7.6 External, 7.7 Upgrades, and 7.8 Operations.

> **Final Recommendation:** It is recommended to transition the minter role to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with centralized control. Additionally, implementing a timelock for sensitive administrative actions would provide transparency and protection for token holders against sudden changes in trading status or supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The codebase utilizes standard OpenZeppelin libraries for ERC-20, Permit, and Burnable functionality, ensuring robust base implementation. The architecture is monolithic and straightforward, reducing… |
| **Governance / Economics** | 1/10 | High | The economic model is highly centralized, granting the minter full control over supply inflation and market liquidity. The ability to toggle trading via the mint function allows for potential… |
| **Upgrades** | 2/10 | High | The contract is not upgradeable and does not utilize proxy patterns. This ensures immutability of the logic, preventing future unauthorized code changes. The lack of upgradeability is a strength for… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows a privileged minter to create new tokens at will. This central authority can dilute the value of existing holdings by increasing the total supply without community oversight.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or replace it with a fixed supply model to ensure token scarcity and holder protection.


### `CP-05` — Administrative Control Over Trading  *(Severity: Medium · Status: Unresolved)*

The mint function includes logic that can influence the trading status of the token. This allows the controller to arbitrarily halt or enable trading, potentially trapping liquidity or preventing users from exiting their positions.

**Recommendation:** Remove the ability for administrative functions to toggle trading status, or implement a transparent, time-locked governance process for any changes to market access.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x0170…3bca — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.4% of supply. Of that, 16.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.2% in wallets, 81.1% in other contracts. 190 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

190 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.0M (DexScreener, all pools). 24h trading volume $169K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 0% on buy, 4.99% on sell. Market: $3.0M of DEX liquidity across 1 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8591...81af`](https://bscscan.com/address/0x85914464dbfc3e61ce4716f23e5d7616edc181af) |
| **Network** | BNB Chain |
| **Price** | $56.4300 |
| **24h Volume** | $169.1K |
| **Liquidity** | $2.98M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 6d |
| **Top-10 Holders** | 97.4% of supply |
| **Buy / Sell Tax** | 0.0% / 5.0% |
| **24h Transactions** | 1622 buys / 1754 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x3b5656ccbc2dc3c6dfe68c311236017248aae26a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fintechai-ecosystem-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*

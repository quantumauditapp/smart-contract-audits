---
token: SENSEI
ticker: SENSEI
network: bsc
risk_score: 57
status: medium
date: 2026-11-01
---

# SENSEI (SENSEI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sensei-bsc)

---

## Audit Summary

SenseiToken is a standard ERC-20 token with additional administrative controls allowing the minter to manage supply and transfer restrictions. The architecture is straightforward, utilizing OpenZeppelin standards for core functionality. However, the centralization of power in the minter role introduces significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the minter role possesses significant power to alter the token's economic state and restrict individual access. It is recommended to transition the minter role to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks.

Ensure that the minter address is secured with hardware-based multi-factor authentication. Regularly monitor the minter's activity on-chain to ensure that administrative functions are only used for legitimate protocol maintenance.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 implementation patterns, ensuring compatibility with major DEXs and wallets. 7.1 Architecture is clean, relying on established libraries for core logic. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | The protocol relies on a single privileged minter role, which creates a high degree of centralization. 7.3 Access Control is strictly enforced but grants the minter total authority over supply and… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, which provides immutability for the logic layer. 7.7 Upgrades are not supported, meaning the current rules are fixed unless the minter uses existing administrative… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.4% (≈ permanent lock) |
| **LP Locked** | 99.4% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The minter role can call mint() or restoreFrom() to increase the total supply of tokens. This allows the controller to dilute the value of existing holdings at their discretion.

**Recommendation:** Implement a time-lock or a multi-signature requirement for minting operations to prevent unilateral supply changes.


### `CP-05` — Transfer Restriction Switch  *(Severity: Medium · Status: Unresolved)*

The disableBlocks() function allows the minter to toggle a global switch that can halt or restrict token transfers. This creates a risk where the minter can effectively freeze the market for the token.

**Recommendation:** Remove the ability to globally disable transfers or restrict this function to emergency-only scenarios governed by a decentralized vote.


### `CP-06` — Individual Address Blocking  *(Severity: Medium · Status: Unresolved)*

The setPoolBlocked() function allows the minter to blacklist specific addresses from interacting with the token. This gives the controller the power to censor individual users or liquidity pools.

**Recommendation:** Limit the use of blacklisting to specific, transparent, and pre-defined compliance scenarios, or remove the functionality entirely to ensure censorship resistance.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 62.0% of supply. Of that, 27.9% burned, 25.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.4% in wallets, 4.3% in other contracts. 5,325 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,325 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.4% of the pool's LP is burned or time-locked. 99.4% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.6% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $378K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $22K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa683...52da`](https://bscscan.com/address/0xa6839b3bc2483f8312466efa25ac8ccc8feb52da) |
| **Network** | BNB Chain |
| **Price** | $0.00000004 |
| **24h Volume** | $378.0K |
| **Liquidity** | $22.2K |
| **Volume / Liquidity** | 17.0× |
| **Token Age** | 9h |
| **Top-10 Holders** | 62.0% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 2939 buys / 3823 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xab757b19c35cede781097d4ebf7a764f47a9a05a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sensei-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*

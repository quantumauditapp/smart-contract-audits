---
token: 安小将
ticker: 安小将
network: bsc
risk_score: 57
status: medium
date: 2026-11-01
---

# 安小将 (安小将) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-52cb15-bsc)

---

## Audit Summary

The AnXiaoJiangToken is a standard ERC-20 implementation with added administrative controls that allow a designated 'minter' address to mint tokens, block specific addresses, and toggle transfer restrictions. While the core ERC-20 logic follows standard patterns, the centralized control over token supply and transferability introduces significant trust requirements for token holders. 7.1 Architecture: Standard ERC-20 with centralized administrative roles. 7.2 Code Security: Standard OpenZeppelin-like implementation. 7.3 Access Control: High centralization via the 'minter' role. 7.4 Economic: Inflationary risk via minting. 7.5 Governance: No decentralized governance. 7.6 External: No external dependencies. 7.7 Upgrades: Not upgradeable. 7.8 Operations: Administrative functions are active.

> **Final Recommendation:** Token holders should be aware that the 'minter' address possesses significant power to alter the token's economic state and restrict individual access. It is recommended to transition these administrative functions to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks.

Ensure that the private keys associated with the 'minter' role are stored in a highly secure environment, such as a hardware security module or a multi-party computation (MPC) wallet, to prevent unauthorized access to these sensitive functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC-20 logic, ensuring reliable token transfers and allowance management. The code is clean and follows established patterns for state updates.… |
| **Governance / Economics** | 1/10 | High | The economic model is highly centralized, granting the 'minter' address total control over supply and transferability. This creates a significant trust dependency, as the minter can dilute holders or… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable and does not utilize proxy patterns. The logic is immutable once deployed. This eliminates risks associated with implementation changes but prevents fixing potential… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.6% (≈ permanent lock) |
| **LP Locked** | 99.6% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'minter' address has the authority to call the mint() function, which increases the total supply of tokens. This allows the controller to dilute the value of existing holdings at any time.

**Recommendation:** Implement a hard cap on total supply or transition the minting authority to a decentralized governance mechanism.


### `CP-05` — Centralized Transfer Restriction Switch  *(Severity: Medium · Status: Unresolved)*

The 'minter' address can call disableBlocks() to toggle global transfer restrictions. This grants the controller the ability to halt all token trading activity across the network.

**Recommendation:** Remove the ability to globally halt transfers or require a community-approved governance vote to trigger such a state.


### `CP-06` — Arbitrary Address Blacklisting  *(Severity: Medium · Status: Unresolved)*

The 'minter' address can call setPoolBlocked() to add specific addresses to a blacklist. This prevents targeted users from transferring or selling their tokens.

**Recommendation:** Restrict the blacklisting capability to specific, transparent, and legally defined scenarios, or remove it entirely to ensure censorship resistance.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 68.1% of supply. Of that, 52.8% burned, 8.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.2% in wallets, 3.6% in other contracts. 702 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

702 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.6% of the pool's LP is burned or time-locked. 99.6% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.4% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $264K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $13K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7fe3...2528`](https://bscscan.com/address/0x7fe3d7e6e18a31a8751db78ee7c7a8ffef0f2528) |
| **Network** | BNB Chain |
| **Price** | $0.00000006 |
| **24h Volume** | $263.7K |
| **Liquidity** | $12.8K |
| **Volume / Liquidity** | 20.6× |
| **Token Age** | 22h |
| **Top-10 Holders** | 68.1% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 2644 buys / 4136 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x07428f7c335a639b629864c3f3b3c2ac568e69a6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-52cb15-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*

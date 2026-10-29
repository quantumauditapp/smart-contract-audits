---
token: BIBIAI
ticker: BIBIAI
network: bsc
risk_score: 49
status: medium
date: 2026-10-29
---

# BIBIAI (BIBIAI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bibiai-bsc-4da8)

---

## Audit Summary

BibiToken is an ERC-20 compliant token with centralized administrative controls. The contract implements standard token functionality but grants a 'minter' role significant power over supply dynamics and transfer restrictions. While the code is clean and follows standard OpenZeppelin patterns, the centralization of power poses a risk to token holders.

> **Final Recommendation:** The protocol should consider transitioning the 'minter' role to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single privileged controller. Additionally, implementing a timelock on sensitive functions like 'setPoolBlocked' would provide transparency and protection for token holders against sudden administrative actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 implementation, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is strictly enforced via the… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance aspects are highly centralized under the 'minter' role. This controller can unilaterally mint tokens, block addresses, and toggle transfer restrictions. While this… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, satisfying 7.7 Upgrades requirements by ensuring the logic remains immutable. 7.8 Operations are straightforward, with no complex proxy patterns to manage or maintain. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.2% (≈ permanent lock) |
| **LP Locked** | 99.2% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'minter' role has the authority to call the 'mint' function, which increases the total supply of tokens. This allows the controller to dilute the value of existing holdings at their discretion.

**Recommendation:** Restrict minting capabilities to a multi-signature wallet or implement a hard-coded supply cap that cannot be exceeded by the controller.


### `CP-05` — Administrative Transfer Switch  *(Severity: Medium · Status: Unresolved)*

The 'minter' can call 'disableBlocks' to alter the transfer logic of the token. This creates a centralized switch that can halt all trading activity for the entire ecosystem.

**Recommendation:** Remove the ability to globally disable transfers or implement a community-driven governance vote to trigger such a state change.


### `CP-06` — Address Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The 'minter' can use 'setPoolBlocked' to prevent specific addresses from transferring or selling their tokens. This gives the controller the power to censor individual users.

**Recommendation:** Limit the use of blacklisting to specific, well-defined scenarios (e.g., regulatory compliance) and document the criteria for blocking addresses clearly.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 46.6% of supply. What remains: 2.3% in wallets, 44.3% in other contracts. 242 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

242 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.2% of the pool's LP is burned or time-locked. 99.2% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.6% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $145K (DexScreener, all pools). 24h trading volume $839K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $145K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x415a...47f9`](https://bscscan.com/address/0x415aac3e46264c046d103c994a1da71f05c547f9) |
| **Network** | BNB Chain |
| **Price** | $0.00000054 |
| **24h Volume** | $838.7K |
| **Liquidity** | $144.9K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 4h |
| **Top-10 Holders** | 46.6% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 5364 buys / 6026 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x10c139638721bb8b40cfe6434acbbb5c295d0991)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bibiai-bsc-4da8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

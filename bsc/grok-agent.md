---
token: Grok Agent
ticker: GROK
network: bsc
risk_score: 70
status: high
date: 2026-11-02
---

# Grok Agent (GROK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grok-agent-bsc)

---

## Audit Summary

ScarabToken is a standard ERC-20 implementation with additional administrative functions for minting and liquidity management. The contract utilizes OpenZeppelin standards for core logic, ensuring robust transfer mechanisms. The primary risk involves centralized control over supply and liquidity, which is typical for this token architecture.

> **Final Recommendation:** The protocol should consider transitioning the minter role to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with centralized control. Additionally, implementing a timelock on sensitive functions like minting would provide transparency and protection for token holders against sudden supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with 7.1 Architecture and 7.2 Code Security adhering to best practices. 7.3 Access Control is implemented via a minter role, ensuring only authorized… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized under the minter role. The ability to mint tokens and manipulate liquidity balances creates a trust-based model for token holders. While… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, which eliminates 7.7 Upgrades risk. 7.8 Operations are straightforward and rely on the immutability of the deployed bytecode. No proxy patterns are utilized. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.6% (≈ permanent lock) |
| **LP Locked** | 99.6% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The minter role has the authority to call mint() and restoreFrom(), which can increase the total supply or move tokens from user balances. This allows the controller to dilute the value of existing holdings at their discretion.

**Recommendation:** Restrict the minter role to a multi-signature wallet or a timelocked governance contract to prevent unilateral actions that could negatively impact token holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 84.3% of supply. Of that, 15.1% burned, 63.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.6% in wallets, 0.0% in other contracts. 371 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

371 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.6% of the pool's LP is burned or time-locked. 99.6% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.4% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $214K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $12K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x59c3...670d`](https://bscscan.com/address/0x59c34b8f07aa50bd469f33c30ddb66518d0b670d) |
| **Network** | BNB Chain |
| **Price** | $0.00000001 |
| **24h Volume** | $214.2K |
| **Liquidity** | $11.5K |
| **Volume / Liquidity** | 18.6× |
| **Token Age** | 12h |
| **Top-10 Holders** | 84.3% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 2245 buys / 3141 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x11648fa63f8e676282b52df6d80d99d927c31625)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grok-agent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*

---
token: BDOG
ticker: BDOG
network: bsc
risk_score: 57
status: medium
date: 2026-11-02
---

# BDOG (BDOG) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bdog-bsc)

---

## Audit Summary

The BDOGToken is a standard ERC-20 implementation with centralized administrative controls. The protocol relies on a 'minter' role that possesses significant power over token supply and transferability. While the code follows standard OpenZeppelin patterns, the centralization of power presents a notable risk to token holders.

> **Final Recommendation:** To improve security, consider transitioning the 'minter' role to a multi-signature wallet or a decentralized DAO contract to prevent single-point-of-failure risks. Additionally, implementing a timelock on sensitive functions like 'setPoolBlocked' or 'mint' would provide transparency and protection for token holders against sudden administrative actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin ERC-20 libraries, ensuring robust base functionality. 7.1 Architecture is clean, and 7.2 Code Security is high due to the use of well-audited primitives.… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are highly centralized. The minter role can unilaterally mint tokens, block addresses, and toggle transfer functionality. This creates a significant trust… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to the minter's ability to manage supply and transfer rules. The lack of upgradeability ensures immutability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'mint' function allows the designated minter to create new tokens at will, which can dilute the value of existing holdings.

**Recommendation:** Restrict minting to a multi-signature wallet or implement a hard-coded supply cap that cannot be exceeded.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The 'disableBlocks' function allows the minter to globally halt or enable token transfers, effectively freezing the market for all users.

**Recommendation:** Remove the ability to globally disable transfers or implement a governance-based voting mechanism for such drastic actions.


### `CP-06` — Address Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The 'setPoolBlocked' function allows the minter to prevent specific addresses from transferring tokens, which can be used to censor users.

**Recommendation:** Limit the use of blacklisting to specific regulatory compliance scenarios and ensure the logic is transparently documented.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.3% of supply. Of that, 39.3% burned, 32.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.3% in wallets, 2.4% in other contracts. 328 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

328 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $194K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $13K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1dbe...678d`](https://bscscan.com/address/0x1dbe621d2f8651cf863ddaa6d7c8ef1c12d3678d) |
| **Network** | BNB Chain |
| **Price** | $0.00000002 |
| **24h Volume** | $194.3K |
| **Liquidity** | $12.9K |
| **Volume / Liquidity** | 15.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 79.3% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 2343 buys / 2868 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x2a6e352224212a5309a376e445cbfd3042f78c1a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bdog-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*

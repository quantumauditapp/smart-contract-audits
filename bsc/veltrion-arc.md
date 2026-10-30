---
token: VELTRION ARC
ticker: VARC
network: bsc
risk_score: 55
status: medium
date: 2026-10-30
---

# VELTRION ARC (VARC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/veltrion-arc-bsc)

---

## Audit Summary

VeltrionToken is a standard ERC-20 token with additional administrative controls allowing for minting, burning, and transfer restrictions. The contract relies on a centralized 'minter' role to manage supply and liquidity pool interactions. While the code follows standard patterns, the high level of centralization poses significant risks to token holders.

> **Final Recommendation:** The protocol should transition the 'minter' role to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single point of failure. Implementing a time-lock mechanism for sensitive administrative actions would provide transparency and protection for token holders against sudden changes in transfer rules or supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with clean, well-structured logic. 7.1 Architecture is straightforward, utilizing a single-contract design. 7.2 Code Security is high, with no… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are highly centralized. The 'minter' role has unilateral control over supply inflation and the ability to freeze liquidity pools. This creates a single point… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to the initial setup and ongoing management by the minter. The lack of upgradeability ensures the logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.2% (≈ permanent lock) |
| **LP Locked** | 99.2% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'minter' address has the power to call the mint function, which increases the total supply of tokens. This allows the controller to dilute the holdings of all existing token holders at any time.

**Recommendation:** Restrict the minting capability to a capped amount or transition the minter role to a decentralized governance mechanism.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The 'minter' can call disableBlocks to toggle a global switch that impacts transfer functionality. This gives the controller the ability to halt trading or restrict token movement across the entire ecosystem.

**Recommendation:** Remove the ability to globally disable transfers or implement a time-lock to ensure any such action is transparent and expected by the community.


### `CP-06` — Arbitrary Address Blocking  *(Severity: Medium · Status: Unresolved)*

The 'minter' can use setPoolBlocked to prevent specific addresses from interacting with the token. This allows the controller to censor individual users or liquidity pools, effectively freezing their assets.

**Recommendation:** Limit the use of address blocking to specific, well-defined scenarios (e.g., compliance) and ensure the logic is transparently documented.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.8% of supply. Of that, 4.8% burned, 22.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.8% in wallets, 0.9% in other contracts. 2,040 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,040 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.2% of the pool's LP is burned or time-locked. 99.2% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.7% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $39K (DexScreener, all pools). 24h trading volume $355K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $39K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd70f...f919`](https://bscscan.com/address/0xd70fb04a22df6dc20fc84576cf44765e5d12f919) |
| **Network** | BNB Chain |
| **Price** | $0.00000009 |
| **24h Volume** | $355.1K |
| **Liquidity** | $38.9K |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 20h |
| **Top-10 Holders** | 36.8% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 3419 buys / 3651 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe38f588c67c5b05f9b0acb2332445e289ce99830)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/veltrion-arc-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

---
token: Agentic Coin
ticker: AGC
network: bsc
risk_score: 48
status: medium
date: 2026-11-02
---

# Agentic Coin (AGC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agentic-coin-bsc)

---

## Audit Summary

The AGC token is a standard ERC-20 implementation with added administrative controls for minting, fee management, and transfer flow control. The contract relies on a centralized minter role and internal logic for swap-back operations. While the code is structurally sound, the high degree of administrative privilege poses a significant centralization risk to token holders.

> **Final Recommendation:** It is recommended to transition the minter role to a multi-signature wallet or a decentralized governance contract to mitigate centralization risks. Additionally, implementing a time-lock for sensitive fee and supply changes would provide transparency and protection for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 patterns with clean logic for state management. 7.1 Architecture is straightforward, though 7.2 Code Security reveals minor rounding issues. 7.3 Access Control is… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance aspects are highly centralized. The minter role has unilateral power to dilute supply and adjust fees, which directly impacts holder value. There are no time-locks or… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are handled via fixed administrative roles. The lack of upgradeability ensures immutability but prevents emergency… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 92.7% |
| **LP Locked** | 92.7% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The minter role has the authority to mint new tokens up to the maximum supply, which can lead to the dilution of existing token holders' value.

**Recommendation:** Restrict minting capabilities or implement a multi-signature requirement for all minting operations.


### `CP-05` — Administrative Control Over Transfers  *(Severity: Medium · Status: Unresolved)*

The swapBackSelf function allows the controller to toggle a switch that can halt or enable token transfers, potentially locking user funds.

**Recommendation:** Remove the ability to pause transfers or implement a clear, public-facing policy for when this function is utilized.


### `CP-07` — Unrestricted Fee Modification  *(Severity: Medium · Status: Unresolved)*

The minter role can arbitrarily change transfer fees, which directly affects the economic outcome of every transaction for users.

**Recommendation:** Set a hard cap on the maximum fee percentage that can be configured by the administrator.


### `CD-01` — Rounding Loss Due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In the _swapBack function, performing division before multiplication can result in precision loss, leading to inaccurate fee calculations.

**Recommendation:** Reorder mathematical operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 54.8% of supply. Of that, 16.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.8% in wallets, 33.3% in other contracts. 1,520 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,520 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

92.7% of the pool's LP is burned or time-locked. 92.7% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 7.3% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $126K (DexScreener, all pools). 24h trading volume $546K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $126K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x63de...4ba6`](https://bscscan.com/address/0x63dea5acdbe1f27c968907d08610a5f0a0284ba6) |
| **Network** | BNB Chain |
| **Price** | $0.00001367 |
| **24h Volume** | $546.3K |
| **Liquidity** | $125.6K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 6h |
| **Top-10 Holders** | 54.8% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 3922 buys / 1831 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe56041cddbb46db01c67b7a62684f428a04db8c6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agentic-coin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*

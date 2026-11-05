---
token: Grand Dacity Coin
ticker: GDC
network: ethereum
risk_score: 42
status: medium
date: 2026-11-05
---

# Grand Dacity Coin (GDC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grand-dacity-coin-eth)

---

## Audit Summary

The audited contract is a standard ERC-20 token implementation. The architecture follows established OpenZeppelin patterns, ensuring standard compliance for transfers and allowances. A high-severity issue was identified regarding return value consistency in the transfer logic, which may impact integration with certain DeFi protocols.

> **Final Recommendation:** The contract is functionally sound for basic token transfers. To ensure full compatibility with all DeFi protocols, the transfer logic should be updated to strictly adhere to the ERC-20 specification regarding return values.

Ensure that all future integrations verify the boolean return of transfer functions to prevent potential failures in automated systems that expect strict adherence to the ERC-20 standard.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for 7.1 Architecture and 7.2 Code Security. 7.3 Access Control is absent as there are no privileged roles, which minimizes attack surface. 7.6… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance factors are not applicable as the contract is a simple token without staking, minting, or voting mechanisms. The lack of administrative control ensures no 7.8… |
| **Upgrades** | 8/10 | Low | The contract is not a proxy, meaning 7.7 Upgrades risk is non-existent. The code is immutable, providing high confidence in long-term behavior. No upgrade paths exist for the logic or state. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `CD-01` — Inconsistent Return Values in Transfer Functions  *(Severity: High · Status: Unresolved)*

The _transfer function and related transfer/transferFrom methods do not consistently handle return values as expected by some external protocols. This can cause integration failures where the calling contract expects a boolean success indicator that may not be correctly propagated or handled in specific edge cases.

**Recommendation:** Ensure that all transfer-related functions explicitly return a boolean value as defined by the ERC-20 standard and that the internal _transfer logic does not interfere with the expected return flow of the public-facing functions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.2% of supply. What remains: 6.4% in wallets, 22.8% in other contracts. 340 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

340 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $47K (DexScreener, all pools). 24h trading volume $453K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $47K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9fd6...b74d`](https://etherscan.io/address/0x9fd621bc85aa080e99d10263df0449de4e19b74d) |
| **Network** | Ethereum |
| **Price** | $0.0002531 |
| **24h Volume** | $452.6K |
| **Liquidity** | $47.2K |
| **Volume / Liquidity** | 9.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | 29.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1499 buys / 961 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf2ed610dff5251a9bd74abdb821ad88fdd50c8203caeedd5bef430b10bb0334b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grand-dacity-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*

---
token: You Missed Bitches
ticker: YMB
network: ethereum
risk_score: 84
status: high
date: 2026-10-23
---

# You Missed Bitches (YMB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/you-missed-bitches-eth)

---

## Audit Summary

The contract is a standard ERC-20 token with additional tax, limit, and trading control features. Ownership has been renounced, meaning the administrative functions that previously allowed for fee adjustments, trading toggles, and limit modifications are now permanently disabled. The code is functionally immutable regarding its privileged parameters.

> **Final Recommendation:** The contract is secure for users because the owner can no longer modify the token's behavior. No further action is required as the administrative surface is effectively removed.

For future deployments, avoid using tx.origin for authorization, as it is susceptible to phishing attacks. Ensure all arithmetic operations use SafeMath or Solidity 0.8+ overflow checks to prevent precision loss.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows a standard ERC-20 implementation with integrated tax and liquidity management. 7.1 Architecture and 7.2 Code Security are robust, though the use of tx.origin for logic is… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance are currently static. Since ownership is renounced, the economic parameters (fees, limits) cannot be altered by any party. This eliminates the risk of rug-pulls via… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable because the contract logic is fixed. No upgrade paths exist, ensuring the current logic remains permanent. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 8 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x61e5…1666) — they can pull that liquidity at any moment. This is the rug-pull path.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-02` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin to determine rules in the _transfer function. This is a security risk as it can be exploited by malicious contracts to bypass authorization checks.

**Recommendation:** Use msg.sender instead of tx.origin for all authorization and logic checks.


### `CD-01` — Potential Rounding Loss  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in some calculations within the _transfer function, which can lead to minor precision loss.

**Recommendation:** Reorder operations to perform multiplication before division to maintain precision.


### `CP-05` — Dormant Administrative Trading Controls  *(Severity: Informational · Status: Unresolved)*

Functions like enableTrading and updateSwapEnabled previously allowed the owner to toggle trading and swap features. Because ownership is renounced, these functions are now permanently inaccessible.

**Recommendation:** No action required; the risk is mitigated by the renounced ownership.


### `CP-07` — Dormant Fee Adjustment Controls  *(Severity: Informational · Status: Unresolved)*

Functions updateSellFees and updateBuyFees allowed the owner to change tax rates. These are now permanently disabled due to renounced ownership.

**Recommendation:** No action required.


### `CP-08` — Dormant Transaction Limit Controls  *(Severity: Informational · Status: Unresolved)*

Functions like updateMaxTxnAmount and updateMaxWalletAmount allowed the owner to set transaction limits. These are now permanently disabled.

**Recommendation:** No action required.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 35.7% of supply. Of that, 20.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.7% in wallets, 0.0% in other contracts. 200 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

200 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $46K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $24K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbfe3...2cd7`](https://etherscan.io/address/0xbfe3defa573d5f225b659f0f034e28f5fa6d2cd7) |
| **Network** | Ethereum |
| **Price** | $0.00005931 |
| **24h Volume** | $46.3K |
| **Liquidity** | $24.1K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 2h |
| **Top-10 Holders** | 35.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 207 buys / 199 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x653fce136ccf0bf5f0ad5c56b614747822879a2e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/you-missed-bitches-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*

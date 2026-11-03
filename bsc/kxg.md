---
token: KXG
ticker: KXG
network: bsc
risk_score: 46
status: medium
date: 2026-11-03
---

# KXG (KXG) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kxg-bsc)

---

## Audit Summary

The Kxg token is a standard ERC-20 implementation with additional transfer restriction logic. Ownership has been renounced on-chain, effectively locking the administrative functions and preventing any further modifications to the whitelist or restriction settings. The protocol is currently immutable and operates as intended by its current configuration.

> **Final Recommendation:** The contract is secure and immutable due to the renunciation of ownership. No further action is required as the administrative functions are permanently disabled.

Users should verify the current state of the 'purchaseRestrictionEnabled' flag via a block explorer to confirm the token's active transfer rules before interacting with the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and ReentrancyGuard, ensuring robust base functionality. 7.1 Architecture is standard for a utility token, while 7.2 Code Security is… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are effectively mitigated by the renunciation of ownership. No entity can alter the tokenomics or transfer rules, providing users with certainty regarding the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which eliminates the risk of malicious or accidental logic updates. 7.8 Operations are stable and require no… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 98.0% (≈ permanent lock) |
| **LP Locked** | 98.0% — Null Address |

## Security Findings

_⚪ 6 Informational_

### `CP-05` — Dormant Administrative Transfer Controls  *(Severity: Informational · Status: Unresolved)*

The contract contains functions like setPurchaseRestrictionEnabled that allow a controller to toggle transfer restrictions. Because ownership has been renounced, these functions are now permanently inaccessible, rendering the controls dormant.

**Recommendation:** No action is required as the renunciation of ownership is a security feature that prevents unauthorized changes to the contract logic.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 77.2% of supply. Of that, 2.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 72.6% in wallets, 1.9% in other contracts. 36,700 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

36,700 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

98.0% of the pool's LP is burned or time-locked. 98.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 2.0% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $134K (DexScreener, all pools). 24h trading volume $638K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $134K of DEX liquidity across 3 pools. Launch: 731 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd723...b2f1`](https://bscscan.com/address/0xd723f2aea80d1620864ac059f34f168fa223b2f1) |
| **Network** | BNB Chain |
| **Price** | $0.2309 |
| **24h Volume** | $637.2K |
| **Liquidity** | $134.1K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 2y |
| **Top-10 Holders** | 77.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2339 buys / 2267 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc29b6c753b474fa14771e6a51ddb12d596019b45)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kxg-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

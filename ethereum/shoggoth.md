---
token: SHOGGOTH
ticker: SHOGGOTH
network: ethereum
risk_score: 76
status: high
date: 2026-11-03
---

# SHOGGOTH (SHOGGOTH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/shoggoth-eth)

---

## Audit Summary

The SHOGGOTH contract is a standard ERC-20 token with additional tax and transfer restriction features. Ownership has been renounced, effectively disabling administrative functions previously restricted to the owner. However, a separate 'taxWallet' address retains control over fee adjustments and liquidity swapping, which introduces centralized control over the token's economic parameters.

> **Final Recommendation:** Investors should be aware that the taxWallet address maintains significant control over the token's economic flow, including the ability to adjust fees and execute manual swaps. Since ownership is renounced, the community cannot influence these settings, making the taxWallet's behavior the primary factor in the token's economic stability.

We recommend that the taxWallet address be transitioned to a multi-signature wallet or a decentralized DAO contract to mitigate the risk of a single point of failure. Ensure that all future interactions with the taxWallet are transparent to the token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality with clean logic for transfers and approvals. 7.1 Architecture follows a monolithic pattern, while 7.2 Code Security is maintained through the… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic parameters are governed by the taxWallet, which can modify fees and trigger liquidity swaps. 7.5 Governance is non-existent as ownership is renounced, preventing community oversight of… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to the taxWallet's ability to manage fees and swap tokens for ETH. No further changes to the contract logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · ⚪ 7 Informational_

### `CP-05` — Centralized Control over Transfer Execution  *(Severity: Medium · Status: Unresolved)*

The manualSwap function, controlled by the taxWallet, manages the internal state of the contract. If misused, this function could potentially disrupt the token's ability to process transfers or sales by altering the internal swap state.

**Recommendation:** Implement a time-lock or multi-signature requirement for the taxWallet to prevent unilateral changes to the contract's transfer logic.


### `CP-07` — Centralized Fee Adjustment  *(Severity: Medium · Status: Unresolved)*

The taxWallet can modify the buy and sell fees via the reduceFee function. This allows the controller to change the economic cost of trading the token at any time.

**Recommendation:** Establish a clear, public policy or hard-coded limit on the maximum fee that the taxWallet can set to protect users from sudden fee spikes.


### `CP-06` — Dormant Blacklist Functionality  *(Severity: Informational · Status: Unresolved)*

The addBots and delBots functions allow for the blacklisting of specific addresses. Because ownership has been renounced, these functions are effectively locked and cannot be called by anyone.

**Recommendation:** None required, as the renouncement of ownership has rendered these functions permanently inaccessible.


### `CP-08` — Dormant Limit Modification  *(Severity: Informational · Status: Unresolved)*

The removeLimits function allows for the removal of transaction and wallet size restrictions. Since ownership is renounced, this function is now permanently disabled.

**Recommendation:** None required, as the renouncement of ownership has rendered this function permanently inaccessible.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 44.9% of supply. Of that, 26.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.1% in wallets, 9.0% in other contracts. 553 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

553 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $144K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 2 pools. Launch: 847 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc703...f60d`](https://etherscan.io/address/0xc7036bbaf044ac631724acb5c33e24fbc14af60d) |
| **Network** | Ethereum |
| **Price** | $0.00000011 |
| **24h Volume** | $143.8K |
| **Liquidity** | $23.3K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 44.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 411 buys / 318 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x45eb8509ead5e76c8ebdff0c4266e6545731bfa3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/shoggoth-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

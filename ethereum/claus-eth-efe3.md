---
token: claus
ticker: CLAUS
network: ethereum
risk_score: 21
status: low
date: 2026-10-10
---

# claus (CLAUS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/claus-eth-efe3)

---

## Audit Summary

The Claus token contract is an ERC-20 standard implementation with additional administrative controls. Ownership of the contract has been renounced, rendering all owner-restricted functions permanently inactive. This significantly reduces the operational risk from centralized control. Identified issues include a medium-severity `tx.origin` usage and a low-severity division-before-multiplication arithmetic error.

> **Final Recommendation:** For token holders, it is important to understand that while the contract's ownership is renounced, making many administrative controls inactive, there are still inherent technical risks. Be aware of the `tx.origin` vulnerability, which could potentially be exploited by sophisticated attackers if interacting with malicious intermediary contracts. Also, acknowledge the minor rounding losses from division before multiplication in transfers. Always exercise caution when interacting with unknown or untrusted contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements standard ERC-20 functionality. A significant strength is the renounced ownership, which has permanently deactivated numerous powerful administrative functions such as… |
| **Governance / Economics** | 10/10 | Low | A key strength is that the renounced ownership prevents any single entity from unilaterally altering critical economic parameters such as transfer fees (`updateBuyFees`, `updateSellFees`)… |
| **Upgrades** | 10/10 | Low | The Claus contract is not implemented as a proxy and does not include any upgrade mechanisms. This design choice eliminates the risks typically associated with upgradeability, such as malicious… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 97.1% (≈ permanent lock) |
| **LP Locked** | 97.1% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 9 Informational_

### `CD-02` — tx.origin Vulnerability in Transfer Logic  *(Severity: Medium · Status: Unresolved)*

The `_transfer` and `balanceOf` functions use `tx.origin` to determine certain rules or authorizations. `tx.origin` refers to the original external account that initiated a transaction, not necessarily the immediate caller. A malicious contract could trick a user into interacting with it, and then that malicious contract could call the token's `_transfer` function, making it appear as if the user (the `tx.origin`) initiated the transfer directly, potentially bypassing intended access controls or rules.

**Recommendation:** For security-critical operations, `msg.sender` should always be used instead of `tx.origin`. `msg.sender` refers to the immediate caller, preventing intermediary contracts from impersonating the original transaction initiator. Users should exercise caution when interacting with unknown or untrusted contracts.


### `CD-01` — Minor Rounding Loss in Transfers  *(Severity: Low · Status: Unresolved)*

The `_transfer` function performs a division operation before a multiplication when calculating amounts. This order of operations can lead to small rounding losses, meaning a tiny fraction of tokens might be lost during certain calculations, though typically negligible.

**Recommendation:** While the impact is usually minor, it's best practice to perform multiplication before division to maintain precision and avoid rounding errors. For future contracts, ensure arithmetic operations are ordered to minimize precision loss.


### `CP-05` — Dormant Control Over Transfer Switches  *(Severity: Informational · Status: Unresolved)*

The contract *had* functions like `enableTrading`, `removeLimits`, `updateSwapEnabled`, and `disableTransferDelay` that could turn on or off various transfer rules, affecting whether tokens could be bought, sold, or moved. However, because the contract's ownership has been permanently given up (renounced), no one can call these functions anymore. They are now inactive.

**Recommendation:** No action is required as ownership is renounced, rendering these controls permanently inactive. This reduces centralized control risk.


### `CP-07` — Dormant Control Over Transfer Fees  *(Severity: Informational · Status: Unresolved)*

The contract *had* functions such as `updateSellFees` and `updateBuyFees` that allowed the owner to change the fees applied to token transfers. These fees could impact the amount of tokens received by users. However, since the contract's ownership has been renounced, these functions can no longer be called by anyone. The current fee structure is permanently fixed.

**Recommendation:** No action is required as ownership is renounced, rendering these controls permanently inactive. This ensures fee stability.


### `CP-08` — Dormant Control Over Transfer and Wallet Limits  *(Severity: Informational · Status: Unresolved)*

The contract *had* functions like `updateSwapTokensAtAmount`, `updateMaxTxnAmount`, and `updateMaxWalletAmount` that allowed the owner to set limits on transaction sizes or the maximum amount of tokens a wallet could hold. These limits could restrict how users interact with their tokens. However, because the contract's ownership has been renounced, these functions are now permanently inactive and cannot be changed.

**Recommendation:** No action is required as ownership is renounced, rendering these controls permanently inactive. This ensures stability of transaction and wallet limits.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 3.5% of supply. Of that, 2.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 1.2% in wallets, 0.0% in other contracts. 2,287 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,287 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

97.1% of the pool's LP is burned or time-locked. 97.1% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 2.9% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $402K (DexScreener, all pools). 24h trading volume $3.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $402K of DEX liquidity across 1 pools. Launch: 5 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa606...ead1`](https://etherscan.io/address/0xa606d433971e9ee140e234daa7c94c476e10ead1) |
| **Network** | Ethereum |
| **Price** | $0.009035 |
| **24h Volume** | $3.36M |
| **Liquidity** | $401.8K |
| **Volume / Liquidity** | 8.4× |
| **Token Age** | 5d |
| **Top-10 Holders** | 3.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1613 buys / 1583 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc2da8a7f8233112dc5b216de23c4308063eaa631)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/claus-eth-efe3)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*

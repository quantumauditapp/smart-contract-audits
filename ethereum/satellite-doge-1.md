---
token: Satellite Doge-1
ticker: DOGE-1
network: ethereum
risk_score: 44
status: medium
date: 2026-07-29
---

# Satellite Doge-1 (DOGE-1) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/satellite-doge-1-eth)

---

## Audit Summary

The Satellite Doge-1 token contract implements standard ERC-20 functionality with reflection mechanics, high transaction fees, and anti-bot features. A critical finding is the renounced ownership, which renders all administrative functions inaccessible, permanently fixing all contract parameters. This, combined with an unlocked liquidity pool, presents severe economic and operational risks. The high, unchangeable transaction fees are likely to deter trading, and the anti-bot mechanism cannot be managed.

> **Final Recommendation:** Given the renounced ownership and unlocked liquidity, the project carries extremely high risks. It is strongly recommended that potential users exercise extreme caution and understand that all contract parameters are permanently fixed and cannot be adjusted. The unlocked liquidity pool presents a direct and immediate risk of total loss of funds for investors. Users should be aware that the high, unchangeable transaction fees will significantly impact trading profitability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The contract implements standard ERC-20 functionality with `SafeMath` for arithmetic safety (7.2 Code Security). It includes a reflection mechanism and a swap-and-liquify feature, protected by a… |
| **Governance / Economics** | 5/10 | Medium | The economic model features extremely high, fixed transaction fees (25% buy, 45% sell) due to renounced ownership, which will severely deter trading (7.4 Economic). All collected fees are directed to… |
| **Upgrades** | 8/10 | Low | The contract is not designed with any upgradeability mechanism (7.7 Upgrades). This means its logic and parameters are immutable once deployed and ownership is renounced, preventing any future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 2 Critical · 🟠 3 High · 🟡 2 Medium · ⚪ 1 Informational_

### `C-01` — Renounced Ownership Leads to Immutability of Critical Parameters  *(Severity: Critical · Status: Unresolved)*

The provided information indicates that ownership of the contract has been renounced (`ownership_renounced: true`). This means the `_owner` address is set to `address(0)`, rendering all `onlyOwner` functions inaccessible. Consequently, critical parameters such as transaction fees, max transaction/wallet limits, trading status, fee recipient addresses, and the Uniswap router address are permanently fixed to their current values. This prevents any future adjustments, bug fixes, or adaptation to market conditions (7.3 Access Control, 7.8 Operations).

**Recommendation:** This issue is inherent to the renounced ownership state and cannot be resolved without redeploying the contract with a different ownership strategy. Users should be fully aware that the contract is unmanageable and its parameters are immutable.


### `C-02` — Unlocked Liquidity Pool Poses Rug Pull Risk  *(Severity: Critical · Status: Unresolved)*

The prefill data explicitly states `lp_lock_status: unlocked`. This indicates that the liquidity provided to the Uniswap pair is not locked and can be removed by the liquidity provider (likely the deployer or owner) at any time. This creates a severe 'rug pull' vulnerability (7.4 Economic).

**Recommendation:** For any token, especially one with high fees and renounced ownership, locking the liquidity pool is paramount to building trust and preventing a rug pull. Without a locked LP, investors face a high risk of losing all funds. This issue cannot be resolved for the current deployment if ownership is renounced.


### `H-01` — Permanently High Transaction Fees  *(Severity: High · Status: Unresolved)*

Given the renounced ownership, the initial high transaction fees (25% on buy, 45% on sell) are permanently fixed and cannot be adjusted. These extremely high fees will significantly deter trading activity and liquidity. Additionally, both `_developmentAddress` and `_marketingAddress` are set to the same address (`0xA2a86678fd8444b08E850Bcd0c7C93f4c90b2B81`), concentrating all collected fee revenue to a single, unchangeable recipient (7.4 Economic).

**Recommendation:** This issue is a direct consequence of renounced ownership and the initial configuration. It cannot be resolved for the current deployment. Future projects should consider more sustainable fee structures and ensure flexibility for adjustments, or clearly communicate the fixed, high fees to users.


### `H-02` — Unmanageable Anti-Bot Mechanism  *(Severity: High · Status: Unresolved)*

The contract includes an anti-bot mechanism using a `bots` mapping and `_buyMap`. However, due to renounced ownership, the `setBots` function is inaccessible. This means the list of `bots` cannot be updated, nor can legitimate users accidentally added to the `bots` list be removed. If sophisticated bots bypass the mechanism, or if it causes false positives, the contract owner cannot intervene (7.3 Access Control, 7.8 Operations).

**Recommendation:** This issue cannot be resolved for the current deployment. Anti-bot mechanisms are often complex and prone to issues; if implemented, they should be carefully designed and maintainable. Users should be aware of the potential for legitimate transactions to be blocked without recourse.


### `H-03` — Centralized Fee Distribution to a Single Address  *(Severity: High · Status: Unresolved)*

Both the `_developmentAddress` and `_marketingAddress` are configured to be the same address (`0xA2a86678fd8444b08E850Bcd0c7C93f4c90b2B81`). This creates a single point of failure for all collected fees. If this address is compromised or becomes inaccessible, all accumulated fees would be lost or frozen. Furthermore, due to renounced ownership, these addresses cannot be changed (7.4 Economic, 7.8 Operations).

**Recommendation:** For future projects, consider distributing fees to multiple addresses or a multi-signature wallet to mitigate single points of failure. Ensure that fee recipient addresses are secure and, if possible, allow for their modification through a robust governance process. This issue cannot be resolved for the current deployment.


### `M-01` — Fixed Max Transaction and Wallet Size Limits  *(Severity: Medium · Status: Unresolved)*

The contract enforces `_maxTxAmount` and `_maxWalletSize` limits. Due to renounced ownership, these limits are permanently fixed. While intended to prevent large dumps or whale accumulation, such limits can hinder legitimate large transactions and may be circumvented by splitting transactions. Their immutability means they cannot be adjusted to adapt to market dynamics or project growth (7.4 Economic, 7.8 Operations).

**Recommendation:** This issue cannot be resolved for the current deployment. While limits can serve a purpose, they should ideally be adjustable by a trusted entity to maintain flexibility. Users should be aware of these fixed limitations on their trading and holding capacity.


### `M-02` — Potential for Sandwich Attacks on Swap-and-Liquify  *(Severity: Medium · Status: Unresolved)*

The `swapTokensForEth` function performs a swap via Uniswap. While the `lockTheSwap` modifier prevents reentrancy, the swap operation itself can be vulnerable to sandwich attacks. If the `_swapTokensAtAmount` threshold is predictable, front-running bots can manipulate the price around the swap, extracting value and reducing the ETH received by the contract for fee distribution (7.2 Code Security, 7.6 External).

**Recommendation:** Consider implementing anti-sandwich measures such as setting a minimum `amountOutMin` with a reasonable slippage tolerance, or using a more sophisticated swapping mechanism. While difficult to fully prevent, reducing predictability can help. This is a general risk for such automated swap mechanisms.


### `I-01` — Reflection Mechanism Complexity  *(Severity: Informational · Status: Unresolved)*

The contract utilizes a reflection mechanism (`_rOwned`, `_tOwned`, `_rTotal`, `_tTotal`, `tokenFromReflection`, `_getRate`) to distribute fees to holders. While `SafeMath` is used to prevent basic arithmetic overflows, reflection mechanisms are inherently complex. The interaction of varying buy/sell fees with the reflection logic can be difficult to reason about and increases the surface area for subtle bugs (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Thorough testing and formal verification are recommended for complex reflection mechanisms to ensure correct behavior under all scenarios. While no specific vulnerability was identified, complexity always increases risk. Ensure clear documentation of the reflection logic.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc5b0...c105`](https://etherscan.io/address/0xc5b0251dacfab74bc2debaa52072a2a4c939c105) |
| **Network** | Ethereum |
| **Price** | $0.0001655 |
| **24h Volume** | $193.6K |
| **Liquidity** | $53.9K |
| **Volume / Liquidity** | 3.6× |
| **Token Age** | 3y |
| **Top-10 Holders** | 37.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 412 buys / 396 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc0263bdeeeef8eb88f34409a3d58e8b3e17f2fda)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/satellite-doge-1-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-29*

---
token: 4CHAN
ticker: 4CHAN
network: ethereum
risk_score: 7
status: low
date: 2026-08-30
---

# 4CHAN (4CHAN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/4chan-eth)

---

## Audit Summary

The FourChan token contract is an ERC-20 compliant token with reflection mechanics, high transaction taxes, and anti-bot features. A critical vulnerability arises from the renounced ownership, which renders all owner-controlled functions immutable, including critical parameter adjustments and fee management. This severely limits the project's adaptability and ability to respond to market changes or security incidents. Additionally, the contract features aggressive anti-bot measures that could inadvertently block legitimate users and high, irreversible tax rates.

> **Final Recommendation:** Given the renounced ownership, the project's ability to adapt or correct issues is severely limited. It is crucial for users to understand that all owner-controlled parameters, including tax rates and anti-bot mechanisms, are permanently fixed. Future projects should carefully consider the implications of renouncing ownership, especially for highly configurable tokens, and ensure that all critical parameters are set optimally before doing so. If such a design is intentional, clear communication to the community about the immutability of these parameters is essential.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates a structured approach to tokenomics, incorporating reflection and fee mechanisms. It utilizes `SafeMath` for arithmetic operations, although redundant in Solidity 0.8+, and… |
| **Governance / Economics** | 8/10 | Low | The contract's economic model is characterized by high buy (20%) and sell (35%) taxes, which are designed to fund development and marketing (7.4 Economic). However, with ownership renounced, these… |
| **Upgrades** | 9/10 | Low | The FourChan contract is not designed with any upgradeability mechanism (7.7 Upgrades). This means its logic and parameters are immutable once deployed and ownership is renounced. While this… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Renounced Ownership Bricks Critical Functions  *(Severity: Critical · Status: Unresolved)*

The contract's ownership has been renounced, as indicated by the `ownership_renounced: true` prefill data. This renders all functions protected by the `onlyOwner` modifier unusable. These functions include `setTaxFeePercent`, `setRedisFeePercent`, `setMaxTxAmount`, `setMaxWalletSize`, `excludeFromFee`, `includeInFee`, `setDevelopmentAddress`, `setMarketingAddress`, `openTrading`, `setSwapEnabled`, `addBot`, `removeBot`, `addPreTrader`, `removePreTrader`, and `updateBuyMap`. The inability to modify these critical parameters or manage operational aspects means the contract is rigid and cannot adapt to market changes, fix potential issues, or update fee recipients, severely impacting its long-…

**Recommendation:** For future projects, if ownership renunciation is intended, ensure that all critical parameters are optimally configured and thoroughly tested beforehand. Consider implementing a timelock or a multi-signature wallet for critical administrative functions if some level of post-deployment control is desired without full centralization. For this specific contract, given the renounced ownership, this issue is irreversible.


### `H-01` — Irreversible High Tax Rates and Centralized Parameters  *(Severity: High · Status: Unresolved)*

The contract is designed with high buy (20%) and sell (35%) taxes, and critical parameters such as `_maxTxAmount`, `_maxWalletSize`, and fee recipient addresses are controlled by the owner. Given that ownership is renounced, these parameters are now immutable. This means the project cannot adjust to market conditions, reduce taxes, or change fee recipients, which could negatively impact token utility, adoption, and the project's ability to respond to future needs or security concerns (7.4 Economic, 7.5 Governance).

**Recommendation:** For future projects, carefully evaluate the long-term implications of fixed high tax rates and other critical parameters. If ownership is to be renounced, consider a mechanism for community governance or a timelock to allow for parameter adjustments, or ensure that initial parameters are sustainable and acceptable for the project's lifespan. For this contract, these parameters are permanently fixed.


### `M-01` — Aggressive Anti-Bot Mechanism May Block Legitimate Users  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function includes an aggressive anti-bot mechanism: `require(_buyMap[from] == 0 \|\| preTrader[from], "Bot detected");`. This logic prevents any address from making a second buy transaction unless that address is explicitly added to the `preTrader` whitelist by the owner. This could inadvertently block legitimate users who are not `preTrader`s from making subsequent purchases, leading to a poor user experience and potential loss of trust. Furthermore, the `preTrader` list itself is centrally controlled by the owner (7.2 Code Security, 7.3 Access Control).

**Recommendation:** Review the anti-bot mechanism to ensure it does not unfairly penalize legitimate users. Consider alternative, less restrictive anti-bot strategies or implement a more transparent and decentralized process for managing whitelists. Given renounced ownership, this mechanism cannot be modified, so clear communication to users about this restriction is vital.


### `L-01` — Single Address for Development and Marketing Fees  *(Severity: Low · Status: Unresolved)*

Both `_developmentAddress` and `_marketingAddress` are set to the same address (`0xB2e08Df39B176EfB731732664B6E5Ef5b9f43FCD`). While this might be intentional, it centralizes the destination of all collected fees into a single wallet. This increases the single point of failure risk, as compromise of this one address would lead to the loss of all accumulated development and marketing funds (7.4 Economic, 7.8 Operations).

**Recommendation:** For future projects, consider using separate addresses for different fund allocations to diversify risk. Ideally, these addresses would be multi-signature wallets to enhance security. Given renounced ownership, this configuration is immutable for this contract.


### `I-01` — Redundant SafeMath Usage  *(Severity: Informational · Status: Unresolved)*

The contract explicitly uses the `SafeMath` library for arithmetic operations (e.g., `amount.sub(...)`). However, the contract is compiled with Solidity `^0.8.14`, which includes built-in overflow and underflow checks by default. Therefore, the explicit use of `SafeMath` is redundant and adds unnecessary code complexity without providing additional security benefits (7.2 Code Security).

**Recommendation:** For future contracts compiled with Solidity 0.8.0 or higher, `SafeMath` can be safely removed to reduce code size and improve readability, as the compiler handles overflow/underflow checks automatically. This is an informational finding and does not pose a security risk to the current contract.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe0a4...7885`](https://etherscan.io/address/0xe0a458bf4acf353cb45e211281a334bb1d837885) |
| **Network** | Ethereum |
| **Price** | $0. |
| **24h Volume** | $3.4K |
| **Liquidity** | $741.6K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 30.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 147 buys / 56 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4ff4c7c8754127cc097910cf9d80400adef5b65d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/4chan-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

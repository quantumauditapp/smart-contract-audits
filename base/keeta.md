---
token: Keeta
ticker: KTA
network: base
risk_score: 15
status: low
date: 2026-08-11
---

# Keeta (KTA) — Smart Contract Security Analysis | Base

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/keeta-base)

---

## Audit Summary

The audited contract implements an ERC20 token with a dynamic, time-decaying tax mechanism and integrates with Aerodrome for liquidity provision. It utilizes OpenZeppelin's Ownable, ERC20Permit, ReentrancyGuard, and SafeERC20 libraries, enhancing security. Key functionalities include initial token minting to the contract, a tax applied to transfers, and a function to create and fund an Aerodrome liquidity pool. The primary concern identified is the transfer of all initial LP tokens to a single tax recipient, concentrating control over the pool's liquidity.

> **Final Recommendation:** It is recommended to carefully review the implications of transferring all initial LP tokens to the `_taxRecipient` and ensure this aligns with the project's long-term strategy and risk tolerance. Consider documenting this design choice explicitly. Additionally, evaluate the strictness of the `receive` function to ensure it does not hinder future operational needs or recovery scenarios. For all external interactions, ensure the addresses for WETH, Router, and Factory are verified and trusted.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good technical security practices (7.2 Code Security) by inheriting from OpenZeppelin's `ReentrancyGuard` and `SafeERC20`, and implementing a robust `approve` override to… |
| **Governance / Economics** | 5/10 | Medium | The economic model (7.4 Economic) features a dynamic tax that reduces over time, providing a clear mechanism for tokenomics. Slippage control is implemented in `createLiquidityPool` to protect… |
| **Upgrades** | 9/10 | Low | The contract is not designed with an upgradeable proxy pattern (7.7 Upgrades). Therefore, there are no upgrade-related risks such as proxy initialization issues, storage collisions, or logic contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 61.2% |
| **Top-3 Unlocked** | ⚠️ 87.3% |

## Security Findings

_🟠 1 High · 🟢 2 Low · ⚪ 2 Informational_

### `H-01` — Centralization Risk: All Initial LP Tokens Transferred to Single Recipient  *(Severity: High · Status: Unresolved)*

In the `createLiquidityPool` function, after successfully adding liquidity to Aerodrome, all generated LP tokens (`lpBalance`) are transferred to the `_taxRecipient` address via `IERC20(liquidityPool).safeTransfer(_taxRecipient, lpBalance)`. This design choice means that the `_taxRecipient` gains sole control over the initial liquidity pool, including the ability to remove liquidity. This concentrates significant power in a single address, which could be a point of failure or an unexpected outcome for the project deployer if they intended to hold or manage the LP tokens themselves. This impacts 7.1 Architecture, 7.3 Access Control, and 7.4 Economic.

**Recommendation:** Clearly document this design choice and its implications. If this is not the intended behavior, modify the `createLiquidityPool` function to distribute LP tokens to a more decentralized set of addresses (e.g., the deployer, a multisig, or a timelock contract) or to burn a portion. If the `_taxRecipient` is intended to manage the liquidity, ensure it is a secure, multi-signature wallet or a governance-controlled contract.


### `L-01` — Restrictive `receive` Function  *(Severity: Low · Status: Unresolved)*

The `receive` function contains a strict `require(msg.sender == _WETH, "Only accept ETH from WETH")` check. This prevents the contract from receiving direct ETH transfers from any address other than the WETH contract. While this might be an intentional design to enforce specific interaction patterns, it also means that any accidental ETH sent directly to the contract from other sources would be unrecoverable, and it limits the contract's ability to receive ETH for other purposes in the future. This impacts 7.2 Code Security and 7.8 Operations.

**Recommendation:** Evaluate if this strict restriction is absolutely necessary. If the contract might need to receive ETH from other sources (e.g., for donations, future features, or emergency recovery), consider relaxing this restriction or implementing an `onlyOwner` function to withdraw accidentally sent ETH. If the restriction is intentional, ensure it is well-documented.


### `L-02` — Hardcoded Slippage Limit in Liquidity Provision  *(Severity: Low · Status: Unresolved)*

The `createLiquidityPool` function enforces a `maxSlippage` parameter with a hardcoded range of `1-1000` (0.01% to 10%). While providing a slippage control is good practice, a fixed range might not be optimal for all market conditions or liquidity sizes. In highly volatile markets, even 10% slippage might be exceeded, or for very large liquidity additions, a dynamic or configurable slippage might be more appropriate. This impacts 7.4 Economic.

**Recommendation:** Consider making the `maxSlippage` parameter configurable by the owner or through a governance mechanism, allowing for adjustments based on market conditions or operational needs. Alternatively, ensure the current range is sufficient for all anticipated scenarios.


### `I-01` — Misleading Event Name for LP Token Transfer  *(Severity: Informational · Status: Unresolved)*

The `createLiquidityPool` function emits an event named `LPTokensBurned` after transferring LP tokens to the `_taxRecipient`. The term 'burned' typically implies that tokens are sent to an unspendable address (e.g., `address(0)`), effectively removing them from circulation. In this case, the tokens are merely transferred to another active address. This misleading event name could cause confusion for users or off-chain monitoring systems. This impacts 7.2 Code Security.

**Recommendation:** Rename the event to accurately reflect the action, for example, `LPTokensTransferred` or `LPTokensSentToTaxRecipient`, to avoid misinterpretation.


### `I-02` — Time-Based Tax Reduction Using `block.number`  *(Severity: Informational · Status: Unresolved)*

The tax reduction mechanism in `getCurrentTax` relies on `block.number` to determine the passage of time and subsequent tax reductions. While `block.number` is a common and generally acceptable method for time-based logic in smart contracts, it is susceptible to minor manipulation by miners who can slightly influence block production times. For a gradual tax reduction, this is typically not a severe vulnerability, but it means the exact timing of tax changes can be slightly imprecise or influenced. This impacts 7.4 Economic and 7.2 Code Security.

**Recommendation:** For gradual, non-critical time-based events, `block.number` is generally acceptable. No immediate action is required, but be aware of this characteristic if precise timing becomes critical for future features.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc063...8973`](https://basescan.org/address/0xc0634090f2fe6c6d75e61be2b949464abb498973) |
| **Network** | Base |
| **Price** | $0.09398 |
| **24h Volume** | $118.4K |
| **Liquidity** | $4.10M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 67.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 160 buys / 382 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xd9edc75a3a797ec92ca370f19051babebfb2edee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/keeta-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*

---
token: Animecoin
ticker: ANIME
network: ethereum
risk_score: 58
status: medium
date: 2026-08-31
---

# Animecoin (ANIME) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/animecoin-eth)

---

## Audit Summary

The Animecoin contract is an ERC20Permit token with owner-controlled functionality for registering the token on an Arbitrum L2 gateway. The audit identified a high-severity issue regarding potential trapped ETH, a medium-severity issue concerning an unusual view function behavior, and several minor issues. The contract's core ERC20 functionality is robust due to OpenZeppelin inheritance, but specific custom logic introduces notable risks.

> **Final Recommendation:** It is strongly recommended to implement a mechanism for the owner to withdraw excess ETH from the contract to prevent potential loss of funds. The behavior of the `isArbitrumEnabled` function should be reviewed to ensure it aligns with expected external integration patterns, potentially by removing the restrictive `require` statement or providing clear documentation. Furthermore, the owner should exercise extreme caution when calling `registerTokenOnL2`, ensuring all gas and value parameters are precisely calculated to avoid transaction failures or trapping funds.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin ERC20Permit and Ownable implementations, providing a solid foundation for token functionality (7.2 Code Security). The architecture integrates with… |
| **Governance / Economics** | 1/10 | High | The contract employs a simple `Ownable` access control model, granting the deployer exclusive rights to critical functions like `registerTokenOnL2` (7.5 Governance). This centralized control is… |
| **Upgrades** | 6/10 | Medium | The Animecoin contract is not designed with an upgradeability pattern (7.7 Upgrades). This means its logic is immutable once deployed, eliminating risks associated with proxy implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Missing ETH Withdrawal Mechanism for Owner  *(Severity: High · Status: Unresolved)*

The `registerTokenOnL2` function is payable and forwards `valueForGateway` and `valueForRouter` to external Arbitrum gateway contracts. If the `msg.value` sent to `registerTokenOnL2` by the owner exceeds the sum of `valueForGateway` and `valueForRouter`, the excess ETH will remain in the `Animecoin` contract. There is no owner-controlled function to withdraw this trapped ETH, leading to a permanent loss of funds for the owner.

**Recommendation:** Implement a dedicated `withdrawETH` function, restricted to the `onlyOwner` role, allowing the owner to recover any excess ETH sent to the contract. This function should transfer the contract's balance to a specified address.


### `M-01` — Unusual `isArbitrumEnabled` View Function Behavior  *(Severity: Medium · Status: Unresolved)*

The `isArbitrumEnabled` view function is guarded by `require(shouldRegisterGateway, "NOT_EXPECTED_CALL")`. The `shouldRegisterGateway` flag is only set to `true` temporarily during the execution of the `registerTokenOnL2` function. This means that `isArbitrumEnabled()` will almost always revert when called directly or by external systems outside of the specific L2 registration process, which is unexpected for a public view function and could cause integration issues or confusion.

**Recommendation:** Re-evaluate the necessity of the `shouldRegisterGateway` check within `isArbitrumEnabled`. If the intent is to only allow this function to be called during registration, this design is highly restrictive. Consider removing the `require` statement to allow the function to always return its intended value, or provide clear documentation on its intended usage and limitations.


### `L-01` — Reliance on External Arbitrum Bridge Parameters  *(Severity: Low · Status: Unresolved)*

The `registerTokenOnL2` function requires the owner to provide several complex parameters (`maxSubmissionCostForCustomGateway`, `maxSubmissionCostForRouter`, `maxGasForCustomGateway`, `maxGasForRouter`, `gasPriceBid`, `valueForGateway`, `valueForRouter`) for the Arbitrum bridge calls. Incorrectly calculated or provided values for these parameters could lead to failed L2 registration transactions, wasted gas, or trapped funds if `value` is too high and not fully consumed (as noted in H-01). This places a significant operational burden on the owner.

**Recommendation:** Provide comprehensive documentation and clear guidelines for the owner on how to correctly calculate and provide these Arbitrum-specific parameters. Consider adding sanity checks within the contract, if feasible, to validate parameter ranges or relationships, although this might be complex given the dynamic nature of gas prices and submission costs.


### `I-01` — Hardcoded Arbitrum Enabled Return Value  *(Severity: Informational · Status: Unresolved)*

The `isArbitrumEnabled` function returns `uint8(0xb1)`. While `0xb1` is a specific and known constant used by Arbitrum for custom tokens, its direct hardcoding as a magic number without an explicit constant definition or comment can reduce code readability and maintainability. Future changes to Arbitrum's protocol might require updating this value, which would be less clear without a named constant.

**Recommendation:** Define `0xb1` as a named constant (e.g., `uint8 public constant ARBITRUM_ENABLED_VALUE = 0xb1;`) and use this constant in the `isArbitrumEnabled` function. This improves readability and makes the code easier to understand and maintain.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4dc2...c277`](https://etherscan.io/address/0x4dc26fc5854e7648a064a4abd590bbe71724c277) |
| **Network** | Ethereum |
| **Price** | $0.002767 |
| **24h Volume** | $2.5K |
| **Liquidity** | $143.9K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 306 buys / 270 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x38fa0e36a9eb335ca00dbd6d0f203b0bd72ce3b6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/animecoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*

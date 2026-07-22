---
token: Surplus Intelligence
ticker: SURPLUS
network: base
risk_score: 84
status: critical
date: 2026-07-22
---

# Surplus Intelligence (SURPLUS) — Smart Contract Security Analysis | Base

> **Risk Score: 84/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/surplus-intelligence-base)

---

## Audit Summary

The DERC20 contract implements an ERC20 token with voting, permit, vesting, and inflation mechanisms. It leverages OpenZeppelin libraries for core functionalities. The audit identified a high level of centralization, a potential denial of service vulnerability in the inflation mechanism, and several informational findings related to design choices. The contract is not upgradeable, which implies a high cost for future modifications.

> **Final Recommendation:** It is highly recommended to implement a robust multi-signature wallet for the contract's ownership to mitigate the risks associated with centralized control and a single point of failure. The `mintInflation` function should be called regularly to prevent the `while` loop from growing excessively large, or consider refactoring the inflation calculation to avoid unbounded loops. All critical design choices, especially those related to owner privileges and immutability, should be thoroughly documented and communicated to users.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The DERC20 contract leverages battle-tested OpenZeppelin libraries for ERC20, ERC20Votes, ERC20Permit, and Ownable functionalities, enhancing code security and adherence to standards (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The contract design grants substantial control to the `owner` address, which can update the yearly mint rate, burn tokens, and lock/unlock the liquidity pool, introducing a high degree of… |
| **Upgrades** | 5/10 | Medium | The DERC20 contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). This design choice means that any future modifications or bug fixes would necessitate a complete… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants the deployer (owner) significant power over the DERC20 token. The owner can mint inflation tokens to themselves, burn tokens from their own address, update the yearly mint rate (up to 2%), and lock/unlock the designated liquidity pool. This level of centralization introduces a single point of failure and a high trust assumption, which can be a significant economic risk for token holders (7.3 Access Control, 7.4 Economic, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the contract's ownership to distribute control and require multiple approvals for sensitive operations. Clearly document the extent of owner privileges and the associated risks to users.


### `M-01` — Potential Denial of Service in `mintInflation`  *(Severity: Medium · Status: Unresolved)*

The `mintInflation` function contains a `while` loop that iterates for each full year that has passed since `currentYearStart`. If the `mintInflation` function is not called for an extended period (e.g., many years), this loop could iterate a large number of times, potentially causing the transaction to exceed the block gas limit and revert. This would prevent the owner from minting inflation tokens and disrupt the intended tokenomics (7.2 Code Security, 7.8 Operations).

**Recommendation:** The owner should ensure `mintInflation` is called regularly (e.g., at least once a year) to prevent the loop from becoming too long. Alternatively, consider refactoring the inflation calculation to avoid an unbounded `while` loop, perhaps by calculating the total inflation up to `block.timestamp` in a single step, or by limiting the number of years processed per transaction.


### `L-01` — Misleading Error Message in `releaseVestedTokens`  *(Severity: Low · Status: Unresolved)*

The `releaseVestedTokens` function uses `require(amount > 0, NoMintableAmount());` when the calculated `amount` of vested tokens available for release is zero. The error `NoMintableAmount()` is semantically incorrect in the context of releasing already existing vested tokens, as it implies minting new tokens rather than releasing. A more appropriate error message would improve clarity for users (7.2 Code Security).

**Recommendation:** Change the error message to something more descriptive, such as `NoVestedAmountToRelease()` or `VestingPeriodNotReached()` to accurately reflect the condition.


### `I-01` — Immutability of Vesting Schedule  *(Severity: Informational · Status: Unresolved)*

The `vestingStart`, `vestingDuration`, and `vestedTotalAmount` variables are declared as `immutable` and are set only once in the constructor. This design choice fixes the overall vesting schedule and the total amount of tokens designated for vesting at deployment. While this provides certainty and prevents tampering, it lacks flexibility for future adjustments to the vesting program if circumstances change (7.1 Architecture).

**Recommendation:** Ensure that the immutability of the vesting schedule aligns with the long-term project vision. If future flexibility is desired, consider an upgradeable contract pattern or a separate vesting contract with configurable parameters.


### `I-02` — Constructor Pre-Minting Limits Tied to `initialSupply`  *(Severity: Informational · Status: Unresolved)*

The `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` limits for pre-minting are calculated as a percentage of `initialSupply` within the constructor. If `initialSupply` is zero or very small, these limits could effectively become zero, preventing any pre-minting even if it was intended as part of the initial token distribution (7.1 Architecture).

**Recommendation:** Verify that the `initialSupply` value used during deployment is sufficient to allow for the desired pre-minting amounts. Clearly document this dependency and its implications for future deployments or initializations.


### `I-03` — `vestedTokens < initialSupply` Requirement in Constructor  *(Severity: Informational · Status: Unresolved)*

The constructor includes a `require(vestedTokens < initialSupply, MaxTotalVestedExceeded(vestedTokens, initialSupply));` check. This design choice explicitly prevents the entire `initialSupply` from being allocated to vesting. While this might be an intentional design constraint to ensure some initial liquid supply, it's a specific limitation that should be clearly understood and documented (7.1 Architecture).

**Recommendation:** Ensure this design constraint is intentional and clearly documented. If the project ever intends to fully vest the initial supply, this `require` statement would need to be removed or modified in a new deployment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc52a...cba3`](https://basescan.org/address/0xc52aedec3374422d7510e294cfaa90799595cba3) |
| **Network** | Base |
| **Price** | $0.00004194 |
| **24h Volume** | $205.2K |
| **Liquidity** | $1.42M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 36.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1094 buys / 171 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xfc25fdd217e288d03a877f0b7d49e0bbe52b2288c88de929125062569fc7eb2a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/surplus-intelligence-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*

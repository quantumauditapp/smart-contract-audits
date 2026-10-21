---
token: 1claw AI
ticker: 1CLAWAI
network: base
risk_score: 74
status: high
date: 2026-09-13
---

# 1claw AI (1CLAWAI) — Smart Contract Security Analysis | Base

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/1claw-ai-base)

---

## Audit Summary

The DERC20 token contract implements standard ERC20 functionalities, along with custom features for vesting, inflationary minting, and a pool locking mechanism. The contract leverages well-audited OpenZeppelin libraries for its core components. Key findings include potential denial of service and integer overflow risks within the `mintInflation` function, which are critical for the token's long-term economic stability. Centralized control over the pool locking mechanism and vesting start time also present notable risks. Recommendations focus on mitigating these technical and centralization concerns.

> **Final Recommendation:** Prioritize addressing the `mintInflation` function's vulnerabilities by implementing safer arithmetic to prevent integer overflows and restructuring the loop to avoid denial-of-service risks. Review the centralized control points, particularly the pool locking mechanism, and consider implementing timelocks or multi-signature requirements for critical administrative actions to enhance security and decentralization. Additionally, improve transparency by emitting events for all significant state changes to facilitate better monitoring and auditing.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The DERC20 contract is built upon robust OpenZeppelin standards (ERC20, ERC20Votes, ERC20Permit, Ownable), providing a solid foundation for token operations (7.1 Architecture). The custom vesting and… |
| **Governance / Economics** | 3/10 | High | The contract operates under an `Ownable` access control model, granting the owner significant power over key parameters (7.5 Governance). The owner can set and update the `yearlyMintRate`, control… |
| **Upgrades** | 4/10 | Medium | The DERC20 contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, it does not inherit the specific upgradeability risks associated with proxy patterns, such as storage collisions… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 85.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Denial of Service in `mintInflation()` due to unbounded loop  *(Severity: High · Status: Unresolved)*

The `mintInflation()` function contains a `while` loop that iterates for each full year passed since the last minting: `while (block.timestamp > currentYearStart_ + 365 days)`. If this function is not called for an extended period (e.g., several years), the loop could iterate many times, potentially consuming excessive gas and causing the transaction to revert due to an out-of-gas error. This would prevent the owner from minting inflation tokens, disrupting the token's intended economic model (7.2 Code Security, 7.8 Operations).

**Recommendation:** Implement a mechanism to cap the number of iterations per transaction or allow for partial minting over multiple transactions. Consider storing the `mintableAmount` and `currentYearStart` in a way that allows for claiming in chunks or limits the number of years processed at once to ensure the function remains callable under all circumstances.


### `H-02` — Potential Integer Overflow in `mintInflation()` Calculation  *(Severity: High · Status: Unresolved)*

The `mintInflation()` function calculates `yearMint` and `partialYearMint` using multiplication before division: `(supply * yearlyMintRate_ * timeLeftInCurrentYear) / (1 ether * 365 days)`. While `uint256` has a large maximum value, if the `supply` grows to an extremely large number (e.g., `2 * 10^53` tokens with 18 decimals), the intermediate product `supply * yearlyMintRate_ * timeLeftInCurrentYear` could exceed `uint256` maximum, leading to an integer overflow and incorrect minting amounts. This could result in an unexpected token supply or a denial of service if the transaction reverts (7.2 Code Security, 7.4 Economic).

**Recommendation:** Reorder operations to perform division earlier or use a fixed-point math library to prevent intermediate overflow. For example, restructure the calculation to `(supply / (1 ether)) * yearlyMintRate_ * (timeLeftInCurrentYear / (365 days))` or similar, ensuring intermediate values remain within `uint256` limits.


### `M-01` — Centralized Control over Pool Locking  *(Severity: Medium · Status: Unresolved)*

The `lockPool()` and `unlockPool()` functions, callable only by the contract owner, allow the owner to arbitrarily pause or resume transfers to a specific `pool` address. This introduces a significant centralization risk, as the owner can unilaterally disrupt liquidity or interactions with a designated DeFi pool. While potentially useful for emergencies or controlled rollouts, this power could be misused or become a single point of failure for critical integrations (7.3 Access Control, 7.5 Governance).

**Recommendation:** Clearly document the intended use cases and limitations of this feature. To mitigate centralization risk, consider implementing a timelock for `lockPool()`/`unlockPool()` operations or requiring multi-signature approval for such critical actions.


### `M-02` — Vesting Start Time Dependency on Deployment  *(Severity: Medium · Status: Unresolved)*

The `vestingStart` variable is set to `block.timestamp` in the constructor, meaning vesting begins immediately upon contract deployment. This design choice ties the vesting schedule directly to the deployment time, which might not always align with the project's intended vesting start date, especially if there are unforeseen delays in ecosystem setup or initial token distribution. This could lead to vesting starting earlier or later than desired (7.4 Economic, 7.8 Operations).

**Recommendation:** Consider allowing `vestingStart` to be set by the owner after deployment, perhaps with a timelock, or by a governance mechanism. This would provide greater flexibility and control over the vesting schedule, allowing for better coordination with project milestones. Alternatively, ensure precise coordination of contract deployment with the desired vesting start.


### `L-01` — Lack of Event Emission for Critical State Changes  *(Severity: Low · Status: Unresolved)*

Several critical state-changing functions, including `lockPool()`, `unlockPool()`, `updateMintRate()`, and `updateTokenURI()`, do not emit events. While the `Ownable` contract emits `OwnershipTransferred`, changes to these specific parameters are not logged on-chain. This makes it difficult for off-chain monitoring tools, users, and auditors to track important administrative actions and verify the contract's current configuration, reducing transparency (7.2 Code Security, 7.8 Operations).

**Recommendation:** Emit specific events for all critical state changes. For example: `event PoolLocked(address indexed pool, bool isLocked);`, `event MintRateUpdated(uint256 oldRate, uint256 newRate);`, and `event TokenURIUpdated(string newURI);`.


### `L-02` — `burn()` function burns from owner's balance  *(Severity: Low · Status: Unresolved)*

The `burn()` function, callable only by the owner, burns tokens from `owner()`'s balance (`_burn(owner(), amount)`). If the intention was for the owner to burn tokens held by the contract itself (e.g., unvested tokens or tokens sent to the contract by mistake), the current implementation would not achieve this directly without the owner first transferring those tokens to their own address. This might lead to confusion or require additional steps for certain burning scenarios (7.2 Code Security, 7.8 Operations).

**Recommendation:** Clarify the intended use of the `burn()` function. If the goal is to allow the owner to burn tokens held by the contract, modify the function to `_burn(address(this), amount);` or provide a separate function for that specific purpose. If the current behavior is intended, ensure it is clearly documented.


### `I-01` — Unused `Nonces` import  *(Severity: Informational · Status: Unresolved)*

The contract imports `Nonces` from `@openzeppelin/utils/Nonces.sol` but does not explicitly inherit from it. The `ERC20Permit` contract, which `DERC20` already inherits from, itself inherits from `Nonces`. Therefore, the direct import of `Nonces` in `DERC20.sol` is redundant and can be removed without affecting functionality (7.2 Code Security).

**Recommendation:** Remove the redundant `import { Nonces } from "@openzeppelin/utils/Nonces.sol";` statement to improve code clarity and reduce unnecessary dependencies.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x61d9...dba3`](https://basescan.org/address/0x61d91cff0fc9fbbdb89f505cf8a7422bf95fdba3) |
| **Network** | Base |
| **Price** | $0.00000373 |
| **24h Volume** | $39.8K |
| **Liquidity** | $161.9K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 53.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 120 buys / 235 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xf80335f8d6ba2a5970474a236bec053a65de6ca6fa1cd1f80086d843fef112bb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/1claw-ai-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*

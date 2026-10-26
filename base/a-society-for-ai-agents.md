---
token: A Society For AI Agents
ticker: 1F916
network: base
risk_score: 33
status: low
date: 2026-09-15
---

# A Society For AI Agents (1F916) — Smart Contract Security Analysis | Base

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/a-society-for-ai-agents-base)

---

## Audit Summary

The audit covers the DopplerERC20V1 implementation contract, which functions as an ERC20 token with vesting capabilities, a balance limit mechanism, and a pool locking feature. The contract utilizes Solady libraries for efficiency and security. A significant economic risk was identified regarding the interpretation of pre-mint limits, potentially allowing for highly concentrated initial token distribution. Centralized control by the owner and controller roles also presents a medium risk. The core vesting logic was partially truncated in the provided source, limiting a full assessment of these critical functions.

> **Final Recommendation:** It is recommended to review the constants `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` to ensure their intended behavior aligns with the project's token distribution strategy, potentially adjusting them to absolute values rather than percentages of `initialSupply`. Consider implementing a multi-signature wallet for the `owner` and `controller` roles to mitigate the risks associated with centralized control over critical contract functions. Ensure the full, untruncated source code, especially for core vesting logic, is thoroughly reviewed to confirm its correctness and security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The DopplerERC20V1 contract is built on robust Solady libraries, enhancing code quality and gas efficiency (7.2 Code Security). It correctly implements the Initializable pattern for proxy… |
| **Governance / Economics** | 5/10 | Medium | The contract features a vesting mechanism to distribute tokens over time and a temporary balance limit to manage initial token concentration (7.4 Economic). However, the interpretation of… |
| **Upgrades** | 7/10 | Low | The DopplerERC20V1 contract is designed as an upgradeable implementation using Solady's Initializable pattern, correctly disabling initializers in the constructor and using an `initialize` function… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 54.4% |
| **Top-3 Unlocked** | ⚠️ 80.7% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control Over Critical Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract grants significant control to single addresses for critical operations. The `owner` (an `Ownable` role) can `lockPool`, `unlockPool`, and `updateTokenURI`. The `controller` address, set during initialization, can `disableBalanceLimit`. These centralized roles represent single points of failure and could be exploited if the private keys are compromised, leading to potential manipulation of the token's operational state or economic parameters (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `owner` and `controller` roles. This would require multiple approvals for critical actions, significantly reducing the risk associated with a single point of compromise. Alternatively, explore time-locks or community governance mechanisms for highly sensitive operations.


### `M-02` — High Pre-Mint Allocation Limits  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constants `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` are defined as `0.8 ether`. In the `initialize` function, these are used to calculate `maxPreMintPerAddress` and `maxTotalPreMint` as `initialSupply * CONSTANT_WAD / WAD`. This calculation effectively sets the limits to 80% of the `initialSupply`. This means a single beneficiary can be allocated up to 80% of the total initial supply, and the total pre-minted amount across all beneficiaries can also be up to 80% of the initial supply. This could lead to an unintended highly concentrated initial token distribution, undermining decentralization goal

**Recommendation:** Clarify the intended purpose of `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD`. If these are meant to be absolute token amounts, they should be used directly without multiplying by `initialSupply` and dividing by `WAD`. If they are intended as percentages, consider if 80% is an appropriate and safe limit for initial distribution. Adjust these constants or the calculation logic to reflect the desired maximum allocation per address and total pre-minted amount.


### `L-01` — Reliance on block.timestamp for Vesting  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The vesting calculations and `balanceLimitEnd` rely on `block.timestamp`. While standard practice, `block.timestamp` can be manipulated by miners within a small window (up to 900 seconds on Ethereum, similar on other EVM chains) to slightly influence vesting schedules or the balance limit expiry. This could potentially be exploited for minor time-sensitive advantages (7.6 External).

**Recommendation:** For critical time-sensitive operations, consider using a decentralized oracle for time if precise, unmanipulable time is paramount. For vesting and balance limits, `block.timestamp` is generally acceptable, but acknowledge the inherent minor risk. Ensure that any time-sensitive actions do not have severe consequences if slightly delayed or accelerated by miner manipulation.


### `I-01` — Truncated Core Vesting Logic  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `DopplerERC20V1` contract was truncated, specifically omitting the full implementation of the `_available` and `_releaseAllFor` internal functions. These functions are critical for correctly calculating and releasing vested tokens. Without the complete code, a thorough security assessment of the core vesting logic cannot be performed, impacting the overall confidence in the audit of this functionality (7.2 Code Security).

**Recommendation:** Provide the complete, untruncated source code for all contract functions, especially those central to the contract's primary functionality (e.g., vesting calculations and releases). A full review of these functions is essential to ensure their correctness, prevent calculation errors, and identify potential reentrancy or other vulnerabilities.


### `I-02` — Short Minimum Vesting Duration  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constant `MIN_VESTING_DURATION` is set to `1 days`. This is a relatively short minimum duration for vesting schedules, meaning tokens can become available for release very quickly after the vesting start. While this might be an intentional design choice, it reduces the long-term holding incentive typically associated with vesting (7.4 Economic).

**Recommendation:** Confirm that a minimum vesting duration of 1 day aligns with the project's tokenomics and distribution strategy. If the intention is to encourage longer-term commitment or prevent immediate token dumps, consider increasing this minimum duration.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9e00...7ba3`](https://basescan.org/address/0x9e00fc92493451eba1c63dd3880d68b622037ba3) |
| **Network** | Base |
| **Price** | $0.00003519 |
| **24h Volume** | $356.3K |
| **Liquidity** | $585.9K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 43.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 636 buys / 983 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x24ecedb296899f0110dce5cfdd9c9dd74b2b11a21dee752e085f93c700c7fccb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/a-society-for-ai-agents-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*

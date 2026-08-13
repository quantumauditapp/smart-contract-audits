---
token: Metronome Synth ETH
ticker: MSETH
network: base
risk_score: 55
status: high
date: 2026-08-13
---

# Metronome Synth ETH (MSETH) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metronome-synth-eth-base)

---

## Audit Summary

The SyntheticToken contract serves as an upgradeable ERC-20 token implementation, integrating with a broader DeFi ecosystem including a PoolRegistry, Pools, DebtTokens, ProxyOFT, and an AMO. The contract leverages OpenZeppelin's upgradeable patterns and Solidity 0.8.24's default overflow/underflow checks, enhancing its robustness. Key strengths include a well-defined access control system for core operations and the use of custom error messages. However, the audit identified a high reliance on the security and correct functioning of external contracts for critical token operations (minting, burning, seizing), which introduces significant external dependency risk. Additionally, the default unbounded `maxTotalSupply` could pose economic risks if not managed by other protocol layers.

> **Final Recommendation:** It is recommended to thoroughly audit all external contracts that interact with the `SyntheticToken`, especially those granted minting, burning, or seizing permissions (ProxyOFT, AMO, Pool, DebtToken, PoolRegistry), to ensure their security and correct behavior. Consider implementing a more restrictive default `maxTotalSupply` or clearly documenting the intended management of this parameter if it is designed to be unbounded. For improved user experience and debugging, consider adding specific custom error messages for all critical revert conditions, such as `amoSupply` underflow.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The SyntheticToken contract demonstrates good technical practices, utilizing OpenZeppelin's `Initializable` for upgradeability and custom error types for efficient error handling. Solidity 0.8.24's… |
| **Governance / Economics** | 1/10 | High | The economic model incorporates various supply limits (`maxAmoSupply`, `maxBridgedInSupply`, `maxBridgedOutSupply`) and a governor-controlled `PoolRegistry` for managing critical parameters (7.4… |
| **Upgrades** | 1/10 | High | The contract is deployed behind a `TransparentUpgradeableProxy` and correctly uses OpenZeppelin's `Initializable` pattern, including `_disableInitializers()` in the constructor and the `initializer`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — High Reliance on External Contracts for Core Logic and Access Control  *(Severity: High · Status: Unresolved)*

The `SyntheticToken` contract delegates critical minting, burning, and seizing capabilities to external contracts (ProxyOFT, AMO, Pool, DebtToken) via the `onlyIfCanBurn`, `onlyIfCanMint`, and `onlyIfCanSeize` modifiers. These modifiers involve multiple external calls to `_poolRegistry`, `IManageable`, `IPool`, and `IDebtToken` to verify the sender's role. This architecture introduces a high degree of trust in the security and correct functioning of these external contracts and the `PoolRegistry`. A vulnerability or misconfiguration in any of these dependent contracts could directly lead to unauthorized minting, burning, or seizing of the synthetic token, compromising its supply and value.

**Recommendation:** Conduct comprehensive security audits of all external contracts that are granted privileged access to the `SyntheticToken`'s core functions. Implement robust monitoring and incident response plans for these interconnected components. Consider adding circuit breakers or emergency pause mechanisms that can be triggered by the `governor` in case of a compromise in a dependent external contract.


### `M-01` — Default Unbounded `maxTotalSupply`  *(Severity: Medium · Status: Unresolved)*

The `initialize` function sets `maxTotalSupply = type(uint256).max;`. This means, by default, there is no effective upper limit on the total supply of the synthetic token. While the contract includes `maxAmoSupply`, `maxBridgedInSupply`, and `maxBridgedOutSupply` limits, the overall `maxTotalSupply` being unbounded could lead to unexpected economic scenarios if not carefully managed by other protocol mechanisms or if the intention was to have a configurable global cap. If `maxTotalSupply` is intended to be a configurable limit, it should be set to a reasonable initial value rather than `type(uint256).max`.

**Recommendation:** If a global maximum total supply is desired, set `maxTotalSupply` to a specific, reasonable value during initialization or provide a dedicated `onlyGovernor` function to set it post-deployment. If the unbounded nature is intentional, ensure that the economic implications are fully understood and that other protocol layers adequately manage the overall supply without relying on this variable.


### `I-01` — Lack of Specific Error for `amoSupply` Underflow  *(Severity: Informational · Status: Unresolved)*

When `_isMsgSenderAmo(_msgSender)` is true in the `_burn` function, `amoSupply -= amount_` is executed. In Solidity 0.8.24, this operation will revert if `amoSupply < amount_` due to default overflow/underflow checks. However, unlike `BurnAmountExceedsBalance()` which is explicitly checked for `balanceOf[account_]`, there is no specific custom error for `amoSupply` underflow. This could lead to a less clear error message for users or integrators if an AMO attempts to burn more than its allocated supply.

**Recommendation:** Consider adding an explicit `require(amoSupply >= amount_, 'AmoSupplyExceedsBalance')` or a custom error check before the `amoSupply -= amount_` operation to provide a more specific and user-friendly error message in case of an underflow.


### `I-02` — Unused `VERSION` Constant  *(Severity: Informational · Status: Unresolved)*

The `VERSION` constant is declared but not referenced anywhere within the provided contract code. While not a security vulnerability, it represents dead code and could be removed to slightly reduce contract size and improve clarity, or utilized for on-chain version tracking.

**Recommendation:** Either remove the `VERSION` constant if it serves no functional purpose, or integrate it into a function (e.g., a `version()` public view function) to provide on-chain version information for external tools or users.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7ba6...8c98`](https://basescan.org/address/0x7ba6f01772924a82d9626c126347a28299e98c98) |
| **Network** | Base |
| **Price** | $1,327.6500 |
| **24h Volume** | $492.9K |
| **Liquidity** | $1.96M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 197 buys / 317 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x00145e8fc9f06a0b71bd57fefbf451ec1db9d69f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metronome-synth-eth-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*

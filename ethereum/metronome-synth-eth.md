---
token: Metronome Synth ETH
ticker: MSETH
network: ethereum
risk_score: 41
status: medium
date: 2026-09-01
---

# Metronome Synth ETH (MSETH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metronome-synth-eth-eth)

---

## Audit Summary

The SyntheticToken contract serves as an ERC-20 compliant token implementation for a TransparentUpgradeableProxy, integrating with a broader DeFi ecosystem including PoolRegistry, Pools, DebtTokens, ProxyOFT, and AMO. The contract features robust access control mechanisms, extensive error handling, and adheres to OpenZeppelin's upgradeability patterns. However, significant reliance on external contracts for core access control decisions introduces a critical dependency risk. Additionally, the provided code snippet for the `_mint` function is incomplete, preventing a full security assessment of its supply management logic. The default initialization of `maxTotalSupply` to its maximum possible value also warrants attention.

> **Final Recommendation:** Prioritize a comprehensive review of the external contracts (`IPoolRegistry`, `IPool`, `IDebtToken`, `IProxyOFT`, `Amo`) that directly influence the access control and economic integrity of the SyntheticToken. Ensure their security and trustworthiness are thoroughly established. Complete the audit of the full `_mint` function implementation to verify all supply management logic and limits. Consider implementing a more restrictive default `maxTotalSupply` or clearly documenting the rationale for its current unbounded state, alongside a robust governance process for its adjustment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates good technical practices, including comprehensive custom error handling and safe arithmetic operations using `unchecked` blocks after validation checks (7.2 Code Security).… |
| **Governance / Economics** | 2/10 | High | The contract implements granular access control through modifiers like `onlyGovernor`, `onlyIfCanBurn`, `onlyIfCanMint`, and `onlyIfCanSeize`, restricting sensitive operations to specific roles or… |
| **Upgrades** | 1/10 | High | The contract correctly utilizes OpenZeppelin's `Initializable` pattern, including `_disableInitializers()` in the constructor and an `initializer` modifier for the `initialize` function (7.7… |

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

_🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Incomplete `_mint` Function Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `_mint` function is truncated. This prevents a complete security assessment of its implementation, particularly regarding how `totalSupply`, `balanceOf`, `totalBridgedIn`, `amoSupply`, and various `maxSupply` limits (`maxTotalSupply`, `maxAmoSupply`, `maxBridgedInSupply`) are managed. Without the full code, it's impossible to verify the correctness of its arithmetic, access control, and adherence to the protocol's economic rules (7.2 Code Security, 7.4 Economic).

**Recommendation:** Provide the complete and untruncated source code for the `_mint` function for a thorough security review. Ensure that all relevant supply limits are checked before minting, and that `totalSupply`, `balanceOf`, and other related state variables are updated correctly and safely, preventing overflows and adhering to the intended economic model.


### `M-02` — `maxTotalSupply` Initialized to `type(uint256).max`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `initialize` function, the `maxTotalSupply` variable is set to `type(uint256).max`. This effectively means there is no upper limit on the total supply of the synthetic token by default. While other specific limits like `maxBridgedInSupply` and `maxAmoSupply` exist, the overall `totalSupply` is not capped. This design choice could lead to unexpected inflation or economic instability if the various minting mechanisms are not sufficiently constrained by other means, or if the intention was to have a more restrictive total supply limit (7.4 Economic).

**Recommendation:** Review the economic model and confirm if an unbounded `maxTotalSupply` is the intended design. If a cap is desired, set a specific `maxTotalSupply` value during initialization or provide a clear governance mechanism for setting and updating this limit. If it is intentionally unbounded, ensure that all individual minting paths (e.g., via `ProxyOFT`, `Amo`, `Pool`, `DebtToken`) have sufficient and robust checks to prevent excessive supply creation.


### `M-03` — Critical External Dependency Risk in Access Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_isMsgSenderDebtToken` and `_isMsgSenderPool` functions, which are integral to the `onlyIfCanBurn`, `onlyIfCanMint`, and `onlyIfCanSeize` modifiers, rely on external calls to `IPoolRegistry`, `IPool`, and `IDebtToken` contracts. These external calls determine if a sender has permission to perform critical operations like minting, burning, or seizing tokens. If any of these external contracts are compromised, or if their logic can be manipulated (e.g., by registering a malicious pool/debt token or returning misleading information), the access control of the SyntheticToken could be bypassed, leading to unauthorized

**Recommendation:** Implement robust validation and trust mechanisms for all external contract interactions. Consider adding a whitelist for trusted PoolRegistry, Pool, and DebtToken addresses, or implementing circuit breakers. Thoroughly audit all integrated external contracts to ensure their security and resistance to manipulation. Document the trust assumptions and potential attack vectors related to these external dependencies.


### `L-01` — Broad Access for Mint and Burn Operations  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `onlyIfCanBurn` and `onlyIfCanMint` modifiers grant permission to `ProxyOFT`, `Amo`, `Pool`, and `DebtToken` contracts to perform mint and burn operations. While this is likely by design to facilitate the protocol's functionality, it means that a significant number of external entities have direct control over the synthetic token's supply. The security and integrity of these external contracts are paramount, as a compromise in any of them could lead to unauthorized token issuance or destruction (7.3 Access Control, 7.4 Economic).

**Recommendation:** Ensure that all external contracts authorized to mint or burn tokens are subject to the highest security standards, including regular audits and robust operational security. Implement monitoring for unusual minting/burning activity from these addresses. Clearly document the roles and responsibilities of each authorized entity and the potential impact of their compromise.


### `L-02` — `seize` Function Grants Powerful Transfer Capability  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `seize` function allows entities identified by `onlyIfCanSeize` (i.e., `Pool` and `DebtToken` contracts) to transfer tokens from any `from_` address to any `to_` address without requiring prior approval from the `from_` address. This is a powerful capability that, if misused or compromised, could lead to arbitrary token transfers. While restricted by the `onlyIfCanSeize` modifier, the implications of this power should be fully understood and documented (7.3 Access Control).

**Recommendation:** Thoroughly review the design rationale and necessity of the `seize` function. Ensure that the `Pool` and `DebtToken` contracts, which are authorized to call `seize`, have robust internal controls and are highly secure. Document the specific scenarios and conditions under which `seize` is intended to be used, and consider implementing additional safeguards or multi-signature approvals for such sensitive operations if feasible.


### `I-01` — Implicit Return of Zero in `bridgedInSupply` and `bridgedOutSupply`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `bridgedInSupply()` and `bridgedOutSupply()` functions implicitly return 0 if their respective `if` conditions are not met (i.e., `_totalBridgedIn <= _totalBridgedOut` for `bridgedInSupply()` or `_totalBridgedOut <= _totalBridgedIn` for `bridgedOutSupply()`). While this is the default behavior for Solidity functions returning a value type when no explicit `return` statement is executed, explicitly returning `0` in these cases would enhance code clarity and readability for future developers and auditors (7.2 Code Security).

**Recommendation:** For improved clarity, consider adding an explicit `return 0;` statement at the end of `bridgedInSupply()` and `bridgedOutSupply()` functions, after the conditional logic, to clearly indicate the intended return value when the conditions for subtraction are not met.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6435...5160`](https://etherscan.io/address/0x64351fc9810adad17a690e4e1717df5e7e085160) |
| **Network** | Ethereum |
| **Price** | $1,165.5100 |
| **24h Volume** | $649.5K |
| **Liquidity** | $7.61M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 97.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 186 buys / 136 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xa4c567c662349bec3d0fb94c4e7f85ba95e208e4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metronome-synth-eth-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*

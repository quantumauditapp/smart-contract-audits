---
token: Griot
ticker: GRIOT
network: bsc
risk_score: 57
status: medium
date: 2026-09-03
---

# Griot (GRIOT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/griot-bsc)

---

## Audit Summary

The FourERC20 Token contract serves as an ERC-20 implementation for a proxy. While it correctly implements standard ERC-20 functionalities and utilizes Solidity 0.8+ for integer safety, significant upgradeability risks were identified. The contract lacks a `__gap` storage variable, which is crucial for preventing storage collisions in future upgrades. Additionally, the `_init` function, intended for initialization, is not protected against re-initialization and its proper invocation relies entirely on the proxy's setup. The internal `_mint` and `_burn` functions lack external access control, leading to an effectively fixed supply unless explicitly managed by the proxy's initializer or a derived contract.

> **Final Recommendation:** It is strongly recommended to refactor the contract to adhere to established upgradeable contract patterns, such as inheriting from OpenZeppelin's `UUPSUpgradeable` or `ERC1967Upgrade` and including a `__gap` storage array. Implement an `initializer` modifier for the `_init` function to prevent re-initialization. Clearly define and implement access control for `_mint` and `_burn` if a dynamic supply is intended, or remove them if the supply is meant to be strictly fixed. Consider removing unused interfaces to reduce bytecode size and improve clarity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality, leveraging Solidity 0.8+ for default integer overflow/underflow protection and OpenZeppelin interfaces. The use of `unchecked` blocks is… |
| **Governance / Economics** | 4/10 | Medium | The contract is a basic ERC-20 token with no inherent governance mechanisms or complex economic models (7.5 Governance). The supply is effectively fixed due to the internal nature of `_mint` and… |
| **Upgrades** | 4/10 | Medium | As an implementation contract for a proxy, the `FourERC20` contract presents significant upgradeability risks (7.7 Upgrades). It lacks a `__gap` storage variable, which is critical for preventing… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Missing `__gap` Storage Variable and Unprotected Initializer in Proxy Implementation  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract is designed as an implementation for a proxy but does not include a `__gap` storage variable. This omission is a critical vulnerability in upgradeable contracts, as it can lead to storage collisions if new state variables are added in future upgrades, potentially corrupting existing data. Furthermore, the `_init` function, which sets `_name` and `_symbol`, is `internal virtual` and lacks an `initializer` modifier. This means it can be called multiple times, leading to re-initialization vulnerabilities if the proxy's initializer logic is not perfectly implemented and protected.

**Recommendation:** Implement a `__gap` storage array (e.g., `uint256[50] private __gap;`) to reserve storage slots for future upgrades. Inherit from OpenZeppelin's `Initializable` contract and use the `initializer` modifier on the `_init` function to ensure it can only be called once. Ensure the proxy's initializer correctly calls `_init` exactly once upon deployment.


### `H-01` — Uncontrolled Mint/Burn Functionality  *(Severity: High · Status: Unresolved)*

The `_mint` and `_burn` functions are `internal virtual` and are not exposed through any public or external functions within the `FourERC20` contract. This means there is no mechanism to mint new tokens or burn existing ones after the initial deployment (unless `_mint` is called by the proxy's initializer, which is not standard for ongoing supply management). If the intention is for a dynamic supply, this design prevents any supply management. If the intention is for a fixed supply, the presence of these functions can be misleading and their potential use by a derived contract or initializer is not explicitly controlled.

**Recommendation:** Clearly define the token's supply policy. If a fixed supply is desired, consider removing `_mint` and `_burn` or ensure they are never called. If a dynamic supply is intended, implement public/external functions with appropriate access control (e.g., `Ownable` or role-based access control) to manage minting and burning operations.


### `M-01` — `increaseAllowance` Potential Overflow Risk  *(Severity: Medium · Status: Unresolved)*

The `increaseAllowance` function calculates the new allowance as `allowance(owner, spender) + addedValue`. While Solidity 0.8+ prevents `uint256` overflow by default, this operation could theoretically overflow if the sum exceeds `type(uint256).max`. Although highly improbable in practical scenarios, an overflow would cause the allowance to wrap around to a very small number, potentially leading to unexpected behavior or denial of service for the spender if they rely on a large allowance.

**Recommendation:** While the likelihood is low, consider adding an explicit `require` check to ensure `allowance(owner, spender) + addedValue` does not overflow, or use OpenZeppelin's `SafeMath` library (if not already implicitly handled by 0.8+ context) for clarity, although 0.8+ generally handles this. For example: `require(type(uint256).max - currentAllowance >= addedValue, 'ERC20: allowance overflow');`


### `L-01` — Missing Event for `_init` Function  *(Severity: Low · Status: Unresolved)*

The `_init` function, which sets the token's `_name` and `_symbol`, does not emit an event upon successful execution. Emitting an event for critical initialization parameters is a best practice for transparency, allowing off-chain applications and block explorers to easily track and verify the token's initial configuration.

**Recommendation:** Add an event (e.g., `Initialized(string name, string symbol)`) and emit it within the `_init` function after setting `_name` and `_symbol`.


### `I-01` — Unused PancakeSwap Interfaces  *(Severity: Informational · Status: Unresolved)*

The contract includes interfaces for `IPancakeFactory`, `IPancakePair`, and `IPancakeRouter01`. However, these interfaces are not utilized anywhere within the `FourERC20` contract's logic. Including unused interfaces adds unnecessary code to the contract, slightly increasing its bytecode size and deployment cost without providing any direct functionality.

**Recommendation:** Remove the unused PancakeSwap interface imports (`IPancakeFactory.sol`, `IPancakePair.sol`, `IPancakeRouter01.sol`) to reduce bytecode size and improve code clarity, unless they are intended for future integration in a derived contract.


### `I-02` — Redundant Use of `_msgSender()` for Standard ERC-20 Functions  *(Severity: Informational · Status: Unresolved)*

The `transfer` and `approve` functions use `_msgSender()` to retrieve the calling address. While `_msgSender()` is correct and useful for meta-transactions or more complex `Context` scenarios, for standard ERC-20 functions like `transfer` and `approve`, `msg.sender` is typically used directly. This is a minor stylistic choice and does not introduce a vulnerability.

**Recommendation:** For simplicity and consistency with common ERC-20 implementations, consider using `msg.sender` directly in `transfer` and `approve` functions, as `_msgSender()` is primarily intended for more advanced `Context` usage.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa6e3...ffff`](https://bscscan.com/address/0xa6e3eacdf8e6a1ea02052693838f3653fa3bffff) |
| **Network** | BNB Chain |
| **Price** | $0.00006307 |
| **24h Volume** | $45.1K |
| **Liquidity** | $25.7K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 20h |
| **Top-10 Holders** | 55.0% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 801 buys / 626 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x4470feb3fd7ac0766166552daf02a7cf7105f7b5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/griot-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*

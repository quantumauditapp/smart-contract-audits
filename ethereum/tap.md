---
token: tap
ticker: TAP
network: ethereum
risk_score: 83
status: critical
date: 2026-08-15
---

# tap (TAP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 83/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tap-eth)

---

## Audit Summary

The TapBridge protocol consists of a main bridge contract and dynamically deployed ERC20 TapToken contracts. The system facilitates cross-chain asset transfers using signature verification and a fee mechanism. While the architecture leverages standard and secure components like OpenZeppelin's upgradeable contracts and ECDSA for signatures, several critical and medium-severity issues were identified, primarily related to the immutability of key operational addresses, initial configuration, and centralization risks. These issues could impact the protocol's long-term operability and security.

> **Final Recommendation:** It is strongly recommended to implement mechanisms for securely updating critical operational addresses, such as `admin` and `canister`, preferably through a multi-signature wallet or a robust governance process, to mitigate single points of failure and ensure long-term protocol resilience. The initial misconfiguration of the `discountToken` should be corrected to ensure the fee discount mechanism functions as intended from deployment.

Further consideration should be given to the `bridgeOut` function's restriction on contract callers to evaluate if the trade-offs in composability are acceptable for the protocol's vision. Additionally, emitting events for all critical parameter settings, including `admin` and `canister` addresses, would significantly enhance transparency and monitoring capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture of the bridge, utilizing `Clones.clone` for efficient token deployment and `ECDSA.recover` for secure cross-chain message verification, is robust. The contract employs… |
| **Governance / Economics** | 1/10 | High | The economic model incorporates a fee mechanism with a discount based on a specified token balance, which is a positive feature. The `ADMIN_ROLE` provides necessary control over fees and discount… |
| **Upgrades** | 2/10 | High | The `TapToken` contract is designed with upgradeability in mind, utilizing OpenZeppelin's `Upgradeable` contracts and an `initialize` function, which is a strong practice for future extensibility.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Irrecoverable `admin` and `canister` Addresses  *(Severity: High · Status: Unresolved)*

The `admin` address, responsible for receiving bridge fees, and the `canister` address, which is the sole authorized signer for `bridgeIn` transactions, are set in the `TapBridge` constructor and cannot be modified post-deployment. If the private keys associated with these addresses are lost, compromised, or become inaccessible, the protocol's ability to collect fees or process `bridgeIn` operations would be permanently impaired or compromised. This introduces a significant single point of failure and operational risk (7.8 Operations, 7.3 Access Control).

**Recommendation:** Implement a mechanism to allow for the secure update of the `admin` and `canister` addresses. This could involve a multi-signature wallet, a time-locked update function, or integration with a robust governance system. For example, add `setAdmin(address newAdmin)` and `setCanister(address newCanister)` functions protected by the `ADMIN_ROLE` with a timelock or multi-sig confirmation.


### `M-01` — Initial Misconfiguration of `discountToken`  *(Severity: Medium · Status: Unresolved)*

In the `TapBridge` constructor, `discountToken` is initialized to `tokenTemplate`. `tokenTemplate` is an address used by `Clones.clone` as the blueprint for new `TapToken` instances, not a deployed ERC20 token itself. Consequently, `TapToken(discountToken).balanceOf(_msgSender())` will likely revert or return 0, rendering the fee discount mechanism non-functional until the `setDiscount` function is explicitly called by an `ADMIN_ROLE` to set a valid `discountToken` address. This leads to an unexpected initial state for users (7.4 Economic, 7.8 Operations).

**Recommendation:** Initialize `discountToken` to `address(0)` or a pre-deployed, valid discount token address in the constructor. Ensure that the `setDiscount` function is called immediately after deployment to configure the correct discount token and threshold, or consider making `discountToken` configurable during deployment.


### `M-02` — Centralization Risk via `ADMIN_ROLE`  *(Severity: Medium · Status: Unresolved)*

The `ADMIN_ROLE` in `TapBridge` holds significant power, including the ability to set bridge fees (`setFee`) and discount parameters (`setDiscount`). While this flexibility is useful, it introduces a centralized point of control. If the `ADMIN_ROLE` key is compromised or misused, an attacker could manipulate fees to drain funds or disrupt the protocol's economic model. This poses a governance risk (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for the `ADMIN_ROLE` or integrating with a decentralized governance system to distribute control and reduce the risk associated with a single point of failure. For critical operations like setting fees, consider adding a timelock to allow users to react to impending changes.


### `L-01` — `bridgeOut` Restriction for Contracts  *(Severity: Low · Status: Unresolved)*

The `bridgeOut` function includes a check `if (_msgSender().code.length > 0) revert Errors.LikelyContract(_msgSender());` which prevents calls from other smart contracts. While this might be intended to prevent certain complex reentrancy or unintended interactions, it significantly limits composability. Legitimate contract wallets, proxy contracts, or other DeFi protocols would be unable to use the `bridgeOut` functionality, potentially hindering integration and user experience (7.1 Architecture, 7.4 Economic).

**Recommendation:** Re-evaluate the necessity of restricting `bridgeOut` calls from contracts. If the primary concern is reentrancy, ensure that the Checks-Effects-Interactions pattern is strictly followed, which is already largely the case. If the restriction is deemed critical, clearly document this design choice and its implications for users and integrators.


### `L-02` — `TapToken` `decimals()` Override Inconsistency  *(Severity: Low · Status: Unresolved)*

The `TapToken` contract explicitly overrides the `decimals()` function to return a custom `_decimals` value set during initialization. However, the inherited `ERC20Upgradeable`'s internal `_decimals` variable (which defaults to 18) remains unchanged because `__ERC20_init` does not take a `decimals_` argument. While the public `decimals()` getter correctly returns the intended value, this internal inconsistency could lead to confusion or unexpected behavior if external tools or contracts rely on the default `ERC20Upgradeable` internal state or assumptions about `_decimals` being directly set by `__ERC20_init` (7.2 Code Security).

**Recommendation:** To maintain consistency and clarity, consider using the `__ERC20_init(name_, symbol_, decimals_)` constructor if available in the specific OpenZeppelin version, or ensure that the custom `_decimals` variable is clearly documented as overriding the default behavior. Alternatively, if `ERC20Upgradeable`'s `_decimals` is accessible, update it directly.


### `I-01` — Lack of Event for Critical Parameter Setup  *(Severity: Informational · Status: Unresolved)*

The `admin` and `canister` addresses, which are critical parameters for the `TapBridge` contract's operation, are set in the constructor. However, no events are emitted to log these values upon deployment. Emitting events for such critical configurations enhances transparency, allows for easier monitoring by off-chain systems, and provides an immutable record of the contract's initial setup (7.8 Operations).

**Recommendation:** Emit events in the `TapBridge` constructor to log the `admin` and `canister` addresses. For example: `event AdminSet(address indexed admin);` and `event CanisterSet(address indexed canister);`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5e7f...7454`](https://etherscan.io/address/0x5e7f6e008c6d9d7ad4c7eb75bd4ce62864cc7454) |
| **Network** | Ethereum |
| **Price** | $0.1069 |
| **24h Volume** | $77.9K |
| **Liquidity** | $33.4K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 57.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 261 buys / 283 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x1563e9af51616e78830de3325da752de369c1714)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tap-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*

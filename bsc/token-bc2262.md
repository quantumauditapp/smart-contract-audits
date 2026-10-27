---
token: 富贵
ticker: 富贵
network: bsc
risk_score: 0
status: low
date: 2026-08-30
---

# 富贵 (富贵) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-bc2262-bsc)

---

## Audit Summary

The `FourERC20` contract provides a foundational ERC-20 token implementation based on OpenZeppelin standards. However, it is designed as an abstract base contract and lacks a constructor to initialize token metadata (name, symbol) and, critically, any public mechanism for initial token supply creation or subsequent minting/burning. If deployed directly without a derived contract adding these essential functionalities, the token would be non-functional with a zero supply. This architectural incompleteness represents a significant risk.

> **Final Recommendation:** It is strongly recommended that `FourERC20` be used exclusively as a base contract for a derived token implementation. The derived contract must include a constructor to initialize the token's name and symbol, and implement a secure, access-controlled minting mechanism to create the initial supply and manage future token issuance. Ensure that any functions added to the derived contract that modify token supply or critical parameters are protected by robust access control, preferably using a battle-tested library like OpenZeppelin's `Ownable` or a multi-signature wallet. Thoroughly test the derived contract's complete lifecycle, including deployment, initial supply creation, and all supply-modifying operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) of `FourERC20` leverages OpenZeppelin's robust ERC-20 standard, providing well-tested implementations for core token functionalities like `transfer` and `approve`.… |
| **Governance / Economics** | 10/10 | Low | The contract does not implement any governance mechanisms (7.5), relying on direct owner actions if a derived contract adds such functionality. Economically (7.4), the token's supply mechanism is… |
| **Upgrades** | 10/10 | Low | The `FourERC20` contract is not designed with upgradeability in mind (7.7), as indicated by the `is_proxy: false` flag. This simplifies the deployment model by removing proxy-related complexities and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Incomplete Token Implementation (No Constructor/Minting Mechanism)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FourERC20` contract lacks a constructor to initialize the token's `_name` and `_symbol` variables. More critically, it does not provide any public or external function to mint new tokens or create an initial supply. The `_mint` function is internal, meaning a derived contract must implement the minting logic. If deployed as-is, the token would have a `totalSupply` of zero and no mechanism to increase it, rendering it unusable.

**Recommendation:** A derived contract must be created that inherits from `FourERC20`. This derived contract should include a constructor that calls `_init` to set the token's name and symbol, and also calls `_mint` to create an initial token supply for a designated address (e.g., the deployer or a treasury). If dynamic minting is desired, the derived contract must implement a public `mint` function with appropriate access control.


### `M-02` — Missing Access Control for Supply Management in Derived Contracts  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FourERC20` contract provides internal `_mint` and `_burn` functions for supply management. However, it does not include any access control mechanisms (e.g., `Ownable`, `AccessControl`) that would restrict who can call these functions if exposed publicly by a derived contract. If a derived contract implements public `mint` or `burn` functions without proper access control, any user could potentially manipulate the token supply, leading to severe economic instability or unauthorized token creation/destruction.

**Recommendation:** Any derived contract that exposes `_mint` or `_burn` functionality via public or external functions must implement robust access control. It is highly recommended to use a battle-tested access control mechanism like OpenZeppelin's `Ownable` or `AccessControl` to restrict these critical functions to authorized addresses (e.g., a contract owner, a multi-signature wallet, or a governance system).


### `L-01` — Use of `_init` Instead of Constructor for Initialization  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses an internal function `_init(string memory name_, string memory symbol_)` to set the token's name and symbol, rather than a standard constructor. While this pattern can be useful for upgradeable contracts (proxies), the `is_proxy: false` flag indicates this is not an upgradeable contract. For non-upgradeable contracts, using a constructor is the standard and most straightforward way to initialize immutable state variables. If `_init` is not called exactly once during deployment by a derived contract's constructor, the token's name and symbol will remain empty.

**Recommendation:** For non-upgradeable contracts, it is generally recommended to use a constructor to initialize immutable state variables like `_name` and `_symbol`. If `_init` is retained, ensure that any derived contract's constructor explicitly calls `_init` exactly once with the desired name and symbol.


### `I-01` — Adherence to OpenZeppelin ERC-20 Standard Implementation  *(Severity: Informational · Status: Resolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FourERC20` contract largely follows the OpenZeppelin ERC-20 standard implementation, including best practices such as `increaseAllowance` and `decreaseAllowance` to mitigate front-running risks associated with `approve`. The use of `unchecked` for `decreaseAllowance` is correctly guarded by a `require` statement, preventing underflow. This adherence to well-audited patterns enhances the contract's reliability and security for core token operations.

**Recommendation:** Continue to leverage battle-tested libraries like OpenZeppelin for core functionalities. Regularly review OpenZeppelin updates for security patches and improvements to ensure ongoing robustness.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x198d...4444`](https://bscscan.com/address/0x198dba421a7db566a90da5de7901abe3443b4444) |
| **Network** | BNB Chain |
| **Price** | $0.003355 |
| **24h Volume** | $1.55M |
| **Liquidity** | $295.2K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 20.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1441 buys / 1826 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8672a5d410c567c1b54703bfeddd7699ffdb1b3f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-bc2262-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

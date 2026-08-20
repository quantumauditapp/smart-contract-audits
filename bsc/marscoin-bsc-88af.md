---
token: MarsCoin
ticker: MARSCOIN
network: bsc
risk_score: 23
status: medium
date: 2026-08-20
---

# MarsCoin (MARSCOIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 23/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/marscoin-bsc-88af)

---

## Audit Summary

The FourERC20 contract implements a standard ERC-20 token based on OpenZeppelin's audited codebase. While the core ERC-20 logic is robust, a critical functional flaw exists where the token's name, symbol, and initial supply are not set upon deployment, rendering the token unusable. Additionally, a low-severity issue related to the standard ERC-20 `approve` function's race condition is noted, though mitigated by alternative functions.

> **Final Recommendation:** It is imperative to address the critical initialization flaw. If `FourERC20` is intended to be a deployable token, a public constructor must be added to call the `_init` function and set the token's metadata (name and symbol), and to implement a minting mechanism to establish an initial supply. If it is meant as a base contract, ensure any inheriting contract properly calls `_init` in its constructor or initializer. Additionally, while `increaseAllowance` and `decreaseAllowance` mitigate some risks, users should be educated on the `approve` race condition.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's well-audited `ERC20` implementation, contributing to strong code security (7.2 Code Security). It includes `increaseAllowance` and `decreaseAllowance` to… |
| **Governance / Economics** | 5/10 | Medium | This contract is a basic ERC-20 token and does not incorporate any governance mechanisms or complex economic models (7.5 Governance, 7.4 Economic). All standard ERC-20 operations are permissionless… |
| **Upgrades** | 9/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades). The provided information indicates it is intended for direct deployment, not as an implementation contract for a proxy.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Uninitialized Token State on Direct Deployment  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract lacks a public constructor to initialize its state variables. The `_init` function, which sets the token's `_name` and `_symbol`, is `internal` and is not called within the contract itself. Furthermore, there are no public minting functions. If this contract is deployed directly, the `_name`, `_symbol`, and `_totalSupply` will remain empty or zero, rendering the token completely non-functional and unusable as an ERC-20 token. This is a critical functional flaw (7.1 Architecture, 7.8 Operations).

**Recommendation:** If `FourERC20` is intended to be a deployable token, add a public constructor that calls `_init(string memory name_, string memory symbol_)` and implements an initial minting mechanism (e.g., `_mint(msg.sender, initialSupply)`). If it is strictly a base contract, ensure that any inheriting contract explicitly calls `_init` in its constructor or initializer.


### `L-01` — Standard ERC-20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

The `approve` function, while compliant with the ERC-20 standard, is susceptible to a known front-running vulnerability. If a user approves an amount, then attempts to change that approval to a different non-zero amount, an attacker can front-run the second transaction to spend the original approved amount. The second transaction will then set the allowance to the new amount, potentially allowing the attacker to spend more than intended. The contract includes `increaseAllowance` and `decreaseAllowance` which mitigate this, but the `approve` function itself remains vulnerable (7.2 Code Security).

**Recommendation:** Educate users about the `approve` race condition and strongly recommend using `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying an existing allowance. If `approve` must be used, advise users to first set the allowance to zero before setting a new non-zero value.


### `I-01` — Base Contract Design for Supply Management  *(Severity: Informational · Status: Unresolved)*

The `_mint` and `_burn` functions are declared as `internal` and are not exposed through any public or external functions within `FourERC20`. This indicates that `FourERC20` is designed as a base contract, expecting a derived contract to implement the actual token supply management (minting and burning). If deployed directly without a derived contract, no tokens can ever be created or destroyed, making the `totalSupply` permanently zero (7.1 Architecture).

**Recommendation:** This is a design choice. Ensure that the deployment strategy aligns with this design. If `FourERC20` is intended to be a standalone, deployable token, consider adding public minting/burning functions or a constructor that mints an initial supply. If it's a base contract, document this clearly for developers inheriting from it.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1706...4444`](https://bscscan.com/address/0x1706f1e06c69f3a8cf33cce179d5d78a5c6f4444) |
| **Network** | BNB Chain |
| **Price** | $0.002059 |
| **24h Volume** | $878.0K |
| **Liquidity** | $208.5K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 80.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3288 buys / 2761 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6a1d08d62786ec9257de00cbdc6313228fce5068)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/marscoin-bsc-88af)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*

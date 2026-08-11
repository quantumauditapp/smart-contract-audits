---
token: Slap Cat
ticker: SLAP
network: bsc
risk_score: 58
status: high
date: 2026-08-11
---

# Slap Cat (SLAP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 58/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/slap-cat-bsc)

---

## Audit Summary

The TokenV2 contract is an upgradeable ERC20 token utilizing OpenZeppelin's upgradeable contracts. It implements a unique transfer constraint mechanism to restrict transfers to/from specific Uniswap pools, which can be disabled by the owner. While the core ERC20 functionality is robust due to OpenZeppelin's audited libraries, a critical vulnerability related to upgradeability was identified, along with concerns regarding centralized control and initial token distribution.

> **Final Recommendation:** Prioritize addressing the high-severity upgradeability issue by adding `_disableInitializers()` to the constructor. For the centralized control points, consider implementing a multi-signature wallet for the owner role to enhance security and decentralize critical administrative actions. Ensure the initial token distribution strategy aligns with the project's overall tokenomics and security best practices.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages well-audited OpenZeppelin Upgradeable libraries for ERC20, ERC20Permit, and Ownable functionalities, contributing to a strong foundation (7.2 Code Security). The custom… |
| **Governance / Economics** | 4/10 | Medium | The contract design grants the owner significant control, particularly over the `transferConstraints` mechanism, which can be unilaterally removed (7.3 Access Control). This centralized control… |
| **Upgrades** | 3/10 | High | The contract is designed as an upgradeable implementation using OpenZeppelin's `Upgradeable` pattern, which is a standard and generally secure approach (7.1 Architecture). The `initialize` function… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Missing `_disableInitializers()` in Constructor of Upgradeable Contract  *(Severity: High · Status: Unresolved)*

The `TokenV2` contract is an upgradeable implementation designed to be deployed behind a proxy. It correctly uses an `initialize` function with the `initializer` modifier. However, its constructor is empty and does not call `_disableInitializers()`. If this implementation contract is ever deployed directly (not through a proxy), its `initialize` function could be called multiple times by anyone, leading to re-initialization of state variables and potential exploits, such as re-minting tokens or changing critical parameters.

**Recommendation:** Add `_disableInitializers()` to the constructor of the `TokenV2` contract. This prevents the `initialize` function from being called on the implementation contract directly, mitigating the risk of re-initialization.


### `M-01` — Centralized Control over Transfer Constraints  *(Severity: Medium · Status: Unresolved)*

The `transferConstraints` mechanism, which restricts token transfers to or from specified Uniswap V2 and V3 pools, can be entirely removed by the contract owner via the `removeTransferConstraints()` function. This grants significant centralized control to a single entity, allowing them to unilaterally alter a core token transfer behavior that could impact liquidity or trading strategies.

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for critical functions like `removeTransferConstraints()`. This would distribute control, increase transparency, and provide a delay for community review before significant changes are enacted.


### `L-01` — Single Point of Failure for Owner Role  *(Severity: Low · Status: Unresolved)*

The contract relies on a single `owner` address for critical administrative functions, such as `removeTransferConstraints()`. If the owner's private key is compromised, or the owner becomes malicious, the protocol could be at risk of unauthorized changes or manipulation.

**Recommendation:** Implement a multi-signature wallet for the owner role to distribute control and enhance security. This requires multiple trusted parties to approve transactions, significantly reducing the risk associated with a single point of failure.


### `I-01` — All Tokens Minted to Initializer  *(Severity: Informational · Status: Unresolved)*

During the `initialize` function call, the entire `maxSupply` of tokens is minted to `msg.sender` (the address that calls `initialize`). This design choice means the deployer or the address responsible for initialization will initially hold the entire token supply.

**Recommendation:** Ensure that the address performing the initialization is a secure, controlled entity (e.g., a multi-sig wallet or a trusted contract) and that this initial distribution model aligns with the project's intended tokenomics and distribution strategy. Clearly communicate this distribution to stakeholders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd82f...bfad`](https://bscscan.com/address/0xd82f2e48a0c7c90bb38f62d45c8d2096b7ccbfad) |
| **Network** | BNB Chain |
| **Price** | $0.00006987 |
| **24h Volume** | $52.9K |
| **Liquidity** | $23.4K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 8d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 361 buys / 241 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x0a5bc2c99b064c22de430bfb14c52fbc92be11ee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/slap-cat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*

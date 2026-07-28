---
token: OMI Token
ticker: OMI
network: base
risk_score: 58
status: high
date: 2026-07-24
---

# OMI Token (OMI) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/omi-token-base)

---

## Audit Summary

The OptimismMintableERC20 contract is a standard ERC20 token designed for cross-chain bridging, allowing a designated bridge contract to mint and burn tokens. The contract leverages OpenZeppelin's battle-tested ERC20 implementation and includes versioning via Semver. The primary security consideration is the centralized control over token supply by the immutable BRIDGE address, making the token's integrity highly dependent on the security of the external bridge contract.

> **Final Recommendation:** Prioritize the security and operational integrity of the external `BRIDGE` contract, as it holds absolute control over the token's supply. Implement stringent pre-deployment checks for the `BRIDGE` and `REMOTE_TOKEN` addresses to prevent irreversible misconfigurations. While legacy functions are harmless, consider their removal in future iterations to streamline the contract interface.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates good technical architecture, extending OpenZeppelin's ERC20 for robust token functionality (7.1 Architecture). Code quality is high, with clear variable names, comprehensive… |
| **Governance / Economics** | 2/10 | High | The economic model of the OptimismMintableERC20 token is directly tied to the security of the `BRIDGE` contract (7.4 Economic). The `BRIDGE` address has absolute power to mint and burn tokens… |
| **Upgrades** | 3/10 | High | The OptimismMintableERC20 contract is not designed as an upgradeable proxy or an implementation contract for a proxy (7.7 Upgrades). Its core variables (`REMOTE_TOKEN`, `BRIDGE`) are immutable, and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 64.6% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `H-01` — Centralized Control of Token Supply by Bridge  *(Severity: High · Status: Unresolved)*

The `OptimismMintableERC20` contract grants exclusive `mint` and `burn` capabilities to a single `BRIDGE` address, set immutably during construction. This design centralizes control over the token's total supply to the security of the designated bridge contract. A compromise of the `BRIDGE` contract would allow an attacker to arbitrarily mint or burn tokens, leading to severe economic consequences for the token and its holders. This represents a critical external dependency and a single point of failure. (7.3 Access Control, 7.4 Economic, 7.6 External)

**Recommendation:** Ensure the `BRIDGE` contract is robustly secured, thoroughly audited, and follows best practices for access control and operational security. Consider multi-signature control or time-locks for critical bridge operations if applicable to the bridge's design. The security posture of the `OptimismMintableERC20` token is directly proportional to the security of its associated `BRIDGE` contract.


### `M-01` — Irreversible `BRIDGE` and `REMOTE_TOKEN` Addresses  *(Severity: Medium · Status: Unresolved)*

The `BRIDGE` and `REMOTE_TOKEN` addresses are declared as `immutable` and are set only once during the contract's construction. While immutability can enhance security by preventing unauthorized changes, it also means that any error in setting these critical addresses during deployment cannot be corrected. An incorrectly configured `BRIDGE` address would render the token's mint/burn functionality unusable or controllable by an unintended entity, while an incorrect `REMOTE_TOKEN` address could lead to cross-chain mapping issues. (7.8 Operations)

**Recommendation:** Implement rigorous pre-deployment verification procedures, including checksum validation and multiple reviews, to ensure the correctness of the `_bridge` and `_remoteToken` parameters passed to the constructor. Consider deploying to a testnet with the exact parameters to confirm functionality before mainnet deployment.


### `I-01` — Use of Legacy Functions  *(Severity: Informational · Status: Unresolved)*

The contract includes several functions (`l1Token`, `l2Bridge`, `remoteToken`, `bridge`) explicitly marked with `@custom:legacy` in their NatSpec comments. These functions provide redundant access to the `REMOTE_TOKEN` and `BRIDGE` immutable variables. While harmless in functionality, their presence adds to the contract's bytecode size and could potentially lead to confusion for integrators if not clearly understood that `REMOTE_TOKEN` and `BRIDGE` are the canonical variables. (7.2 Code Security, 7.8 Operations)

**Recommendation:** For future versions or new deployments, consider removing these legacy functions if backwards compatibility is no longer a strict requirement, to reduce contract complexity and bytecode size. Ensure documentation clearly distinguishes between canonical and legacy getters.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3792...3299`](https://basescan.org/address/0x3792dbdd07e87413247df995e692806aa13d3299) |
| **Network** | Base |
| **Price** | $0.0001529 |
| **24h Volume** | $28.6K |
| **Liquidity** | $237.9K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 28.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 575 buys / 651 sells |

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

## Frequently Asked Questions

### Is OMI Token a scam?

Based on automated analysis, OMI Token scores 76/100 (Critical Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is OMI Token safe to buy?

Our scanner flagged a risk score of 76/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has OMI Token been audited?

The contract is open-source and verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x6e7b4416e3a2b873f6cd4840e6bee7d88f07da8f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/omi-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*

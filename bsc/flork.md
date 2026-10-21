---
token: flork
ticker: FLORK
network: bsc
risk_score: 0
status: low
date: 2026-09-01
---

# flork (FLORK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flork-bsc)

---

## Audit Summary

The `FourERC20` contract implements a standard ERC-20 token, leveraging well-audited OpenZeppelin libraries for its core functionalities. While the base implementation for transfers and allowances appears robust, the contract as provided lacks a public mechanism to mint tokens, rendering it non-functional as a standalone token. Additionally, a critical portion of the `_transfer` function was truncated in the provided source, which significantly limited a complete security analysis of its internal logic. The contract is not upgradeable, which simplifies its security model but removes future flexibility.

> **Final Recommendation:** It is strongly recommended to provide the complete and final source code for all functions, especially the truncated `_transfer` function, for a comprehensive security analysis before deployment. If this contract is intended to be a functional token, it must be inherited by a derived contract that implements a public minting mechanism, along with robust access control for that mechanism. Consider the long-term implications of the non-upgradeable design for future protocol flexibility and potential feature enhancements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages well-audited OpenZeppelin libraries (v4.9.4) for its ERC-20 implementation, ensuring a strong foundation for core token functionalities like transfers and allowances (7.2 Code… |
| **Governance / Economics** | 8/10 | Low | The contract implements a basic ERC-20 token with no complex economic models, fees, or governance mechanisms (7.4 Economic, 7.5 Governance). This simplicity inherently reduces economic and governance… |
| **Upgrades** | 10/10 | Low | The `FourERC20` contract is not designed to be upgradeable (7.7 Upgrades). This eliminates risks associated with proxy patterns, such as storage collisions, improper initialization, or upgrade path… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Missing Public Token Supply Mechanism  *(Severity: Medium · Status: Unresolved)*

The `FourERC20` contract provides internal `_mint` and `_burn` functions but lacks any public or external functions to create or destroy tokens. As a result, the token's `_totalSupply` will remain zero upon deployment, and there will be no mechanism to issue new tokens, rendering the contract non-functional as a standalone ERC-20 token. This is a design flaw that prevents the token from being used as intended without further development.

**Recommendation:** If this contract is intended to be a base, ensure that any derived contract implements a public minting function (e.g., `mint(address to, uint256 amount)`) that calls the internal `_mint` function. This public function must be protected by appropriate access control mechanisms (e.g., `Ownable`, `AccessControl`) to prevent unauthorized token creation.


### `L-01` — Incomplete Source Code Provided for Audit  *(Severity: Low · Status: Unresolved)*

The provided source code for the `_transfer` internal function within `FourERC20.sol` is truncated. This prevents a full and accurate security analysis of one of the most critical functions in an ERC-20 token, as the complete logic for balance updates and checks could not be reviewed. While it is likely based on OpenZeppelin's standard implementation, an audit cannot make assumptions about missing code.

**Recommendation:** Always provide the complete and final source code for all contracts and functions to be audited. This ensures that all logic, including internal helper functions, can be thoroughly reviewed for potential vulnerabilities, edge cases, and deviations from expected behavior.


### `I-01` — Non-Upgradeability of Contract  *(Severity: Informational · Status: Unresolved)*

The `FourERC20` contract is deployed directly and does not implement any upgradeability pattern (e.g., UUPS, Transparent Proxies). This means that once deployed, its logic cannot be modified or updated. While this simplifies the security model by removing upgrade-related risks, it also means that any future bug fixes, feature enhancements, or protocol changes would require deploying an entirely new contract and migrating users/assets.

**Recommendation:** Acknowledge the implications of non-upgradeability. If future flexibility is desired, consider implementing an upgradeable proxy pattern (e.g., UUPS) for the token contract. If non-upgradeability is a deliberate design choice, ensure that the current implementation is robust and future-proof to minimize the need for redeployment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x09db...4444`](https://bscscan.com/address/0x09db6885551ab1d4a9fa484d9b4b9fe899134444) |
| **Network** | BNB Chain |
| **Price** | $0.00005514 |
| **24h Volume** | $17.8K |
| **Liquidity** | $41.3K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 57.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 918 buys / 1008 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3afcebe6cdc13c3dac83e4be73b892f460dfd0a2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flork-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*

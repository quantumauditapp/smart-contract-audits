---
token: Dogelon
ticker: ELON
network: ethereum
risk_score: 4
status: low
date: 2026-09-21
---

# Dogelon (ELON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 4/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dogelon-eth)

---

## Audit Summary

The Dogelon contract implements a standard ERC20 token using OpenZeppelin's SafeMath library. The primary economic risk identified is the complete centralization of the initial token supply to the deployer address. Technically, the contract is robust, utilizing established patterns and mitigating common vulnerabilities like integer overflows.

> **Final Recommendation:** It is strongly recommended to address the high centralization of the initial token supply. Consider implementing a distribution strategy that diversifies token holdings away from a single address to mitigate potential market manipulation risks. For future projects, evaluate the need for governance mechanisms or a multi-signature wallet for critical operations if any privileged functions were to be introduced. While not upgradeable, ensure thorough testing of the current immutable contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture (7.1) is a straightforward ERC20 token, inheriting from well-audited OpenZeppelin contracts. Code security (7.2) is strong, with SafeMath used throughout to prevent integer… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4) of the Dogelon token presents a significant centralization risk. The entire initial supply of 10e32 tokens is minted to the contract deployer (msg.sender) in the constructor… |
| **Upgrades** | 7/10 | Low | The contract is not designed to be upgradeable (7.7), meaning its logic cannot be modified after deployment. This eliminates upgrade-related risks such as proxy misconfigurations or malicious upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.8% (≈ permanent lock) |
| **LP Locked** | 99.8% |

## Security Findings

_🟠 1 High · ⚪ 3 Informational_

### `H-01` — Centralized Initial Token Supply  *(Severity: High · Status: Unresolved)*

The `Dogelon` contract's constructor mints the entire initial supply of 10e32 tokens to the deployer's address (`msg.sender`). This results in 100% of the token supply being held by a single entity, creating a significant centralization risk. This concentration of power could lead to market manipulation, such as large-scale selling (rug pull), or give the deployer undue influence over the token's ecosystem.

**Recommendation:** Implement a more decentralized distribution strategy for the initial token supply. This could involve distributing tokens to multiple addresses, locking a portion in a liquidity pool, or vesting tokens over time. For future projects, consider using a multi-signature wallet for initial token distribution or critical administrative functions.


### `I-01` — No Pause or Blacklist Functionality  *(Severity: Informational · Status: Unresolved)*

The ERC20 token implementation does not include any pause or blacklist functionality. While this enhances decentralization by preventing arbitrary freezing of transfers or accounts, it also means there is no mechanism to stop token transfers in case of a critical vulnerability, exploit, or regulatory requirement.

**Recommendation:** This is a design choice. If the project requires the ability to halt operations or restrict certain addresses in emergencies, consider implementing `Pausable` or `Blacklist` patterns. However, be aware that such features introduce centralization and potential attack vectors.


### `I-02` — Fixed Decimals  *(Severity: Informational · Status: Unresolved)*

The `_decimals` variable is set to 18 in the `ERC20` constructor and can only be set once via `_setupDecimals` (which is called in the constructor). This means the token's decimal precision is fixed at 18 and cannot be changed after deployment. While 18 is a common standard for ERC20 tokens, it's worth noting its immutability.

**Recommendation:** This is standard behavior for most ERC20 tokens and generally not an issue. Ensure that all integrations and front-end applications correctly handle the 18 decimal places.


### `I-03` — Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract uses Solidity compiler version `^0.7.1`. While this version is functional, it is not the latest stable release. Newer compiler versions often include bug fixes, security enhancements, and gas optimizations.

**Recommendation:** Consider upgrading to the latest stable Solidity compiler version (e.g., `^0.8.x`) for new deployments to benefit from recent improvements and security patches, such as default checked arithmetic. Thoroughly test the contract after any compiler version upgrade.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x761d...60f3`](https://etherscan.io/address/0x761d38e5ddf6ccf6cf7c55759d5210750b5d60f3) |
| **Network** | Ethereum |
| **Price** | $0.00000003 |
| **24h Volume** | $36.5K |
| **Liquidity** | $5.79M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 5y |
| **Top-10 Holders** | 57.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 40 buys / 85 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x7b73644935b8e68019ac6356c40661e1bc315860)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dogelon-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-21*

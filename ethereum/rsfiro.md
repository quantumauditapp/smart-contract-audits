---
token: rsFIRO
ticker: RSFIRO
network: ethereum
risk_score: 70
status: high
date: 2026-09-19
---

# rsFIRO (RSFIRO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rsfiro-eth)

---

## Audit Summary

The rsFIRO token contract is a standard ERC20 implementation, largely based on OpenZeppelin's robust and audited patterns. It features a fixed supply, custom error handling, and an overridden decimals function. No critical or high-severity vulnerabilities were identified. The primary characteristic noted is the initial distribution of the entire token supply to the deployer, which is common for new tokens.

> **Final Recommendation:** It is recommended to ensure that the initial distribution strategy for the rsFIRO token aligns with the project's long-term decentralization goals, given the deployer holds the entire initial supply. Users should be aware of this initial centralization. For future developments, consider implementing a multi-signature wallet for critical administrative functions if any are introduced, to enhance security and decentralization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The rsFIRO contract is a well-structured ERC20 token, inheriting from a robust base (7.1 Architecture). It utilizes modern Solidity features such as custom errors and `unchecked` blocks for gas… |
| **Governance / Economics** | 1/10 | High | The token implements a fixed supply model with no further minting capabilities after deployment, which enhances scarcity and predictability (7.4 Economic). The entire initial supply is minted to the… |
| **Upgrades** | 6/10 | Medium | The rsFIRO contract is not designed to be upgradeable (7.7 Upgrades). This eliminates the complexities and potential risks associated with proxy patterns and upgrade mechanisms, providing a fixed and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Standard ERC20 Implementation  *(Severity: Informational · Status: Unresolved)*

The rsFIRO token contract is a standard implementation of the ERC20 token interface, inheriting from a well-vetted base similar to OpenZeppelin's contracts. It provides all expected functionalities such as `transfer`, `approve`, `transferFrom`, `balanceOf`, `totalSupply`, `name`, `symbol`, and `decimals`. The contract correctly overrides the `decimals()` function to return 8.

**Recommendation:** No action required. This is a standard and secure implementation.


### `I-02` — Use of Custom Errors  *(Severity: Informational · Status: Unresolved)*

The contract utilizes custom errors (e.g., `ERC20InsufficientBalance`, `ERC20InvalidSender`) instead of traditional `require()` statements with string messages. This is a modern Solidity best practice that improves gas efficiency for failed transactions and provides clearer error reporting for off-chain applications.

**Recommendation:** No action required. This is a positive design choice.


### `I-03` — Fixed Supply and Initial Distribution  *(Severity: Informational · Status: Unresolved)*

The rsFIRO token has a fixed total supply of 2,140,000 tokens (with 8 decimals) minted entirely to the contract deployer (`msg.sender`) during construction. There are no further public minting or burning capabilities exposed, ensuring a predictable supply schedule. This initial distribution model centralizes the entire supply with the deployer at launch.

**Recommendation:** Ensure transparency regarding the initial distribution and the deployer's role. If the project aims for decentralization, a plan for further distribution of the initial supply should be communicated.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2744...ddc2`](https://etherscan.io/address/0x2744ea5ac9b11cb5e3cd63d3a88e858336aeddc2) |
| **Network** | Ethereum |
| **Price** | $1.2300 |
| **24h Volume** | $65.9K |
| **Liquidity** | $61.5K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 200.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 131 buys / 101 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x385cd0e67ceae18d38c415bb01df62bace0c25ba)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rsfiro-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-19*

---
token: Brad
ticker: BRAD
network: bsc
risk_score: 0
status: low
date: 2026-08-12
---

# Brad (BRAD) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/brad-bsc)

---

## Audit Summary

The FourERC20 contract is a standard ERC-20 token implementation, largely based on OpenZeppelin Contracts. It provides core token functionalities and includes mitigations for common ERC-20 allowance issues. The contract itself is a base implementation and lacks a public supply mechanism or a constructor to initialize its name and symbol, requiring a derived contract for full functionality. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** Ensure that a derived contract properly implements a constructor to set the token's name and symbol, and to establish a controlled supply mechanism (minting/burning). This will ensure the token is fully functional upon deployment. If there is an intention to make this token upgradeable in the future, a separate proxy contract would be required, and the `FourERC20` contract would need to be adapted to include an `initialize` function with appropriate access control and an `initializer` modifier to prevent re-initialization vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements the ERC-20 standard using well-vetted OpenZeppelin libraries, ensuring strong code security (7.2 Code Security) and adherence to best practices. It includes… |
| **Governance / Economics** | 9/10 | Low | The contract itself does not implement any governance mechanisms (7.5 Governance) or complex economic models (7.4 Economic), functioning purely as a standard token. Its economic stability depends… |
| **Upgrades** | 10/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades) and does not include any proxy-related logic. If deployed directly, it is not upgradeable, and thus upgrade safety is not a direct… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Uninitialized Metadata on Direct Deployment  *(Severity: Low · Status: Unresolved)*

The `FourERC20` contract includes an internal `_init(string memory name_, string memory symbol_)` function to set the token's name and symbol. However, the contract itself does not have a public constructor that calls this `_init` function. If `FourERC20` is deployed directly without a constructor, the `_name` and `_symbol` state variables will remain empty strings, causing `name()` and `symbol()` functions to return empty values, which is unusual for an ERC-20 token.

**Recommendation:** Implement a public constructor in the `FourERC20` contract or a derived contract that calls `_init(string memory name_, string memory symbol_)` to properly set the token's metadata upon deployment. For example: `constructor(string memory name_, string memory symbol_) { _init(name_, symbol_); }`.


### `I-01` — Base Contract Design - Missing Supply Mechanism  *(Severity: Informational · Status: Unresolved)*

The `FourERC20` contract is designed as a base implementation for an ERC-20 token. It provides core functionalities like `transfer`, `approve`, and `balanceOf`, but intentionally lacks a public mechanism for minting or burning tokens. The `_mint` and `_burn` functions are internal, requiring a derived contract to implement the token's supply mechanism. This design choice means the contract, as-is, cannot create new tokens or destroy existing ones publicly.

**Recommendation:** A derived contract must be implemented to define and control the token's supply mechanism (e.g., through a `Minter` role or a fixed supply at deployment). This is a design consideration rather than a vulnerability, but it's crucial for the token's intended utility.


### `I-02` — EIP-2771 Context Suffix Not Configured  *(Severity: Informational · Status: Unresolved)*

The contract inherits from OpenZeppelin's `Context.sol`, which includes the virtual function `_contextSuffixLength()`. This function is part of the infrastructure for supporting EIP-2771 (meta-transactions) by indicating the length of the suffix appended to `msg.data`. The current implementation in `Context` (and thus in `FourERC20`) returns `0`, meaning EIP-2771 is not actively configured or supported by this contract. While not a vulnerability, it indicates a lack of meta-transaction support.

**Recommendation:** If EIP-2771 meta-transactions are intended to be supported, a derived contract must override the `_contextSuffixLength()` function to return the correct suffix length, and integrate with a trusted forwarder. If meta-transactions are not a requirement, this can be disregarded.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3db1...4444`](https://bscscan.com/address/0x3db1b406a4d50a841948765685ed42ed1f174444) |
| **Network** | BNB Chain |
| **Price** | $0.00002134 |
| **24h Volume** | $95.9K |
| **Liquidity** | $14.8K |
| **Volume / Liquidity** | 6.5× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 62.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4020 buys / 2997 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x13a9dafa6c65c88f53ebd561e587dea3aa09c9f8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/brad-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*

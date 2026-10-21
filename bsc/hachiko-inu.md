---
token: Hachiko Inu
ticker: HACHIKO
network: bsc
risk_score: 8
status: low
date: 2026-09-13
---

# Hachiko Inu (HACHIKO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hachiko-inu-bsc)

---

## Audit Summary

The FourERC20 contract, intended as an ERC-20 token, exhibits critical functional flaws. It lacks a constructor to initialize essential token metadata (name, symbol) and does not expose any mechanism to mint or burn tokens, rendering it non-functional as a standalone token. Additionally, there is a complete absence of access control for any potential privileged operations. The provided code snippet is also truncated, limiting a full assessment.

> **Final Recommendation:** It is strongly recommended to implement a constructor to properly initialize the token's name and symbol. A controlled supply mechanism, such as minting and burning functions, must be added and secured with robust access control (e.g., using OpenZeppelin's Ownable or AccessControl). Ensure all critical functions are protected by appropriate permissions to prevent unauthorized actions. A thorough review of the complete, untruncated source code is also advised before deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes OpenZeppelin's `Context` for standard utilities, which generally contributes to robust code security (7.2 Code Security). However, a critical architectural flaw (7.1… |
| **Governance / Economics** | 7/10 | Low | The economic model (7.4 Economic) is severely impacted by the lack of a supply mechanism; the token cannot be created or destroyed, rendering it economically inert. There are no governance mechanisms… |
| **Upgrades** | 9/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades), as indicated by `is_proxy: false`. Therefore, upgrade safety is not a concern, and the contract's logic is immutable once deployed. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 1 Informational_

### `C-01` — Missing Constructor and Uninitialized Token Metadata  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract lacks a constructor. The internal `_init(string memory name_, string memory symbol_)` function, which is intended to set the token's name and symbol, is never called. Consequently, `_name` and `_symbol` will remain empty strings, and `_totalSupply` will remain zero, making the token non-functional upon deployment. This impacts 7.1 Architecture and 7.8 Operations.

**Recommendation:** Implement a public constructor that calls `_init` with the desired token name and symbol. For example: `constructor(string memory name_, string memory symbol_) { _init(name_, symbol_); }`.


### `H-01` — Lack of Supply Mechanism  *(Severity: High · Status: Unresolved)*

The contract includes internal `_mint` and `_burn` functions, but no public or external functions are provided to call them. This means there is no mechanism to create or destroy tokens, rendering the ERC-20 token unusable as its `_totalSupply` will always remain zero. This directly impacts 7.4 Economic and 7.1 Architecture.

**Recommendation:** Implement public or owner-controlled functions (e.g., `mint(address to, uint256 amount)`) that call the internal `_mint` and `_burn` functions. These functions must be protected by appropriate access control mechanisms.


### `H-02` — Missing Access Control  *(Severity: High · Status: Unresolved)*

The `FourERC20` contract does not implement any access control mechanisms (e.g., `Ownable`, `AccessControl`). If privileged functions (such as minting, burning, or pausing) were to be added, they would be callable by any external address, leading to severe security vulnerabilities and potential loss of control over the token supply. This impacts 7.3 Access Control and 7.5 Governance.

**Recommendation:** Integrate a robust access control mechanism, such as OpenZeppelin's `Ownable` or `AccessControl` contracts. All functions intended for privileged users (e.g., future minting functions) must be protected with appropriate modifiers (e.g., `onlyOwner`).


### `I-01` — Truncated Code Snippet  *(Severity: Informational · Status: Unresolved)*

The provided source code for `FourERC20.sol` is truncated, specifically the `_transfer` function and potentially other parts of the contract. This limits the scope of the audit and prevents a complete security assessment of the entire codebase. This impacts 7.2 Code Security.

**Recommendation:** Provide the complete and untruncated source code for all contracts to enable a comprehensive security audit.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf1c5...4444`](https://bscscan.com/address/0xf1c599e9a5fbdea408a7409c0176a2fe42c64444) |
| **Network** | BNB Chain |
| **Price** | $0.001133 |
| **24h Volume** | $408.3K |
| **Liquidity** | $139.6K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 22.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3120 buys / 3396 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe6edc555061d1d9fe0145867b7ea7b07da840898)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hachiko-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*

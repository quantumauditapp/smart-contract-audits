---
token: ZygoSwap
ticker: ZSWAP
network: bsc
risk_score: 22
status: medium
date: 2026-06-10
---

# ZygoSwap (ZSWAP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 22/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zygoswap-bsc)

---

## Audit Summary

The FourERC20 contract implements a standard ERC-20 token using OpenZeppelin's battle-tested patterns. While the core token logic for transfers and allowances is robust, the contract suffers from critical architectural flaws. It lacks a public constructor to initialize its name and symbol, and crucially, it provides no public mechanism for minting tokens. These omissions render the token non-functional and unusable as a standalone ERC-20 asset, as its total supply will remain zero and its metadata uninitialized.

> **Final Recommendation:** To make the FourERC20 token functional, a public constructor must be added to properly initialize the token's name and symbol. Furthermore, public functions with appropriate access control should be implemented to allow for the minting and burning of tokens, enabling supply management. Consider integrating an access control mechanism like OpenZeppelin's Ownable for administrative functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages battle-tested OpenZeppelin ERC-20 implementations for core functionalities like `transfer` and `approve`, which inherently reduces common code security risks (7.2 Code… |
| **Governance / Economics** | 8/10 | Low | The contract implements a basic ERC-20 token with no complex economic model or governance mechanisms (7.4 Economic, 7.5 Governance). This simplicity reduces the attack surface related to economic… |
| **Upgrades** | 8/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades), which eliminates risks associated with proxy implementation, storage collisions, or upgrade path vulnerabilities. This design… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 2 Critical · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Missing Constructor for Initialization  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract includes an internal `_init` function for setting the token's name and symbol, but it lacks a public constructor to call this function. Consequently, upon deployment, the `_name` and `_symbol` state variables will remain uninitialized (empty strings), making the token non-compliant with standard ERC-20 metadata expectations and difficult to identify on block explorers. (7.1 Architecture, 7.8 Operations)

**Recommendation:** Implement a public constructor in `FourERC20` that calls `_init(name_, symbol_)` to properly set the token's metadata at deployment. For example: `constructor(string memory name_, string memory symbol_) { _init(name_, symbol_); }`


### `C-02` — No Public Minting Mechanism  *(Severity: Critical · Status: Unresolved)*

The contract provides an internal `_mint` function but does not expose any public or external function to invoke it. As a result, the `_totalSupply` will always remain zero, and no tokens can ever be created or distributed. This renders the ERC-20 token completely non-functional and unusable for its intended purpose. (7.1 Architecture, 7.4 Economic, 7.8 Operations)

**Recommendation:** Implement a public function (e.g., `mint(address to, uint256 amount)`) that calls the internal `_mint` function. This function should include appropriate access control (e.g., `onlyOwner`) to restrict who can mint new tokens.


### `M-01` — Lack of Administrative Control Functions  *(Severity: Medium · Status: Unresolved)*

The `FourERC20` contract does not inherit from `Ownable` or implement any custom access control mechanisms. This means there are no administrative functions to manage critical aspects such as pausing transfers, setting a minter role, or upgrading the contract (if it were part of a proxy system). This limits operational flexibility and the ability to respond to emergencies or evolving protocol needs. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Consider inheriting from OpenZeppelin's `Ownable` or `AccessControl` to implement administrative roles. This would allow for controlled execution of sensitive functions, such as a `pause` mechanism or a designated minter role, if such functionalities are desired.


### `I-01` — Missing Events for Initialization  *(Severity: Informational · Status: Unresolved)*

The internal `_init` function, which sets the token's name and symbol, does not emit any event. While not a direct vulnerability, emitting an event (e.g., `Initialized(string name, string symbol)`) upon successful initialization would provide a clear on-chain record of these critical parameters, aiding off-chain monitoring and indexing services. (7.8 Operations)

**Recommendation:** Add an event emission within the `_init` function to log the token's name and symbol upon initialization.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2e44...4444`](https://bscscan.com/address/0x2e44ab95549b8a12afdb970bde5a6a78365e4444) |
| **Network** | BNB Chain |
| **Price** | $0.0003953 |
| **24h Volume** | $257 |
| **Liquidity** | $70.1K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 33.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd367e7ea6d26f408b1ccdaafdb251dda6dced821)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zygoswap-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

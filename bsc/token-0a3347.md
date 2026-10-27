---
token: 哈基米
ticker: 哈基米
network: bsc
risk_score: 0
status: low
date: 2026-08-31
---

# 哈基米 (哈基米) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-0a3347-bsc)

---

## Audit Summary

The audited contract, FourERC20, is intended to be an ERC20 token. However, it lacks a constructor to initialize its name and symbol, and crucially, it has no mechanism to mint tokens. This renders the contract completely non-functional as an ERC20 token, as its total supply will always be zero. This represents a critical functional failure.

> **Final Recommendation:** To make the FourERC20 token functional, a constructor must be added to initialize the `_name` and `_symbol` state variables. Furthermore, the constructor or a separate, access-controlled public function is required to call the `_mint` function, allowing for the creation of an initial token supply and subsequent minting if desired. Additionally, consider integrating standard OpenZeppelin modules like `Pausable` and `Ownable` for enhanced operational control and security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard OpenZeppelin ERC20 patterns, which generally contribute to robust code security (7.2 Code Security). However, a critical architectural flaw exists where the token's… |
| **Governance / Economics** | 10/10 | Low | The contract, as a basic ERC20 token, does not implement complex governance mechanisms (7.5 Governance). However, the complete absence of a token supply mechanism means the token has no economic… |
| **Upgrades** | 10/10 | Low | The contract is implemented directly and does not utilize any proxy patterns, meaning it is not upgradeable (7.7 Upgrades). This design choice eliminates upgrade-related risks such as proxy storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_🟡 2 Medium · 🟢 1 Low_

### `M-01` — Missing Constructor for Token Metadata Initialization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FourERC20` contract lacks a constructor. Consequently, the `_init` function, which sets the token's `_name` and `_symbol`, is never called. This results in the `name()` and `symbol()` functions returning empty strings, making the token's identity unclear and hindering its usability in applications (7.1 Architecture, 7.8 Operations).

**Recommendation:** Implement a constructor in the `FourERC20` contract that calls the internal `_init(string memory name_, string memory symbol_)` function with the desired token name and symbol. This ensures proper initialization of the token's metadata upon deployment.


### `M-02` — Absence of Token Supply Mechanism  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract does not provide any public or constructor-based mechanism to call the internal `_mint` function. As a result, the `_totalSupply` variable will always remain zero, and no tokens can ever be created or distributed. This renders the ERC20 token completely non-functional, as no transfers or balance operations can occur (7.1 Architecture, 7.4 Economic, 7.8 Operations).

**Recommendation:** Introduce a mechanism to mint tokens. This could be done by calling `_mint` within the constructor to create an initial supply for a designated address (e.g., the deployer), or by adding an access-controlled public `mint` function that allows authorized entities to create new tokens.


### `L-01` — Lack of Standard ERC20 Extensions for Operational Control  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FourERC20` contract implements the basic ERC20 standard but does not include common extensions such as `Pausable` functionality or `Ownable`/`AccessControl` for managing administrative roles. While not a direct vulnerability, the absence of these features means there is no emergency stop mechanism or explicit role-based access for potential future administrative actions (7.2 Code Security, 7.8 Operations).

**Recommendation:** Consider integrating OpenZeppelin's `Pausable` module to allow for emergency halting of transfers and `Ownable` or `AccessControl` to define and manage administrative roles. These additions enhance operational safety and provide flexibility for future governance or emergency scenarios.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x82ec...4444`](https://bscscan.com/address/0x82ec31d69b3c289e541b50e30681fd1acad24444) |
| **Network** | BNB Chain |
| **Price** | $0.01867 |
| **24h Volume** | $1.16M |
| **Liquidity** | $1.50M |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 65.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2120 buys / 1986 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc33bacff9141da689875e6381c1932348ab4c5cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-0a3347-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*

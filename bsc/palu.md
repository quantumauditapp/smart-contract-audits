---
token: Palu
ticker: PALU
network: bsc
risk_score: 0
status: low
date: 2026-08-30
---

# Palu (PALU) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/palu-bsc)

---

## Audit Summary

The FourERC20 contract is an implementation of the ERC-20 standard, largely based on OpenZeppelin's battle-tested libraries. However, the contract as provided lacks a constructor to initialize token parameters (name, symbol) and, critically, a mechanism to mint the initial supply of tokens. If deployed directly, this contract would result in a non-functional token with zero total supply, rendering it unusable for its intended purpose. This fundamental design flaw constitutes a critical vulnerability.

> **Final Recommendation:** It is strongly recommended to either implement a constructor within the `FourERC20` contract to initialize `_name`, `_symbol`, and mint an initial supply, or to deploy a derived contract that properly extends `FourERC20` with these essential functionalities. Without a constructor and a minting mechanism, the deployed token will be non-functional. Additionally, consider adding an `Ownable` or similar access control pattern if specific administrative functions (like pausing or further minting/burning) are desired post-deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages well-audited OpenZeppelin libraries for its core ERC-20 functionality, which contributes to strong code security (7.2 Code Security). Standard ERC-20 functions like `transfer`… |
| **Governance / Economics** | 9/10 | Low | The contract has no explicit governance mechanisms (7.5 Governance) or access control roles beyond the standard ERC-20 sender/spender model (7.3 Access Control). The economic model (7.4 Economic) is… |
| **Upgrades** | 10/10 | Low | The FourERC20 contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no specific upgrade-related risks. Any changes to the token's logic would require deploying a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Non-functional Token due to Missing Constructor and Minting Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FourERC20` contract, as provided, lacks a public constructor to initialize the token's `_name` and `_symbol` variables. More critically, it does not include any public or external function to mint an initial supply of tokens. The `_mint` function is internal, meaning it can only be called by the contract itself or a derived contract. If `FourERC20` is deployed directly, `_totalSupply` will remain 0, and no tokens can ever be created, rendering the token completely non-functional and unusable.

**Recommendation:** Implement a public constructor in `FourERC20` that calls `_init(name_, symbol_)` and `_mint(recipient, initialSupply)` to set the token's metadata and create an initial supply upon deployment. Alternatively, ensure that any contract inheriting `FourERC20` properly implements these initialization and minting steps in its own constructor.


### `I-01` — Use of Internal `_init` Function for Token Metadata  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses an internal function `_init(string memory name_, string memory symbol_)` to set the token's name and symbol. While this pattern is common in base contracts designed for inheritance, it means that if `FourERC20` is deployed directly without a derived contract calling `_init` in its constructor, the `_name` and `_symbol` state variables will remain empty strings. This contributes to the non-functional state of the token.

**Recommendation:** If `FourERC20` is intended to be directly deployable, convert `_init` into a public constructor. If it's strictly a base contract, ensure clear documentation for developers inheriting it to call `_init` in their derived contract's constructor.


### `I-02` — Adherence to OpenZeppelin Standards  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FourERC20` contract largely follows the structure and implementation patterns of OpenZeppelin Contracts for ERC-20 tokens. This includes using `Context` for `_msgSender()`, implementing standard ERC-20 functions, and including `increaseAllowance` and `decreaseAllowance` to mitigate common allowance-related issues. This adherence to well-audited and widely adopted standards enhances the contract's inherent security and reliability.

**Recommendation:** Continue to leverage and stay updated with OpenZeppelin's best practices and contract versions. Ensure any custom logic added in the future maintains the same high standards.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x02e7...4444`](https://bscscan.com/address/0x02e75d28a8aa2a0033b8cf866fcf0bb0e1ee4444) |
| **Network** | BNB Chain |
| **Price** | $0.001289 |
| **24h Volume** | $84.7K |
| **Liquidity** | $370.5K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 71.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 350 buys / 356 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x126fadb82cc4ab91e6cd03accaf209fb6d1ffaab)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/palu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

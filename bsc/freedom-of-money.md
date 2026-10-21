---
token: Freedom of Money
ticker: FREEDOM OF MONEY
network: bsc
risk_score: 0
status: low
date: 2026-08-30
---

# Freedom of Money (FREEDOM OF MONEY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/freedom-of-money-bsc)

---

## Audit Summary

The FourERC20 contract is a standard implementation of the ERC-20 token interface, largely based on OpenZeppelin Contracts. It provides core functionalities for token transfers, allowances, and balance management. The contract is designed as a base for further extension, requiring a derived contract to implement specific supply mechanisms (minting/burning) and a constructor to initialize token metadata. While the core logic is robust, its incompleteness as a standalone deployable token and the absence of explicit access control for potential administrative functions in derived contracts are key considerations.

> **Final Recommendation:** For deployment, ensure a derived contract properly implements a public constructor to initialize token metadata and includes robust access control for any exposed administrative functions, such as minting or burning. Consider integrating a pause mechanism if the token is part of a larger ecosystem requiring emergency control. If upgradeability is desired, deploy this contract as an implementation behind a well-audited proxy contract (e.g., UUPS or Transparent) and ensure the `_init` function is called correctly during proxy initialization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) of the FourERC20 contract is sound, leveraging well-audited OpenZeppelin libraries for its ERC-20 implementation. Code security (7.2) is high, with Solidity 0.8.0+… |
| **Governance / Economics** | 9/10 | Low | The contract does not implement any governance (7.5) or complex economic (7.4) models beyond standard ERC-20 token transfers. There are no fees, staking mechanisms, or voting functionalities. The… |
| **Upgrades** | 10/10 | Low | The FourERC20 contract is not designed as an upgradeable proxy (7.7) itself. While the internal `_init` function suggests it could be used as an implementation contract in a proxy pattern, the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Incomplete Token Implementation for Standalone Deployment  *(Severity: Medium · Status: Unresolved)*

The `FourERC20` contract is designed as a base ERC-20 implementation. It lacks a public constructor to set the token's `name` and `symbol` and does not expose public functions for `_mint` or `_burn`. This means the contract cannot be deployed as a fully functional, self-contained token without a derived contract adding these essential functionalities. Deploying this contract directly would result in a token with no initial supply and unchangeable default metadata.

**Recommendation:** A derived contract must be created that inherits from `FourERC20`. This derived contract should include a public constructor to call `_init(name_, symbol_)` and implement public functions (with appropriate access control) to utilize the internal `_mint` and `_burn` functionalities to manage the token supply.


### `L-01` — Absence of Explicit Access Control for Administrative Functions  *(Severity: Low · Status: Unresolved)*

The `_mint` and `_burn` functions are internal, and the `_init` function is also internal. While this is appropriate for a base contract, if a derived contract exposes these or similar administrative functions (e.g., for supply management), it must implement robust access control (7.3). The current contract does not include any access control mechanisms like `Ownable` or `AccessControl` to restrict who can perform such operations, which could lead to unauthorized actions if not properly handled by a derived contract.

**Recommendation:** When extending `FourERC20` with administrative functionalities (e.g., minting, burning, pausing), ensure that these functions are protected by appropriate access control mechanisms, such as OpenZeppelin's `Ownable` or `AccessControl` roles, to prevent unauthorized execution.


### `I-01` — Standard ERC-20 `approve` Front-Running Vulnerability  *(Severity: Informational · Status: Unresolved)*

The standard ERC-20 `approve` function is susceptible to a known front-running vulnerability. If a user approves an allowance for a spender, and then attempts to change that allowance to a different value, a malicious actor could front-run the second transaction by executing the first approved transaction. This would cause the second `approve` transaction to set an allowance based on an outdated state, potentially leading to an unintended allowance value. The contract does provide `increaseAllowance` and `decreaseAllowance` as mitigations.

**Recommendation:** Advise users to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying existing allowances. Educate users about the risks associated with directly calling `approve` to change an allowance.


### `I-02` — Lack of Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

The contract does not include a pause mechanism (7.8 Operations) to halt transfers or other critical operations in case of an emergency, such as a discovered vulnerability or a major market disruption. While not strictly required for all tokens, a pause function can be a valuable tool for mitigating risks in complex DeFi ecosystems.

**Recommendation:** Consider integrating a pause mechanism, such as OpenZeppelin's `Pausable` contract, into a derived token contract. This would allow a designated administrator to temporarily halt token operations during critical situations, providing a safety switch for the protocol.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3e17...4444`](https://bscscan.com/address/0x3e17ee3b1895dd1a7cf993a89769c5e029584444) |
| **Network** | BNB Chain |
| **Price** | $0.002602 |
| **24h Volume** | $135.1K |
| **Liquidity** | $392.3K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 73.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 959 buys / 518 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf79501dc9a6b78279a5b723fbf2d62234fa0fca6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/freedom-of-money-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

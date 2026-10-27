---
token: 错版马
ticker: 哭哭马
network: bsc
risk_score: 0
status: low
date: 2026-09-03
---

# 错版马 (哭哭马) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-0bdac3-bsc)

---

## Audit Summary

The FourERC20 contract provides a standard ERC-20 token implementation based on OpenZeppelin's well-audited contracts. The core token functionalities are robust. However, as a base contract, it lacks specific minting/burning mechanisms and initial supply definition, which would be critical for a complete token system. Potential re-initialization issues exist if used in an upgradeable proxy context without modification. Overall, the technical risk is low for the provided code.

> **Final Recommendation:** It is recommended to thoroughly audit any derived contracts that implement the minting, burning, and initial supply logic, as these will define the complete token's security and economic model. If this contract is intended for use as an implementation in an upgradeable proxy system, ensure the `_init` function is properly secured against multiple calls by converting it to an `initialize` function with an `initializer` modifier. Users should be aware of the standard ERC-20 `approve` front-running risk, although `increaseAllowance` and `decreaseAllowance` provide safer alternatives.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract (7.1 Architecture) is a standard ERC-20 implementation, inheriting from OpenZeppelin's battle-tested contracts, which contributes to high code quality and security. (7.2 Code Security)… |
| **Governance / Economics** | 10/10 | Low | As a base ERC-20 contract, FourERC20 does not define specific (7.4 Economic) tokenomics, such as initial supply, minting, or burning mechanisms. These critical aspects would be implemented in a… |
| **Upgrades** | 10/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades). The `_init` function, which sets immutable token properties, is an internal function. If this contract were to be used as an… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% |

## Security Findings

_🟢 2 Low · ⚪ 1 Informational_

### `L-01` — Potential Re-initialization in Proxy Context  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_init` function, which sets the token's name and symbol, is an internal function. If this `FourERC20` contract were to be used as an implementation contract in an upgradeable proxy pattern (e.g., UUPS or Transparent), this `_init` function could be called multiple times by malicious actors after deployment, leading to re-initialization of state variables. While the provided context states `is_proxy: false`, this is a common vulnerability when base contracts are repurposed for upgradeable systems without modification.

**Recommendation:** If this contract is intended to be used as an implementation for an upgradeable proxy, the `_init` function should be renamed to `initialize` and protected with OpenZeppelin's `initializer` modifier. This modifier ensures the function can only be called once, preventing re-initialization attacks.


### `L-02` — Standard ERC-20 `approve` Front-Running Risk  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC-20 `approve` function is susceptible to a known front-running vulnerability. If a user approves an amount, and then attempts to change that approved amount to a different value, a malicious actor observing the transaction can front-run the second `approve` call. This allows the attacker to spend the original approved amount before the new approval takes effect, and then also spend the newly approved amount.

**Recommendation:** While the contract includes `increaseAllowance` and `decreaseAllowance` functions to mitigate this, users should be educated to use these functions instead of directly calling `approve` to modify an existing allowance. If `approve` must be used to change an allowance, it is safer to first set the allowance to zero and wait for that transaction to confirm before setting the new allowance.


### `I-01` — Incomplete Token Implementation  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided `FourERC20` contract is a base implementation of the ERC-20 standard. It includes core functionalities like transfers and allowances but lacks concrete mechanisms for initial supply, minting, or burning tokens. These critical functionalities are left to be implemented in a derived contract via the `_mint` and `_burn` internal virtual functions.

**Recommendation:** Ensure that any derived contract implementing the `_mint` and `_burn` functions incorporates robust access control, supply caps, and other necessary security measures to prevent unauthorized token creation or destruction. A complete audit of the derived contract will be essential to assess the full security posture of the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x671e...4444`](https://bscscan.com/address/0x671ecbcb89ee3f85e2199294e723d309d98c4444) |
| **Network** | BNB Chain |
| **Price** | $0.003069 |
| **24h Volume** | $155.0K |
| **Liquidity** | $464.2K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 47.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1883 buys / 1104 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8c46930c8a84dc5f8f9f545be1e255ce41d0b206)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-0bdac3-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*

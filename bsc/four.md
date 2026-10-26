---
token: Four
ticker: FORM
network: bsc
risk_score: 62
status: medium
date: 2026-09-12
---

# Four (FORM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/four-bsc)

---

## Audit Summary

The FormToken contract is a standard ERC20 token implementation, inheriting from OpenZeppelin's `ERC20` and `Ownable2Step` contracts. The code adheres to well-established patterns, incorporating robust checks for common ERC20 operations and secure ownership transfer mechanisms. The use of `unchecked` blocks is appropriately guarded by prior `require` statements, preventing integer underflows. The contract is not upgradeable. Overall, the contract exhibits a low-risk profile.

> **Final Recommendation:** It is recommended to ensure that the multisig wallet designated as the owner is securely managed, with robust key management practices and a clear operational procedure for signing transactions. Regularly review the access permissions and roles within the multisig to prevent unauthorized actions. For any future deployments or integrations, consider conducting thorough testing, including unit, integration, and fuzz testing, to cover all possible execution paths and edge cases.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) is based on battle-tested OpenZeppelin ERC20 and Ownable2Step contracts, ensuring a solid foundation. Code security (7.2) is high, with `unchecked` arithmetic… |
| **Governance / Economics** | 1/10 | High | The governance model (7.5) relies on the `Ownable2Step` pattern, which enhances security by requiring the new owner to accept ownership, preventing accidental transfers to incorrect addresses. The… |
| **Upgrades** | 4/10 | Medium | The contract is not designed as an upgradeable proxy (7.7). This simplifies the architecture and eliminates risks associated with proxy patterns, such as storage collisions or incorrect… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Centralized Control by Owner  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract implements `Ownable2Step`, granting the owner significant control over administrative functions, specifically the ability to transfer ownership. While `Ownable2Step` improves the security of ownership transfers by requiring a two-step process, the owner (even if a multisig) still represents a central point of control. Malicious or compromised owner keys could lead to unauthorized ownership changes.

**Recommendation:** Ensure the owner's private keys (for the multisig signers) are secured with industry best practices. Implement robust operational security procedures for the multisig wallet, including strict access controls and multi-person authorization for all critical transactions. Consider exploring more decentralized governance models for future iterations if applicable to the project's goals.


### `I-01` — Unused Interfaces and Libraries  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract imports `IERC20Permit` and the `Math` library, but neither is utilized within the provided `ERC20` contract code. While this does not pose a direct security vulnerability, it adds unnecessary code and slightly increases deployment costs and contract size.

**Recommendation:** Remove any unused interfaces or libraries to optimize contract size and reduce deployment costs. If these components are intended for future functionality or extensions, consider adding them only when they become necessary.


### `I-02` — Standard ERC20 Approval Race Condition  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard `approve()` function in ERC20 is susceptible to a known front-running attack. If a user approves an amount for a spender, and then attempts to approve a different amount (either higher or lower) before the first transaction is mined, a malicious actor can front-run the second `approve` transaction. This could allow the malicious actor to spend the original approved amount, and then also spend the new approved amount, effectively doubling the spendable allowance or leading to unexpected behavior. While `increaseAllowance()` and `decreaseAllowance()` mitigate this, the base `approve()` function remains vulne

**Recommendation:** Educate users about the risks associated with directly calling `approve()` to change an existing allowance. Encourage the use of `increaseAllowance()` and `decreaseAllowance()` functions when modifying an existing allowance, as these functions are designed to prevent this specific race condition. If direct `approve()` calls are necessary, advise users to first set the allowance to zero before setting a new value.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5b73...e284`](https://bscscan.com/address/0x5b73a93b4e5e4f1fd27d8b3f8c97d69908b5e284) |
| **Network** | BNB Chain |
| **Price** | $0.2556 |
| **24h Volume** | $482.2K |
| **Liquidity** | $572.2K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3785 buys / 3507 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7cb113b487e025b3a69537fca579559433240cb5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/four-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*

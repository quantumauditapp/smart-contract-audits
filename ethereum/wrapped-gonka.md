---
token: Wrapped Gonka
ticker: WGNK
network: ethereum
risk_score: 35
status: medium
date: 2026-09-15
---

# Wrapped Gonka (WGNK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-gonka-eth)

---

## Audit Summary

This audit reviewed a standard ERC20 token implementation. The contract adheres largely to the ERC20 specification, providing core token functionalities like transfer, approval, minting, and burning. Key strengths include the use of Solidity 0.8.19, which provides default overflow/underflow checks, and the modular design with virtual functions for extensibility. However, the explicit use of `unchecked` blocks for additions in `_mint` and `_transfer` introduces a potential integer overflow risk for `_totalSupply` and individual balances. Other findings are informational, related to standard ERC20 behaviors and architectural considerations for derived contracts. Note that the provided `Address` library code was truncated, but it is not directly utilized by the `ERC20` contract under review.

> **Final Recommendation:** It is recommended to address the potential integer overflow in `_mint` and `_transfer` by either removing the `unchecked` blocks for additions or implementing explicit overflow checks. While `uint256` is large, ensuring arithmetic safety for `_totalSupply` and balances is crucial for token integrity. For any contracts inheriting from this ERC20, ensure that `_mint` and `_burn` functions, if exposed externally, are protected by robust access control mechanisms. Consider the implications of the standard ERC20 `approve` race condition and advise users to use `increaseAllowance`/`decreaseAllowance` where possible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements a standard ERC20 token, demonstrating good adherence to the specification (7.1 Architecture). It utilizes Solidity 0.8.19, benefiting from default arithmetic safety, though… |
| **Governance / Economics** | 4/10 | Medium | The contract represents a basic ERC20 token without inherent governance or complex economic mechanisms (7.4 Economic, 7.5 Governance). Its economic model is straightforward, relying on standard token… |
| **Upgrades** | 7/10 | Low | The provided contract is a standalone ERC20 implementation and does not incorporate any explicit upgrade mechanisms or proxy patterns (7.7 Upgrades). This simplifies the deployment and reduces the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.7% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `M-01` — Potential Integer Overflow in `_mint` and `_transfer` Additions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_mint` function increments `_totalSupply` and `_balances[account]` within an `unchecked` block. Similarly, `_transfer` increments `_balances[to]` within an `unchecked` block. While Solidity 0.8+ generally provides overflow protection, explicit `unchecked` blocks disable this. If `_totalSupply` or a specific `_balances[account]` or `_balances[to]` is near `type(uint256).max` and a sufficiently large `amount` is added, an overflow could occur. This would lead to incorrect token supply, incorrect user balances, and could potentially be exploited to create 'phantom' tokens or disrupt token economics (7.2 Code Security

**Recommendation:** Ensure that `_totalSupply` and individual `_balances` cannot overflow during addition. This can be achieved by either removing the `unchecked` blocks for additions (relying on default Solidity 0.8+ checks) or by adding explicit `require` statements to check for potential overflows before the addition, especially in `_mint` where `amount` is arbitrary. For `_transfer`, `_balances[to]` is bounded by `_totalSupply`, so if `_totalSupply` is handled correctly, `_balances[to]` overflow is less likely…


### `I-01` — Potential `increaseAllowance` Overflow  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `increaseAllowance` function directly adds `addedValue` to the current allowance without an explicit overflow check. While Solidity 0.8+ provides default overflow protection, if `allowance(owner, spender)` is already extremely high (e.g., near `type(uint256).max`) and `addedValue` is non-zero, an overflow could occur, resetting the allowance to a small value. This is an edge case for allowance manipulation (7.2 Code Security).

**Recommendation:** While highly improbable for practical use cases, consider adding an explicit overflow check for the addition in `increaseAllowance` if extreme allowance values are a concern, or rely on Solidity 0.8+ default checks by removing the `unchecked` block if it were present (though it's not in this specific function).


### `I-02` — Standard ERC20 `approve` Race Condition  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `approve` function is susceptible to a known front-running attack (7.4 Economic). If a user approves an amount, then approves a different amount for the same spender before the first transaction is mined, a malicious spender could front-run the second approval, causing the spender to be able to spend both the original and the new approved amounts. While `increaseAllowance` and `decreaseAllowance` mitigate some aspects of this, the core `approve` function still carries this risk.

**Recommendation:** Educate users about the `approve` race condition and recommend using `increaseAllowance` and `decreaseAllowance` functions when modifying an existing allowance, as these functions are less susceptible to this specific front-running vector. For new approvals, users should be aware of the risk.


### `I-03` — Internal `_mint` and `_burn` Require Careful Access Control in Derived Contracts  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_mint` and `_burn` functions are declared as `internal virtual`. This is appropriate for a base ERC20 contract, as it prevents direct external calls. However, any contract inheriting from this `ERC20` implementation that exposes these functionalities externally (e.g., via a public `mint` or `burn` function) *must* implement robust access control mechanisms (e.g., `onlyOwner`, `onlyMinter`) to prevent unauthorized token creation or destruction (7.3 Access Control, 7.1 Architecture).

**Recommendation:** When extending this `ERC20` contract, ensure that any external functions that call `_mint` or `_burn` are protected by appropriate and secure access control modifiers to restrict who can perform these sensitive operations.


### `I-04` — Empty `_beforeTokenTransfer` and `_afterTokenTransfer` Hooks  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_beforeTokenTransfer` and `_afterTokenTransfer` hook functions are implemented as empty virtual functions. While this is standard for a base ERC20 contract, it means no custom logic or security checks are enforced at the token transfer level by default (7.1 Architecture).

**Recommendation:** Derived contracts should consider implementing these hooks to add custom logic, such as pausing transfers, blacklisting addresses, enforcing KYC/AML, or integrating with other protocol-specific functionalities, if required for the project's specific use case.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x972a...2f68`](https://etherscan.io/address/0x972a7a92d92796a98801a8818bcf91f1648f2f68) |
| **Network** | Ethereum |
| **Price** | $0.2136 |
| **24h Volume** | $178.6K |
| **Liquidity** | $907.0K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 79.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 144 buys / 80 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x203ee836d417cf944133bbdd2c62b4bc7388c55d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-gonka-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*

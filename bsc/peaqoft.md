---
token: PeaqOFT
ticker: PEAQ
network: bsc
risk_score: 28
status: low
date: 2026-08-30
---

# PeaqOFT (PEAQ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/peaqoft-bsc)

---

## Audit Summary

The audit focused on the provided Solidity source code, which consists of standard OpenZeppelin `ERC20` and `Ownable` implementations. The code demonstrates high quality and adherence to best practices for a basic token. However, the specific `PeaqOFT` contract implementation was not provided, limiting the scope to generic OpenZeppelin components. Key findings include informational notes on the missing specific contract source, the standard ERC20 `approve` race condition, and the presence of the `IERC1363` interface without implementation in the provided code. Centralized ownership, while present, is mitigated by a multisig owner.

> **Final Recommendation:** Ensure that the full source code for the `PeaqOFT` contract, including any custom logic or overrides, is thoroughly audited to confirm its security posture. Implement a robust process for managing the multisig owner keys to prevent unauthorized access or loss of control. For any future token interactions, consider using the `approve(0)` then `approve(newAmount)` pattern to mitigate the ERC20 `approve` race condition, or utilize alternative approval mechanisms if available in the ecosystem.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) is based on well-vetted OpenZeppelin standards, ensuring a robust foundation. Code security (7.2) is strong, utilizing Solidity 0.8+ with safe math and comprehensive… |
| **Governance / Economics** | 4/10 | Medium | Access control (7.3) is managed via the `Ownable` pattern, restricting administrative functions like `transferOwnership` to a single owner. While this introduces centralization (L-01), the prefill… |
| **Upgrades** | 7/10 | Low | The provided contract is not designed as an upgradeable proxy (7.7), meaning its logic is immutable once deployed. This eliminates upgrade-related risks such as proxy misconfigurations or logic bugs… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — Centralized Ownership  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes the `Ownable` pattern, granting the `owner` address significant control over administrative functions such as `transferOwnership` and `renounceOwnership`. While the prefill indicates the owner is a multisig (0x3e3f35d49ff20262be309695c9c52ec14bdcf08b with 3/5 threshold), which mitigates single-point-of-failure risk, this still represents a centralized control point for the contract's management.

**Recommendation:** Ensure the multisig wallet managing ownership is highly secure, with robust key management practices and a sufficient threshold for transaction execution. Regularly review the multisig signers and their security practices. Consider implementing a time-lock for critical administrative actions to provide a window for community review or emergency intervention.


### `I-01` — Missing Specific Contract Source for `PeaqOFT`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code only contains OpenZeppelin base contracts (`Context`, `Ownable`, `ERC20`, etc.) and interfaces (`IERC1363`). The actual implementation of the `PeaqOFT` token, which would inherit from `ERC20` and potentially add custom logic or implement `IERC1363`, is not included. This limits the scope of the audit to the generic OpenZeppelin components only, and any specific vulnerabilities or features of the `PeaqOFT` contract itself could not be assessed.

**Recommendation:** Provide the complete source code for the `PeaqOFT` contract to enable a comprehensive security audit of its specific implementation and business logic.


### `I-02` — ERC20 `approve` Race Condition  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC20 `approve` function is susceptible to a front-running attack. If a user attempts to change an existing allowance by calling `approve` with a new value, a malicious actor can observe this transaction, front-run it by spending the original allowance, and then allow the new `approve` transaction to proceed. This results in the spender having access to the original allowance plus the new allowance, effectively spending more than intended. This is an inherent design pattern of ERC20 and not a flaw in this specific implementation.

**Recommendation:** Users should be advised to first set the allowance to zero (`approve(spender, 0)`) before setting a new non-zero allowance (`approve(spender, newAmount)`). Alternatively, consider using `increaseAllowance` and `decreaseAllowance` functions if available in a derived contract, or explore alternative approval mechanisms like ERC2612 (permit) for more secure allowance management.


### `I-03` — `IERC1363` Interface Present Without Implementation  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `IERC1363` interface, which defines `transferAndCall` and `approveAndCall` functionalities, is included in the provided source code. However, the `ERC20` abstract contract does not implement these functions. If the `PeaqOFT` contract (not provided) also does not implement them, users might expect these functionalities based on the interface's presence but find them unavailable, potentially leading to confusion or failed transactions.

**Recommendation:** If `PeaqOFT` is intended to support `IERC1363`, ensure the contract explicitly implements all functions defined in the interface. If not, consider removing the `IERC1363` interface import to avoid misleading users about supported functionalities.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8b9e...18f6`](https://bscscan.com/address/0x8b9ee39195ea99d6ddd68030f44131116bc218f6) |
| **Network** | BNB Chain |
| **Price** | $0.02385 |
| **24h Volume** | $175.8K |
| **Liquidity** | $89.3K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 72.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 759 buys / 747 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x83a9fd66c9515536d630cf818c41190b0372c6f6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/peaqoft-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

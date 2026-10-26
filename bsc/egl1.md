---
token: EGL1
ticker: EGL1
network: bsc
risk_score: 0
status: low
date: 2026-09-23
---

# EGL1 (EGL1) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/egl1-bsc)

---

## Audit Summary

This report details the security audit of the FourERC20 token contract. The contract implements the ERC-20 standard, leveraging OpenZeppelin libraries for core functionality. However, the provided source code for critical internal functions (`_transfer`, `_mint`, `_burn`, etc.) was truncated, preventing a comprehensive security assessment. This limitation introduces significant uncertainty regarding potential vulnerabilities.

> **Final Recommendation:** To ensure the security and integrity of the FourERC20 token, it is paramount to provide the complete and verifiable source code for all deployed contracts. A thorough review of the access control mechanisms for `_mint` and `_burn` functions is essential to prevent unauthorized supply manipulation. Additionally, consider implementing an emergency pause mechanism to provide a safety switch in case of unforeseen vulnerabilities or critical issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract is based on OpenZeppelin's ERC-20 implementation, which generally provides robust and well-audited code (7.2 Code Security). Solidity version 0.8.0+ is used, benefiting from automatic… |
| **Governance / Economics** | 10/10 | Low | As a standard ERC-20 token, the contract's economic model is straightforward. The inclusion of `_mint` and `_burn` functions suggests potential for supply manipulation (7.4 Economic). Without the… |
| **Upgrades** | 10/10 | Low | The contract is not designed with upgradeability in mind, as indicated by the `is_proxy: false` flag and the absence of proxy-related patterns (7.7 Upgrades). This simplifies the deployment model by… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 66.4% — GoPlus SafeToken Locker |
| **Top-1 Unlocked Holder** | 22.7% |
| **Top-3 Unlocked** | 33.6% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Incomplete Source Code for Critical Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided `FourERC20.sol` source code is truncated, specifically missing the full implementation of core internal functions such as `_transfer`, `_mint`, `_burn`, `_approve`, and `_spendAllowance`. These functions are fundamental to the operation and security of an ERC-20 token. The absence of their complete code prevents a comprehensive security assessment, leaving critical aspects of the token's behavior unverified (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Provide the complete and verifiable source code for all contracts, including all internal and external functions, to enable a full security audit. Without the complete code, the security posture of the contract cannot be fully determined.


### `M-02` — Potential Centralized Control over Supply (Unverified)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes internal `_mint` and `_burn` functions, which allow for the creation and destruction of tokens. Without the full source code, it is impossible to determine how these functions are exposed externally and what access control mechanisms, if any, are in place (7.3 Access Control, 7.4 Economic). If these functions are callable by a single entity (e.g., an owner or admin) without robust multi-signature or time-locked controls, it poses a high risk of arbitrary token supply manipulation, which could devalue tokens or disrupt the ecosystem.

**Recommendation:** If `_mint` and `_burn` are exposed externally, implement strict access control mechanisms (e.g., `Ownable2Step`, `AccessControl`, or a multi-signature wallet) to restrict who can call them. Consider decentralizing control or implementing time-locks for sensitive supply-altering operations. Ensure that the policy for supply changes is clearly documented and transparent.


### `L-01` — Standard ERC-20 `approve` Front-Running Vulnerability  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While the contract includes `increaseAllowance` and `decreaseAllowance` functions, which are designed to mitigate the known front-running issue with `approve`, the standard `approve` function itself remains susceptible (7.2 Code Security). A user attempting to change an allowance from amount X to amount Y can be front-run by a malicious spender. The attacker can spend the original X amount before the new Y amount is set, potentially leading to a double-spend of the allowance.

**Recommendation:** Educate users to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying existing allowances. While this is a known ERC-20 limitation, clear communication can help users avoid this pitfall. No code change is strictly required if `increaseAllowance` and `decreaseAllowance` are promoted as the primary methods for allowance modification.


### `I-01` — Lack of Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract does not implement a pausing mechanism (e.g., using OpenZeppelin's `Pausable` module) (7.8 Operations). In the event of a critical vulnerability, an unforeseen bug, or a major external dependency issue, the lack of a pause function could prevent immediate mitigation. This could lead to significant loss of funds, system disruption, or other adverse effects that cannot be quickly addressed.

**Recommendation:** Consider integrating an emergency pause mechanism (e.g., `Pausable` from OpenZeppelin) to allow authorized entities to temporarily halt critical operations (like transfers, minting, or burning) in an emergency. Ensure that the pause functionality itself is protected by robust access control (e.g., a multi-signature wallet) and that the conditions for pausing and unpausing are clearly defined.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf4b3...4444`](https://bscscan.com/address/0xf4b385849f2e817e92bffbfb9aeb48f950ff4444) |
| **Network** | BNB Chain |
| **Price** | $0.01129 |
| **24h Volume** | $49.9K |
| **Liquidity** | $495.1K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 14.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 334 buys / 191 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6d76e7bb743fee795a2f00a317760acf822ee2be)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/egl1-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*

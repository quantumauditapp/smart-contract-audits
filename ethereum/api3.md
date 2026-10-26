---
token: API3
ticker: API3
network: ethereum
risk_score: 48
status: medium
date: 2026-09-14
---

# API3 (API3) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/api3-eth)

---

## Audit Summary

This report details the security audit of the provided ERC20 token contract, which serves as the base for the Api3Token. The contract implements standard ERC20 functionality, leveraging well-vetted OpenZeppelin libraries for secure arithmetic operations and address handling. The primary technical risks are low due to robust code quality. However, the inherent centralized control via the `Ownable` pattern, particularly if it governs token minting/burning, introduces a medium governance and economic risk. The contract is not upgradeable, simplifying its lifecycle.

> **Final Recommendation:** It is recommended to ensure that the `Ownable` address is controlled by a robust multi-signature wallet or a well-designed governance contract to mitigate the risks associated with centralized control, especially if minting or burning functions are exposed. Consider implementing a pausable mechanism in the inheriting contract to provide an emergency stop functionality in case of unforeseen vulnerabilities or external threats. Regularly review and update dependencies to benefit from the latest security patches and compiler improvements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation (7.1 Architecture, 7.2 Code Security) is robust, utilizing battle-tested OpenZeppelin libraries like SafeMath for arithmetic safety and Address for secure external calls.… |
| **Governance / Economics** | 4/10 | Medium | The contract incorporates the `Ownable` pattern (7.3 Access Control, 7.5 Governance), granting a single owner significant control over the token. While the prefill indicates the owner is another… |
| **Upgrades** | 4/10 | Medium | The contract is not designed as an upgradeable proxy (7.7 Upgrades), as indicated by `is_proxy: false` in the prefill. This means the contract's logic is immutable once deployed, eliminating… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Token Supply (Potential)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes the `Ownable` pattern, granting a single address (or a controlling contract) significant administrative privileges. While the base ERC20 contract's `_mint` and `_burn` functions are internal, it is highly probable that the inheriting `Api3Token` contract exposes these functions to the owner. If so, the owner would have the ability to arbitrarily increase or decrease the total token supply, which can have substantial economic implications for token holders and the protocol's stability. The prefill indicates the owner is an 'Other-Contract', which could be a multisig or governance, but the extent of

**Recommendation:** If minting/burning capabilities are exposed to the owner, ensure that the owner address is controlled by a robust multi-signature wallet with a high threshold or a decentralized governance mechanism. Clearly document the owner's capabilities and any limitations. Consider time-locks for critical operations like large mints or burns to provide transparency and allow community reaction.


### `L-01` — Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with Solidity version `0.6.12`, based on pragmas `^0.6.0` and `^0.6.2`. While `SafeMath` is used to prevent arithmetic overflows/underflows, newer Solidity versions (e.g., `0.8.x` and above) include built-in overflow and underflow checks by default. Using an older compiler version may miss out on recent language improvements, optimizations, and security features introduced in later versions.

**Recommendation:** Consider upgrading the Solidity compiler version to `0.8.x` or higher. This would allow for the removal of `SafeMath` library usage, simplifying the code and leveraging the compiler's native safety features. Thorough testing would be required after any compiler upgrade.


### `I-01` — Lack of Pausability Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The ERC20 contract does not include a pausable mechanism. In the event of a critical vulnerability within the token contract itself, or in an integrated DeFi protocol, there is no emergency stop function to temporarily halt transfers or other critical operations. This means that if an exploit occurs, funds could be drained or manipulated without an immediate way to intervene.

**Recommendation:** Consider integrating OpenZeppelin's `Pausable` contract into the inheriting `Api3Token` contract. This would allow the owner (or a designated role) to pause and unpause token transfers and other sensitive functions in an emergency, providing a crucial safety mechanism. Implement clear access control for the pause functionality.


### `I-02` — ERC20 `approve` Race Condition  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC20 `approve` function is susceptible to a known race condition. If a user approves an allowance for a spender, and then attempts to change that allowance, a malicious actor could front-run the second `approve` transaction. This could result in the spender spending the original allowance, and then also spending the new allowance, effectively doubling the approved amount. While `increaseAllowance` and `decreaseAllowance` functions are provided to mitigate this, direct `approve` calls remain vulnerable.

**Recommendation:** Educate users and integrated protocols to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying an existing allowance. If `approve` must be used, advise users to first set the allowance to zero and wait for that transaction to confirm before setting the new allowance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0b38...b88a`](https://etherscan.io/address/0x0b38210ea11411557c13457d4da7dc6ea731b88a) |
| **Network** | Ethereum |
| **Price** | $0.2497 |
| **24h Volume** | $73.7K |
| **Liquidity** | $419.9K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 69.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 63 buys / 87 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x81a98ae40148e298c77bd43082c6baf2b69c2940e3815c6b56c11dd2c467b05f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/api3-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*

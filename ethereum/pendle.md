---
token: Pendle
ticker: PENDLE
network: ethereum
risk_score: 34
status: low
date: 2026-09-02
---

# Pendle (PENDLE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 34/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pendle-eth)

---

## Audit Summary

This audit was conducted on the provided Solidity source code, which consists of OpenZeppelin's `Address.sol` library and `IERC20.sol` interface. The main `PENDLE` token contract, which presumably utilizes these components, was not provided for review. Therefore, the scope of this report is limited to the security and best practices observed in the provided library and interface files, and does not cover the full PENDLE token implementation or its specific business logic.

> **Final Recommendation:** For the full PENDLE token implementation, it is crucial to ensure that all custom logic adheres to the highest security standards, including rigorous testing and formal verification. Developers should carefully consider the implications of using library functions, especially those that transfer control or value, and implement appropriate reentrancy guards and access controls. A comprehensive audit of the complete PENDLE token contract, including its specific business logic and interactions with external protocols, is strongly recommended to identify and mitigate any project-specific vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The provided code, consisting of OpenZeppelin's `Address` library and `IERC20` interface, demonstrates high technical quality and adherence to established security patterns (7.2 Code Security). The… |
| **Governance / Economics** | 2/10 | High | Due to the absence of the main PENDLE token contract and any associated governance or economic logic, a comprehensive assessment of governance and economic risks (7.4 Economic, 7.5 Governance) cannot… |
| **Upgrades** | 6/10 | Medium | The provided `Address` library and `IERC20` interface are not designed to be upgradeable contracts (7.7 Upgrades). The pre-analysis indicates that the main contract is not a proxy (`is_proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Limitations of `Address.isContract` Function  *(Severity: Informational · Status: Unresolved)*

The `Address.isContract` function, which relies on `extcodesize`, has known limitations as explicitly documented within the library itself. It returns `false` for externally-owned accounts (EOAs), contracts in construction, addresses where a contract will be created, or addresses where a contract previously existed but was destroyed. This means `isContract` cannot definitively confirm if an address is an active, fully deployed contract in all scenarios.

**Recommendation:** Developers should be fully aware of the documented limitations of `Address.isContract` and avoid using it as a sole definitive check for contract existence, especially in security-critical contexts where precise contract state is required. Consider alternative checks or design patterns if a more robust contract verification is needed.


### `I-02` — Reentrancy Warning in `Address.sendValue`  *(Severity: Informational · Status: Unresolved)*

The `Address.sendValue` function, while designed to safely send Ether, explicitly includes a warning about potential reentrancy vulnerabilities if control is transferred to a recipient. This highlights that while the library function itself is secure, the calling contract must implement proper reentrancy protection (e.g., using `ReentrancyGuard` or the checks-effects-interactions pattern) when using `sendValue` to prevent malicious re-entry attacks.

**Recommendation:** Any contract utilizing `Address.sendValue` (or similar functions that transfer value and control) must implement robust reentrancy protection for functions that modify state after an external call. Adhere strictly to the checks-effects-interactions pattern to ensure state changes occur before external calls.


### `I-03` — Use of Low-Level Calls and Inline Assembly  *(Severity: Informational · Status: Unresolved)*

The `Address` library internally utilizes low-level calls (`call`, `staticcall`, `delegatecall`) and inline assembly (e.g., `extcodesize`, `revert` in `_verifyCallResult`). While these are necessary for the library's functionality and are carefully wrapped with safety checks and error handling, direct use of such low-level constructs in custom contract logic can introduce significant security risks if not handled with extreme care. The library itself disables `solhint` warnings for these specific lines, acknowledging their inherent complexity.

**Recommendation:** Developers should generally avoid direct low-level calls and inline assembly in their application-specific logic unless absolutely necessary and thoroughly understood. When using functions from the `Address` library, trust that its internal mechanisms are secure, but remain vigilant about the potential dangers if similar patterns are implemented without the same level of rigorous safety checks and error handling.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8085...a827`](https://etherscan.io/address/0x808507121b80c02388fad14726482e061b8da827) |
| **Network** | Ethereum |
| **Price** | $1.9700 |
| **24h Volume** | $140.3K |
| **Liquidity** | $210.9K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 70.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 54 buys / 62 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xd790576b49a17562cd29054c4dd79d3c3fa17aeb14432cd9c20dc3b382f5042c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pendle-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*

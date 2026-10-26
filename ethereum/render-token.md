---
token: Render Token
ticker: RNDR
network: ethereum
risk_score: 50
status: medium
date: 2026-09-23
---

# Render Token (RNDR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/render-token-eth)

---

## Audit Summary

The RenderToken contract, serving as an implementation behind an AdminUpgradeabilityProxy, integrates ERC-20 token functionality with a custom migration system and an escrow mechanism. While it utilizes SafeMath and SafeERC20 for arithmetic safety and includes functions to mitigate ERC-20 approval front-running, a critical design flaw renders the escrow's funding mechanism unusable. Significant centralization exists in escrow disbursement, and the use of an older Solidity compiler version combined with a legacy proxy pattern and custom migration logic introduces elevated technical and upgrade risks.

> **Final Recommendation:** Address the critical design flaw in the `Escrow.fundJob` function to enable proper external funding. Re-evaluate the centralization of control over escrow disbursements, potentially implementing a multi-signature wallet or a more decentralized governance mechanism for critical operations. Consider a comprehensive review of the upgrade architecture, especially given the legacy proxy and custom migration logic, to mitigate risks of storage collisions and ensure future upgrade safety. Finally, migrate to a modern Solidity compiler version to benefit from enhanced security features and optimizations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | 7.1 Architecture and 7.2 Code Security are generally robust due to the use of SafeMath and SafeERC20 libraries, mitigating common integer overflow/underflow issues. The implementation of… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects present significant risks. The `Escrow.fundJob` function's access control (7.3 Access Control) is critically flawed, making it impossible for external users to… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via an `AdminUpgradeabilityProxy`, a legacy proxy pattern, combined with a custom `Migratable` contract for initialization and migration steps. This combination, along with… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 85.8% |
| **Top-3 Unlocked** | ⚠️ 96.9% |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Custom String-Based Migration Logic Complexity  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Migratable` contract implements a custom migration and initialization system using string-based `contractName` and `migrationId` parameters. This approach, while functional, is less standardized than typical proxy-based upgrade mechanisms. Relying on exact string matching for migration IDs can be prone to human error (e.g., typos), potentially leading to failed initializations or migrations, leaving the contract in an inconsistent or uninitialized state. The complexity of managing these string identifiers across multiple inherited contracts adds to the maintenance burden.

**Recommendation:** While the system is in place, ensure rigorous testing of all initialization and migration paths. For future iterations or new contracts, consider adopting more standardized and less error-prone initialization patterns, such as those provided by OpenZeppelin's `Initializable` contract, which typically use a boolean flag or version number for initialization control.


### `M-02` — Critical Design Flaw: Escrow Funding Mechanism Unusable  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `fundJob` function in the `Escrow` contract, intended for depositing tokens into job-specific balances, includes the requirement `require(msg.sender == renderTokenAddress)`. During initialization, `renderTokenAddress` is set to `address(this)`, meaning the contract's own address. Consequently, only the contract itself can call `fundJob`, making it impossible for external users or other contracts to deposit funds into the escrow. This renders the core functionality of the escrow system for receiving external funds completely non-functional.

**Recommendation:** Modify the `fundJob` function's access control to allow authorized external entities (e.g., the `owner`, a designated `funder` role, or any token holder) to deposit funds. For example, remove the `require(msg.sender == renderTokenAddress)` line and instead ensure that the `ERC20(renderTokenAddress).transferFrom(msg.sender, address(this), _tokens)` is called to pull tokens from the caller.


### `M-03` — Centralized Control Over Escrow Funds  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Escrow` contract's `disburseJob` function, which transfers tokens from job balances to recipients, is protected by the `canDisburse` modifier, allowing only the `disbursalAddress` to execute it. The `disbursalAddress` is initially set to the `owner` and can be changed by the `owner`. This design concentrates significant power in a single address, creating a single point of failure. If the `disbursalAddress` (or the `owner` who can change it) is compromised, all funds held within the escrow could be maliciously disbursed or stolen.

**Recommendation:** Consider implementing a multi-signature wallet for the `disbursalAddress` or introducing a more robust governance mechanism (e.g., a time-locked contract, a DAO vote) for critical operations like changing the `disbursalAddress` or executing large disbursements. This would distribute control and reduce the risk associated with a single point of failure.


### `M-04` — Legacy Proxy Pattern and Elevated Upgrade Risks  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is deployed as an implementation behind an `AdminUpgradeabilityProxy`, a legacy proxy pattern from OpenZeppelin (formerly ZeppelinOS). This, combined with the use of `pragma solidity ^0.4.24` and a custom `Migratable` initialization system, introduces elevated risks for future upgrades. Storage collisions are a significant concern with multiple inheritance and older Solidity versions if new state variables are not carefully managed in upgrade implementations. The custom `Migratable` pattern adds another layer of complexity to the standard proxy upgrade process, increasing the potential for misconfiguration

**Recommendation:** Thoroughly review the upgrade strategy, including the interaction between the `AdminUpgradeabilityProxy` and the custom `Migratable` logic. Ensure a robust testing framework for upgrades, specifically focusing on storage layout compatibility and correct initialization across versions. Consider migrating to a more modern and well-audited proxy pattern (e.g., UUPS with a newer Solidity version) in a future major upgrade to reduce inherent risks.


### `L-01` — Use of `assert` for External Call Validation in `SafeERC20`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SafeERC20` library uses `assert(token.transfer(to, value))` and `assert(token.transferFrom(from, to, value))` to validate the success of external ERC-20 token transfers. In Solidity 0.4.x, `assert` consumes all remaining gas on failure. While this ensures that failed transfers revert, it is less gas-efficient than using `require` for input validation or checking return values, which refunds unused gas on failure. This is a minor gas inefficiency rather than a direct security vulnerability.

**Recommendation:** For future development or if upgrading to a newer Solidity version, consider replacing `assert` with `require` for external call success checks. For example, `require(token.transfer(to, value), 'ERC20 transfer failed');` would be more gas-efficient on failure.


### `I-01` — Outdated Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with `pragma solidity ^0.4.24`. This is an outdated compiler version. While `SafeMath` is used to mitigate common arithmetic issues, newer Solidity versions (e.g., 0.8.x) offer significant improvements in security features (e.g., default checked arithmetic, `try/catch` for external calls), optimizations, and bug fixes. Using an older compiler might expose the contract to known compiler-specific vulnerabilities that have since been patched, or prevent the use of modern security patterns.

**Recommendation:** Consider upgrading the contract to a more recent and actively maintained Solidity compiler version (e.g., 0.8.x) during a future major upgrade. This would allow the contract to benefit from the latest security enhancements, compiler optimizations, and improved developer tooling. A thorough re-audit would be required after such an upgrade.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6de0...eb24`](https://etherscan.io/address/0x6de037ef9ad2725eb40118bb1702ebb27e4aeb24) |
| **Network** | Ethereum |
| **Price** | $1.8100 |
| **24h Volume** | $43.6K |
| **Liquidity** | $401.8K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 6y |
| **Top-10 Holders** | 93.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 103 buys / 113 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc0a6bb3d31bb63033176edba7c48542d6b4e406d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/render-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*

---
token: LienFi
ticker: LFI
network: base
risk_score: 63
status: high
date: 2026-08-12
---

# LienFi (LFI) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lienfi-base)

---

## Audit Summary

The CloneDERC20VotesV2 contract implements an ERC20 token with voting capabilities, a vesting mechanism, and an inflation model. It leverages well-audited Solady libraries for core functionalities and uses an Ownable pattern for administrative control. The owner is a multisig, enhancing operational security. Key findings include unused state variables, potential gas limit issues in the inflation and vesting release functions under extreme conditions, and a design choice regarding inflation token distribution. The contract is designed with `Initializable` but is reported as not being a proxy.

> **Final Recommendation:** It is recommended to address the identified medium-severity issues to enhance the contract's robustness and long-term operational stability. Specifically, consider alternative patterns for the `mintInflation` loop and `release` function's iteration to prevent potential gas limit issues. Clarify or remove the unused `pool` and `isPoolLocked` variables to avoid confusion and potential future integration risks. Ensure the economic implications of the owner receiving all inflation tokens align with the project's long-term vision and communicate this clearly to stakeholders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract's architecture (7.1) is clear, utilizing Solady libraries for robust ERC20, ERC20Votes, and Ownable implementations. Code security (7.2) is generally strong, with no apparent reentrancy… |
| **Governance / Economics** | 5/10 | Medium | The economic model (7.4) includes a capped yearly inflation rate and a vesting mechanism. Inflation tokens are minted directly to the `owner()`, which is a multisig, mitigating the risk of a single… |
| **Upgrades** | 2/10 | High | The contract includes the `Initializable` base contract (7.7), suggesting it was designed with upgradeability in mind, typically for deployment behind a proxy. However, the provided information… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 69.9% |
| **Top-3 Unlocked** | ⚠️ 99.1% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Unused `pool` and `isPoolLocked` Variables  *(Severity: Medium · Status: Unresolved)*

The `pool` address and `isPoolLocked` boolean state variables are declared and can be set by the `onlyOwner` functions `lockPool` and `unlockPool`. However, these variables are never read or used anywhere else in the contract to restrict or enable any functionality. This indicates either incomplete features, dead code, or a misunderstanding of their intended purpose, which can be misleading and potentially lead to future vulnerabilities if these variables are later integrated without proper security review.

**Recommendation:** Either implement the intended logic that utilizes the `pool` address and `isPoolLocked` flag, or remove these variables and their associated functions if they are not part of the current design. If they are placeholders for future functionality, clearly document their purpose and ensure a thorough security review is conducted before activating any logic dependent on them.


### `M-02` — Potential Gas Limit Issues in `mintInflation` Loop  *(Severity: Medium · Status: Unresolved)*

The `mintInflation` function contains a `while` loop that iterates for each full year that has passed since `currentYearStart`. While `currentYearStart` is updated to `block.timestamp` upon `unlockPool` and within `mintInflation` itself, if the contract is left un-minted for an extremely long period (e.g., many centuries), this loop could iterate a significant number of times. This could potentially exceed the block gas limit, preventing the inflation mechanism from being triggered and leading to a denial of service for token minting.

**Recommendation:** Consider an alternative approach for calculating inflation over multiple years that avoids a `while` loop, such as a formula-based calculation or a mechanism that caps the number of iterations. Alternatively, ensure that `mintInflation` is called regularly (e.g., via a keeper bot) to prevent `currentYearStart` from becoming excessively old.


### `M-03` — Potential Gas Limit Issues in `release()` for Many Schedules  *(Severity: Medium · Status: Unresolved)*

The `release()` function (without a `scheduleId` parameter) and `computeAvailableVestedAmount(address beneficiary)` iterate over the `_scheduleIdsOf[beneficiary]` array to process all vesting schedules for a given beneficiary. While the `initialize` function includes checks like `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD`, these primarily limit the total *amount* allocated, not the *number* of individual vesting schedules. If a single beneficiary is allocated an extremely large number of distinct vesting schedules during initialization, iterating through this array could become gas-intensive, potentially leading to a denial of service for that beneficiary's ability to claim…

**Recommendation:** During the contract deployment and initialization phase, ensure that the number of vesting schedules allocated to any single beneficiary remains within reasonable limits to prevent excessive gas consumption. If a very large number of schedules per beneficiary is a design requirement, consider implementing a paginated claim mechanism or a way to claim a subset of schedules to avoid hitting gas limits.


### `L-01` — Owner Receives All Inflation Tokens  *(Severity: Low · Status: Unresolved)*

The `mintInflation` function mints all newly generated inflation tokens directly to the `owner()`. While the owner is a multisig (0x660eaaedebc968f8f3694354fa8ec0b4c5ba8d12, 3/6 threshold), this design centralizes the control of all newly minted supply. Depending on the project's economic model and governance structure, this could be perceived as a centralization risk, as the owner has sole discretion over the distribution or use of these tokens, potentially impacting market dynamics.

**Recommendation:** Clearly document the intended use and distribution strategy for the inflation tokens received by the owner. If a more decentralized distribution is desired in the future, consider implementing a governance-controlled treasury or a mechanism to distribute inflation directly to stakers or other protocol participants.


### `I-01` — Truncated Vesting Logic in `_available` Function  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `_available` function is truncated at the point where the linear vesting calculation (`else { ves...`) would typically be implemented. Without the full code, a complete security analysis of the linear vesting logic, including potential edge cases like division by zero or incorrect calculation, cannot be performed.

**Recommendation:** Provide the complete and untruncated source code for a comprehensive audit. Assuming a standard linear vesting implementation, ensure it correctly handles edge cases such as `s.duration == s.cliff` (which should be covered by the `if (t >= start + s.duration)` condition if `s.cliff == s.duration`) and avoids any potential for division by zero.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3722...aba3`](https://basescan.org/address/0x3722264ab15a1dfce5a5af89e6547f7949a8aba3) |
| **Network** | Base |
| **Price** | $0.00005673 |
| **24h Volume** | $37.6K |
| **Liquidity** | $577.0K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 50.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 73 buys / 176 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x6ef02666f150d9649655b884e043b61b0990fad9be4c632d0c7568bb24da9367)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lienfi-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*

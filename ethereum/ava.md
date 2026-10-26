---
token: AVA
ticker: AVA
network: ethereum
risk_score: 55
status: medium
date: 2026-09-18
---

# AVA (AVA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ava-eth)

---

## Audit Summary

The AVA token contract implements an ERC20 token with a time-based inflationary minting model, leveraging OpenZeppelin's `ERC20PresetMinterPauser`. A critical vulnerability was identified where public minting functions lack proper role-based access control, allowing unauthorized token minting. Additionally, an inconsistency in the inflationary model's year-tracking logic and the admin's ability to indefinitely increase the maximum supply pose further risks to the token's integrity and economic model.

> **Final Recommendation:** Address the critical access control vulnerability immediately by implementing proper role checks (e.g., `onlyRole(MINTER_ROLE)`) on all custom minting functions. Review and refine the `addNewYearForInflationaryModel` logic to ensure consistent and sequential addition of inflationary years, preventing unintended gaps. Consider the long-term implications of the `increaseMaxSupply` mechanism and communicate its potential impact on token supply to the community. Ensure robust monitoring of the `DEFAULT_ADMIN_ROLE` and its associated permissions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes OpenZeppelin's `ERC20PresetMinterPauser` for core ERC20 functionality and access control (7.1 Architecture). The code generally follows good practices for Solidity 0.8.18… |
| **Governance / Economics** | 1/10 | High | The tokenomics are based on a predefined 10-year inflationary schedule, with the `DEFAULT_ADMIN_ROLE` having significant power to modify future yearly mint amounts, add new years, and increase the… |
| **Upgrades** | 3/10 | High | The AVA contract is deployed as a standard, non-upgradeable implementation (7.7 Upgrades). This design choice means that any identified vulnerabilities or desired feature changes would necessitate a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Inconsistent `inflationaryModelTotalYears` Update Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `addNewYearForInflationaryModel` function's logic for updating `inflationaryModelTotalYears` can lead to gaps in the inflationary model. If `getCurrentYear()` is significantly ahead of `inflationaryModelTotalYears`, the function will set `inflationaryModelTotalYears = currentYear`, skipping intermediate years. This means `inflationaryModelPerYear` entries for the skipped years will remain zero, preventing minting during those periods if `getCurrentYear()` falls within them, potentially disrupting the token's planned inflation schedule.

**Recommendation:** Refine the logic in `addNewYearForInflationaryModel` to ensure that new years are added sequentially or allow the admin to specify the exact `yearID` to add, ensuring no gaps are created in the inflationary model. For example, ensure `inflationaryModelTotalYears` is always `currentYear` or `inflationaryModelTotalYears + 1` when adding a new year.


### `M-02` — Unauthorized Minting via Public Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mintCurrentYear`, `mintRemainingCurrentYear`, and `mintRemainingPastYear` functions are declared `public` but lack any access control checks (e.g., `onlyRole(MINTER_ROLE)`). This allows any external caller to mint tokens up to the yearly limits defined by the inflationary model, bypassing the intended authorization mechanism provided by `ERC20PresetMinterPauser` and leading to uncontrolled inflation.

**Recommendation:** Implement appropriate role-based access control for all custom minting functions. For instance, add `onlyRole(MINTER_ROLE)` or `onlyRole(DEFAULT_ADMIN_ROLE)` to `mintCurrentYear`, `mintRemainingCurrentYear`, and `mintRemainingPastYear` to restrict their execution to authorized accounts.


### `L-01` — Admin Can Increase `MAX_SUPPLY` Indefinitely  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `increaseMaxSupply` function allows the `DEFAULT_ADMIN_ROLE` to increase the `MAX_SUPPLY` by a percentage of the `totalSupply` once per year after the initial 10-year period. While restricted to a percentage less than 100%, this mechanism, if repeatedly invoked over many years, could lead to a significantly higher total supply than initially anticipated, potentially diluting existing token holders over a long timeframe.

**Recommendation:** Consider implementing a hard cap on the total `MAX_SUPPLY` or a maximum number of times the `increaseMaxSupply` function can be called. Clearly communicate the long-term implications of this mechanism to token holders to manage expectations regarding potential supply dilution.


### `I-01` — Hardcoded Initial Inflationary Model Limits Flexibility  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The inflationary model for the first 10 years is hardcoded in the constructor. While `updateInflationaryModelPerYear` allows modification of future years, it requires `yearID >= currentYear`. This design choice prevents the admin from adjusting the minting schedule for any of the initial 10 years that have not yet passed, limiting flexibility in response to unforeseen economic conditions.

**Recommendation:** This is a design choice. If greater flexibility is desired, consider allowing the admin to update future years within the initial 10-year period, perhaps with a grace period or a multi-signature approval process.


### `I-02` — Reliance on `block.timestamp` for Critical Logic  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `getCurrentYear` function, which is central to the inflationary model and `MAX_SUPPLY` increase logic, relies on `block.timestamp`. While acceptable for long durations like years, `block.timestamp` can be manipulated by miners within a small range (up to 900 seconds on Ethereum), potentially affecting the precise timing of year transitions.

**Recommendation:** For yearly calculations, `block.timestamp` is generally considered acceptable. However, for extremely time-sensitive operations, consider using a decentralized oracle for time if precise, unmanipulable time is critical, though this adds complexity and external dependencies.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa6c0...ceb9`](https://etherscan.io/address/0xa6c0c097741d55ecd9a3a7def3a8253fd022ceb9) |
| **Network** | Ethereum |
| **Price** | $0.2535 |
| **24h Volume** | $464.2K |
| **Liquidity** | $168.2K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 2y |
| **Top-10 Holders** | 74.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 812 buys / 809 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x41e570fc65d0f9efe89a6145306e2ba7b8a0fa6b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ava-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-18*

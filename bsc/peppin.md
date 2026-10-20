---
token: Peppin
ticker: PEPPIN
network: bsc
risk_score: 53
status: medium
date: 2026-09-23
---

# Peppin (PEPPIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/peppin-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and a multi-state pool system. It leverages OpenZeppelin's upgradeable contracts and gas-efficient storage. Key findings include a high-severity reentrancy vulnerability in the tax liquidation logic and a denial-of-service risk due to unhandled external call reverts. Centralized control by the owner over critical state transitions and potential storage collision risks during upgrades are also noted. The provided code for `_liquidateTax` was truncated, limiting full analysis of its conditions.

> **Final Recommendation:** Prioritize addressing the reentrancy vulnerability in `_liquidateTax` by implementing the Checks-Effects-Interactions pattern to ensure state updates precede external calls. Mitigate the denial-of-service risk by implementing robust error handling for external calls to `taxProcessor` and `dividendContract`. For future upgrades, meticulously plan any changes to the `PackedPoolState` struct to avoid storage collisions, and consider implementing a pause mechanism for emergency situations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good use of OpenZeppelin upgradeable standards and gas optimization with `PackedPoolState`. However, a significant reentrancy vulnerability exists in the `_liquidateTax`… |
| **Governance / Economics** | 4/10 | Medium | The economic model incorporates dynamic tax rates and state-based transitions, managed by an `OwnableUpgradeable` contract. The owner has centralized control over critical state changes like… |
| **Upgrades** | 8/10 | Low | The contract correctly utilizes OpenZeppelin's UUPS proxy pattern, including `Initializable` and `_disableInitializers` in the constructor, ensuring proper upgradeability (7.1 Architecture, 7.7… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Reentrancy Vulnerability in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function, called during every `_transfer`, modifies the `notLiquidating` state variable to `false` *before* making external calls to `ITaxProcessor(taxProcessor).processTax` and `IDividend(dividendContract).distributeDividends`. It resets `notLiquidating` to `true` *after* these calls. A malicious `taxProcessor` or `dividendContract` could re-enter the `_transfer` function (and thus `_liquidateTax`) while `notLiquidating` is `false`. This could lead to unexpected behavior, such as multiple liquidations within a single transaction, or other state manipulation if the re-entered logic relies on `notLiquidating` to prevent concurrent execution.

**Recommendation:** Implement a Checks-Effects-Interactions pattern. Move the external calls to `taxProcessor` and `dividendContract` *after* all state changes, including resetting `notLiquidating` to `true`. Consider using a reentrancy guard if complex interactions are unavoidable.


### `H-02` — Denial of Service via External Call Reverts  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function, which is called on every token transfer, makes external calls to `ITaxProcessor(taxProcessor).processTax` and `IDividend(dividendContract).distributeDividends`. If either of these external contracts reverts for any reason (e.g., misconfiguration, intentional attack, or unexpected state), the entire `_transfer` transaction will revert. This could lead to a denial of service, preventing all token transfers and potentially locking funds within the contract.

**Recommendation:** Implement robust error handling for external calls. Consider using `try/catch` blocks to gracefully handle reverts from `taxProcessor` and `dividendContract`, allowing transfers to proceed even if tax processing or dividend distribution fails. Alternatively, ensure these external contracts are highly reliable and audited, or design the system to allow the owner to disable/change them in case of issues.


### `M-01` — Centralized Control over Critical State Transitions  *(Severity: Medium · Status: Unresolved)*

The `startMigration` and `finalizeMigration` functions, which control the `PoolState` transitions from `BondingCurve` to `Migrating` and then to `TaxEnforcedAntiFarmer`, are protected by the `onlyOwner` modifier. This grants significant centralized control to the contract owner over the token's operational state, including when taxes are enforced and anti-farmer mechanisms are activated. While common for initial phases, this centralization could pose a risk if the owner's key is compromised or acts maliciously.

**Recommendation:** For long-term decentralization and security, consider transitioning critical administrative functions to a multi-signature wallet or a decentralized autonomous organization (DAO) governance mechanism. Clearly document the owner's responsibilities and the implications of their control.


### `M-02` — Potential for Storage Collisions in Future Upgrades  *(Severity: Medium · Status: Unresolved)*

The contract uses a `PackedPoolState` struct to optimize gas usage by packing multiple state variables into a single storage slot. While efficient, modifying the `PackedPoolState` struct (e.g., changing the order, type, or adding new fields) in a future upgrade could lead to storage collisions if not handled with extreme care. This could corrupt existing state variables, leading to unexpected behavior or loss of funds.

**Recommendation:** When performing upgrades, strictly adhere to the OpenZeppelin UUPS storage layout guidelines. New state variables should only be appended to the end of the contract's storage. If changes to `PackedPoolState` are necessary, consider a migration strategy or ensure that the new struct layout is fully compatible with the old one, which is often difficult to guarantee without careful planning and testing.


### `L-01` — Lack of Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract implements complex tax and state transition logic, and relies on external contracts for tax processing and dividend distribution. In the event of an emergency, such as a critical bug, an exploit in an external dependency, or a market manipulation attempt, there is no mechanism for the owner to temporarily pause transfers or critical operations. This could exacerbate losses or allow an attack to continue unchecked.

**Recommendation:** Consider implementing a `PausableUpgradeable` mechanism (e.g., from OpenZeppelin) to allow the owner (or a designated emergency multisig) to pause critical functions like `_transfer` in an emergency. This provides a crucial safety net, though it introduces another point of centralization.


### `I-01` — Truncated Code for `_liquidateTax` Function  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `_liquidateTax` function is truncated, specifically the condition `taxAmount >= currentPoolState.liqu...`. This prevents a full security analysis of the complete liquidation logic, including the exact conditions under which `ITaxProcessor` and `IDividend` calls are made.

**Recommendation:** Provide the complete and untruncated source code for a comprehensive audit.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa816...7777`](https://bscscan.com/address/0xa81697d866bfcfbdecd44134c5c02c7032c07777) |
| **Network** | BNB Chain |
| **Price** | $0.0002128 |
| **24h Volume** | $87.7K |
| **Liquidity** | $49.1K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 19d |
| **Top-10 Holders** | 33.6% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 799 buys / 447 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x3864300132ebfc073b9ab322fd51dc4ebe1fc089)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/peppin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*

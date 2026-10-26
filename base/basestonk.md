---
token: BaseStonk
ticker: BSTONK
network: base
risk_score: 19
status: low
date: 2026-08-30
---

# BaseStonk (BSTONK) — Smart Contract Security Analysis | Base

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/basestonk-base)

---

## Audit Summary

The AdvancedLaunchToken contract is an ERC20 token with a max wallet cap feature and an external reward tracker integration. The audit identified a critical denial of service vulnerability due to an unchecked external call that can block all transfers. High-severity issues include irreversible roles and external contract settings, and unchecked return values from external calls. The contract exhibits high centralization, with key administrative functions controlled by an immutable 'launcher' address. While the core ERC20 functionality is robust due to OpenZeppelin inheritance, the custom logic introduces significant operational and security risks.

> **Final Recommendation:** Prioritize addressing the critical denial of service vulnerability by implementing robust error handling for external calls to the `rewardTracker`. Consider using a try/catch block or ensuring the `rewardTracker` is a highly trusted and audited contract that cannot revert on `ping`. Evaluate the long-term implications of immutable administrative roles and single-set addresses. Implement mechanisms for role transfers or multi-signature control for critical functions like `launcher` and `rewardTracker` to enhance operational flexibility and reduce single points of failure. Ensure all external dependencies, especially the `rewardTracker`, are thoroughly audited and trusted.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's robust ERC20 implementation, providing a solid foundation for token functionality (7.2 Code Security). However, a critical vulnerability exists in the `_update`… |
| **Governance / Economics** | 5/10 | Medium | The contract exhibits high centralization, with the `launcher` address holding immutable control over critical functions like setting exemptions, the reward tracker, and finishing the launch (7.3… |
| **Upgrades** | 6/10 | Medium | The AdvancedLaunchToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This means that once deployed, its logic cannot be modified or updated. While this eliminates risks associated… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 38.1% |
| **Top-3 Unlocked** | 77.1% |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control over Max Wallet Exemptions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `launcher` address has the sole ability to add or remove addresses from the `exemptFromMaxWallet` list via the `setExempt` function. This centralization of control means a single entity can decide which users are subject to the `maxWalletBps` cap and which are not. This introduces a trust assumption in the `launcher` and could potentially be abused to unfairly exempt large holders or manipulate market dynamics (7.3 Access Control, 7.5 Governance).

**Recommendation:** Evaluate if this level of centralized control is necessary long-term. Consider transitioning this power to a more decentralized governance mechanism or a multi-signature wallet after the initial launch phase to reduce single-point-of-failure risk and increase transparency.


### `M-02` — Denial of Service via External Call Revert  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_update` function, called on every token transfer, includes an external call to `rewardTracker.call{gas: 600_000}(...)`. If this external call reverts for any reason (e.g., `rewardTracker` is a malicious contract, a buggy contract, or a non-contract address), the entire `_update` transaction will revert. This effectively blocks all token transfers for all users, creating a severe denial of service vulnerability (7.2 Code Security, 7.8 Operations).

**Recommendation:** Implement robust error handling for external calls. The `ok` boolean returned by `call` should be checked, and the transaction should not revert if the external call fails. Consider using a try/catch block around the external call to gracefully handle failures without blocking core token functionality. Ensure the `rewardTracker` is a trusted, audited contract that cannot revert on `ping`.


### `M-03` — Irreversible `rewardTracker` Address and Immutable Launcher Role  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `rewardTracker` address can only be set once by the `launcher` (`if (rewardTracker == address(0)) rewardTracker = tracker;`). If this address is set incorrectly, to a malicious contract, or if the legitimate tracker needs to be updated or replaced, it is impossible to change it. This creates a permanent single point of failure and limits operational flexibility. Furthermore, the `launcher` role itself is immutable, meaning if the `launcher` key is compromised or lost, the ability to set the `rewardTracker` (if not already set) or manage exemptions is permanently lost (7.3 Access Control, 7.8 Operations).

**Recommendation:** Implement a mechanism to allow the `rewardTracker` to be updated by a trusted entity (e.g., a multi-signature wallet or governance) after an appropriate timelock. Consider making the `launcher` role upgradeable or managed by a multi-sig to mitigate the risk of a single point of failure and enhance long-term security.


### `M-04` — Unchecked Return Value of External Call  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The external call to `rewardTracker.call{gas: 600_000}(...)` does not check the boolean `ok` return value. While the transaction will revert if the target contract reverts, if the target contract simply returns `false` without reverting, the `_update` function will proceed as if the call was successful. This can lead to unexpected or incorrect state in the `rewardTracker` or the overall protocol, as the success of the `ping` operation is not confirmed (7.2 Code Security, 7.6 External).

**Recommendation:** Always check the return value of low-level `call` functions. If the `ping` operation is critical, ensure `ok` is true and handle cases where it is false. If it's best-effort, consider logging the failure but not reverting the transaction (after addressing the critical DoS issue).


### `L-01` — Max Wallet Cap Inactive During Pre-Launch and for 100%+ Caps  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxWalletBps` cap is only enforced `if (launched)` and `if (maxWalletBps < BPS)`. This means during the initial phase before `finishLaunch()` is called, or if `maxWalletBps` is set to 100% (10,000 BPS) or higher, the wallet cap is not active. While this might be an intentional design choice for initial distribution, it allows for large accumulations before the cap becomes active (7.4 Economic).

**Recommendation:** Document the intended behavior of the `maxWalletBps` cap during the pre-launch phase and when set to 100% or more. Ensure that the project's whitepaper or documentation clearly explains these conditions to users to manage expectations.


### `I-01` — Hardcoded Exempt Addresses  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Several addresses are hardcoded as exempt from the max wallet cap in the constructor: `mintTo`, `poolManager`, `0x000000000000000000000000000000000000dEaD`, and `creator_`. While `mintTo` and `creator_` are parameters, `0x00...dEaD` is a literal. Hardcoding addresses can sometimes lead to issues if the purpose of that address changes or if it's a typo (7.1 Architecture).

**Recommendation:** Document the precise purpose of each hardcoded exempt address, especially `0x00...dEaD`. Ensure that the use of `0x00...dEaD` is intentionally for a burn address or similar and does not conflict with other protocol mechanics or future plans.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0f61...dfc9`](https://basescan.org/address/0x0f61edbfe6cd86024c0f210c0695b08df55fdfc9) |
| **Network** | Base |
| **Price** | $0.002609 |
| **24h Volume** | $537.4K |
| **Liquidity** | $141.6K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 13d |
| **Top-10 Holders** | 31.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1213 buys / 577 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xc9786476d2492eb8ddb2ebf8b4b69e227e1f31397c790d877541ab0ed5cf5ee2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/basestonk-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

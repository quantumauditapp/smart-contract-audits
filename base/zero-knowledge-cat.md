---
token: ZERO KNOWLEDGE CAT
ticker: ZKAT
network: base
risk_score: 24
status: low
date: 2026-09-14
---

# ZERO KNOWLEDGE CAT (ZKAT) — Smart Contract Security Analysis | Base

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zero-knowledge-cat-base)

---

## Audit Summary

The AdvancedLaunchToken contract is an ERC20 token with custom logic for a maximum wallet cap and an external reward tracker integration. The audit identified a High-severity issue related to centralized control by the 'launcher' address, which poses a significant single point of failure. Additionally, a Medium-severity finding was noted regarding unhandled external call reverts. The contract exhibits good code quality and standard ERC20 implementation, but key economic parameters are immutable, limiting future flexibility. Overall, the contract presents a Medium risk profile, primarily due to the centralized control and potential for operational issues if the 'launcher' key is compromised or external calls fail silently.

> **Final Recommendation:** It is highly recommended to implement robust security measures for the 'launcher' address, such as multi-signature control, to mitigate the risks associated with its centralized power. Consider adding explicit error handling for external calls to the reward tracker to ensure critical off-chain processes are not silently disrupted. For future iterations, evaluate the trade-offs of immutability for key economic parameters versus the flexibility to adapt to evolving market conditions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates good adherence to ERC20 standards by inheriting from OpenZeppelin's implementation (7.1 Architecture). The `_update` function correctly implements custom logic for a max… |
| **Governance / Economics** | 3/10 | High | The economic model includes a `maxWalletBps` to limit individual holdings, which is a positive feature for distribution (7.4 Economic). Key addresses like the `launcher` and `poolManager` are… |
| **Upgrades** | 6/10 | Medium | The `AdvancedLaunchToken` contract is not designed with an upgrade mechanism, such as a proxy pattern (7.7 Upgrades). This means that the contract's logic is immutable once deployed, providing… |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Unhandled External Call Revert in `_update`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_update` function makes an external call to `rewardTracker.ping` via `call{gas: 5_000_000}`. While the `ok` boolean is captured from the low-level call, it is not used to revert the transaction if the `ping` call fails. This 'fire-and-forget' approach means that if the `rewardTracker` is critical for certain off-chain or on-chain processes, its failure might go unnoticed, leading to inconsistencies or unexpected behavior in the broader ecosystem (7.2 Code Security, 7.6 External).

**Recommendation:** Consider explicitly checking the `ok` boolean and reverting the transaction if the `ping` call is expected to always succeed and its failure would indicate a critical issue. For example: `require(ok, 'RewardTracker ping failed');`. If the 'fire-and-forget' behavior is intentional, document this design choice clearly.


### `M-02` — Centralized Control by Launcher Address  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `launcher` address holds significant power over critical contract functions, including `setExempt`, `setRewardTracker`, and `finishLaunch`. A compromise of this single address could lead to unauthorized manipulation of the token's core mechanics, such as bypassing max wallet caps for specific addresses, setting a malicious reward tracker, or prematurely activating the 'launched' state. This creates a single point of failure for the protocol's operational security (7.3 Access Control, 7.8 Operations).

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `launcher` address to distribute control and require multiple approvals for critical operations. Alternatively, consider a time-locked mechanism for sensitive actions to provide a window for intervention if a compromise occurs.


### `L-01` — Immutability of Key Economic Parameters  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxWalletBps` parameter, which defines the maximum percentage of total supply an address can hold, is set in the constructor and declared as `immutable`. While immutability provides certainty and reduces governance complexity, it also means that this critical economic parameter cannot be adjusted after deployment. If the project needs to modify the maximum wallet cap due to changing market conditions, community feedback, or unforeseen circumstances, a new token contract would be required, necessitating a complex migration process (7.4 Economic).

**Recommendation:** Evaluate the long-term implications of an immutable `maxWalletBps`. If flexibility is desired, consider making this parameter configurable by a trusted role (e.g., `launcher` or a governance mechanism) with appropriate time-locks or multi-signature controls. If immutability is a core design principle, ensure this is clearly communicated to users.


### `I-01` — Extensive List of Exempted Addresses from Max Wallet Cap  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Several addresses, including the `launcher`, `poolManager`, `creator`, and the `0x...dEaD` address, are permanently exempted from the `maxWalletBps` cap in the constructor. While `0x...dEaD` is a burn address and `creator` has no special privileges, the `launcher` and `poolManager` are operational roles. These exemptions mean these entities can accumulate an unlimited supply of tokens, potentially creating large whale holdings that could contradict the spirit of a max wallet cap designed for broader distribution (7.4 Economic).

**Recommendation:** Ensure that the operational necessity for each exempted address to hold an unlimited supply is thoroughly justified and documented. Consider if any of these exemptions could be managed dynamically by the `launcher` via the `setExempt` function rather than being hardcoded, offering more flexibility if roles or operational needs change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6055...f222`](https://basescan.org/address/0x60555ab88a0caaf893ab284c1332c9d0a05af222) |
| **Network** | Base |
| **Price** | $0.000604 |
| **24h Volume** | $261.7K |
| **Liquidity** | $87.4K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 28.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 824 buys / 611 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x4768d50673a8920e634129ae569c2f4eb9345b1f660845e7b7730423f6997cb8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zero-knowledge-cat-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*

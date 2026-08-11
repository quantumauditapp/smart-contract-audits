---
token: Test
ticker: TST
network: bsc
risk_score: 27
status: medium
date: 2026-08-11
---

# Test (TST) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 27/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/test-bsc)

---

## Audit Summary

The audit of the Token contract, an ERC-20 compliant token with custom transfer restrictions, identified a High-severity issue related to the irreversible nature of its transfer mode. Once the token's transfer mode is set to 'NORMAL', it cannot be reverted to a restricted state, which significantly impacts the project's ability to manage token transfers post-launch. Other findings include centralized control and a missing event for mode changes.

> **Final Recommendation:** It is strongly recommended to review the `setMode` logic to ensure it aligns with the intended long-term operational strategy for token transferability. If flexibility is desired, the condition preventing mode changes from `MODE_NORMAL` should be removed or modified. Additionally, consider emitting an event when the transfer mode is changed to enhance transparency and on-chain monitoring. Ensure clear communication to users regarding the initial transfer restrictions and any subsequent mode changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract implements a standard ERC-20 token with OpenZeppelin's Ownable pattern. The core functionality is sound, utilizing `unchecked` blocks appropriately after boundary checks (7.2 Code… |
| **Governance / Economics** | 5/10 | Medium | The token's economic model is heavily influenced by the `_mode` variable, which dictates transferability (7.4 Economic). The contract relies on a single owner for critical operations, including… |
| **Upgrades** | 10/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no upgrade-specific risks or vulnerabilities to address. Any changes to the contract logic would require a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 97.0% — GoPlus SafeToken Locker |
| **Top-1 Unlocked Holder** | 2.8% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Irreversible Transfer Mode Change  *(Severity: High · Status: Unresolved)*

The `setMode` function contains a condition `if (_mode != MODE_NORMAL) { _mode = v; }`. This logic dictates that once the token's transfer mode (`_mode`) is set to `MODE_NORMAL` (0), it can never be changed again. This means that any transfer restrictions (e.g., `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`) cannot be re-enabled after the token has been set to fully transferable. This significantly limits the project's ability to adapt to future needs, such as implementing vesting schedules, preventing market manipulation, or responding to security incidents by temporarily restricting transfers.

**Recommendation:** If the intention is to allow flexible control over transfer restrictions, remove the `if (_mode != MODE_NORMAL)` condition from the `setMode` function. This would allow the owner to switch between all defined modes as needed. If the irreversible nature is intentional, ensure this design choice is clearly documented and understood by all stakeholders, acknowledging the permanent loss of control once `MODE_NORMAL` is activated.


### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract utilizes the `Ownable` pattern, granting the deployer (owner) exclusive control over critical functions such as `setMode` and initial token minting. While common, this centralization introduces a single point of failure. A compromised owner key could lead to unauthorized changes in transferability or other malicious actions, impacting the token's integrity and user trust.

**Recommendation:** Consider implementing a multi-signature wallet for ownership of critical functions to distribute control and reduce the risk associated with a single compromised key. For future iterations, explore decentralized governance mechanisms if the project aims for community-driven control over such parameters.


### `L-01` — Initial Transfer Restriction Requires Owner Action  *(Severity: Low · Status: Unresolved)*

In the constructor, the `_mode` is initialized to `MODE_TRANSFER_RESTRICTED`. This means that immediately after deployment, no token transfers are possible until the owner explicitly calls `setMode` to change it to `MODE_NORMAL` or `MODE_TRANSFER_CONTROLLED`. While this might be an intentional design choice for a controlled launch, it could lead to user confusion or operational delays if not clearly communicated and managed.

**Recommendation:** Ensure that the initial transfer restriction is clearly communicated to users and the community. Provide clear instructions and a timeline for when the owner intends to change the mode to enable transfers. Consider emitting an event in the constructor to explicitly state the initial mode.


### `I-01` — Missing Event for Mode Change  *(Severity: Informational · Status: Unresolved)*

The `setMode` function, which modifies the critical `_mode` state variable controlling token transferability, does not emit an event. Without an event, it is difficult for off-chain applications, block explorers, and users to track changes to the token's transfer status programmatically or to verify when and by whom the mode was changed.

**Recommendation:** Add an event to the `setMode` function to log the old and new mode values. For example: `event ModeChanged(uint256 oldMode, uint256 newMode);` and emit it after `_mode` is updated.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x86bb...6429`](https://bscscan.com/address/0x86bb94ddd16efc8bc58e6b056e8df71d9e666429) |
| **Network** | BNB Chain |
| **Price** | $0.01563 |
| **24h Volume** | $883.8K |
| **Liquidity** | $769.0K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 85.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2799 buys / 2920 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x16969fa79651bae11736f2f6576a86fe2726b42b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/test-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*

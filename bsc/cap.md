---
token: Cap
ticker: CAP
network: bsc
risk_score: 59
status: high
date: 2026-07-23
---

# Cap (CAP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 59/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cap-bsc)

---

## Audit Summary

The L2TokenUpgradeable contract implements an ERC-20 token with LayerZero Omnichain Fungible Token (OFT) capabilities and UUPS upgradeability. It leverages standard OpenZeppelin and LayerZero upgradeable patterns. The owner, a Timelock, holds significant administrative power, including upgrades and LayerZero configurations. The audit identified a high-level concern regarding centralized control, a medium-level concern regarding external dependencies, and minor informational findings.

> **Final Recommendation:** It is recommended to maintain robust operational security practices around the Timelock owner address, including secure key management and multi-signature requirements. Continuous monitoring of LayerZero endpoint configurations and cross-chain message flows is advisable to detect any anomalies. For future enhancements, consider implementing events for all critical state changes, such as `setDelegate`, to improve transparency and off-chain monitoring capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract utilizes well-audited OpenZeppelin and LayerZero upgradeable libraries, providing a robust foundation for ERC-20, permit, and cross-chain functionalities (7.1 Architecture, 7.2 Code… |
| **Governance / Economics** | 3/10 | High | The contract employs an `Ownable` access control pattern where a single address, identified as a Timelock, holds all administrative privileges (7.3 Access Control). This owner can manage LayerZero… |
| **Upgrades** | 7/10 | Low | The contract implements the UUPS upgradeability pattern, allowing for future logic updates (7.7 Upgrades). The `_authorizeUpgrade` function is correctly restricted to the `onlyOwner` modifier… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `owner` address, set during initialization, holds significant administrative control over the contract. This includes the ability to authorize upgrades (`_authorizeUpgrade`), set LayerZero peers (`setPeer`), and set the LayerZero delegate (`setDelegate`). While the owner is identified as a Timelock, which mitigates immediate malicious actions by introducing a delay, this still represents a single point of administrative decision-making and control. A compromise of the Timelock's governance mechanism could lead to unauthorized upgrades or manipulation of cross-chain functionality.

**Recommendation:** Ensure the Timelock governance mechanism is robust, well-tested, and follows best practices for decentralized decision-making. Implement strict access controls and multi-signature requirements for any actions that can modify the Timelock's configuration or execute proposals. Regularly audit the Timelock contract itself for vulnerabilities.


### `M-01` — Dependency on LayerZero Protocol Security  *(Severity: Medium · Status: Unresolved)*

The contract's core functionality, particularly its cross-chain transfer capabilities as an Omnichain Fungible Token (OFT), is entirely dependent on the security, liveness, and correct operation of the LayerZero protocol and its endpoint. Any vulnerabilities, compromises, or operational failures within the LayerZero network or its endpoint contracts could directly impact the integrity, availability, and security of the L2TokenUpgradeable's cross-chain operations, potentially leading to loss of funds or service disruption.

**Recommendation:** Acknowledge and monitor the inherent risks associated with external protocol dependencies. Implement robust monitoring for LayerZero endpoint health, message delivery, and any security announcements from the LayerZero team. Consider contingency plans for extreme scenarios involving LayerZero disruptions, if feasible.


### `L-01` — Hardcoded LayerZero Storage Slot  *(Severity: Low · Status: Unresolved)*

The `OAppCoreUpgradeable` contract uses a hardcoded storage slot (`OAPP_CORE_STORAGE_LOCATION`) for its `peers` mapping. While this is a common and often necessary pattern in upgradeable contracts to ensure consistent storage layout across upgrades and complex inheritance hierarchies, incorrect calculation or accidental collision with other storage variables (especially in contracts with multiple inheritance paths) could lead to critical state corruption or unexpected behavior. Assuming LayerZero's calculation is robust, the risk is low.

**Recommendation:** Verify that the hardcoded storage slot calculation is unique and does not conflict with any other storage variables in the inheritance chain of `L2TokenUpgradeable`. While this is typically handled by library developers, a thorough understanding of the storage layout is crucial for upgradeable contracts.


### `I-01` — Missing Event for `setDelegate` Function  *(Severity: Informational · Status: Unresolved)*

The `setDelegate` function in `OAppCoreUpgradeable` allows the owner to change the delegate address on the LayerZero endpoint. However, this function does not emit an event upon successful execution. The absence of an event makes it challenging for off-chain systems, such as block explorers, monitoring tools, or user interfaces, to track changes to the delegate address, potentially hindering transparency and auditability.

**Recommendation:** Consider adding an event, such as `DelegateSet(address indexed oldDelegate, address indexed newDelegate)`, to the `setDelegate` function. Emitting events for critical state changes enhances transparency, allows for easier off-chain monitoring, and improves the overall auditability of the contract's administrative actions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9999...9999`](https://bscscan.com/address/0x99991c6aabba5a096f24f250b73580f5179b9999) |
| **Network** | BNB Chain |
| **Price** | $0.02283 |
| **24h Volume** | $55.5K |
| **Liquidity** | $22.9K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 26d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 786 buys / 797 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x1f87f6a5ae82c4fa00b41f1e6e1afaa4e69ea228)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cap-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*

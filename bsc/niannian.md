---
token: NianNian
ticker: NIANNIAN
network: bsc
risk_score: 0
status: low
date: 2026-08-31
---

# NianNian (NIANNIAN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/niannian-bsc)

---

## Audit Summary

The audit of the Token contract identified a critical design flaw related to the irreversible loss of transfer control, where the owner cannot re-enable transfer restrictions once the token is set to `MODE_NORMAL`. Additionally, the contract exhibits a high degree of centralization in transfer control and requires immediate owner action post-deployment to enable transfers. The core ERC20 implementation is robust, leveraging standard OpenZeppelin patterns.

> **Final Recommendation:** It is strongly recommended to address the critical issue regarding the irreversible loss of transfer control. The `setMode` function should be modified to allow the owner to transition between all defined modes as needed, providing necessary operational flexibility. Consider whether the high degree of centralization in transfer control aligns with the project's long-term decentralization goals and communicate these limitations clearly to users. Ensure the owner is prepared to execute the initial `setMode` transaction promptly after deployment to enable token transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements a standard ERC20 token with custom transfer logic. It correctly uses OpenZeppelin's `Ownable` pattern for access control and `unchecked` blocks for arithmetic operations where… |
| **Governance / Economics** | 10/10 | Low | The token's economic model is highly centralized, with the owner having significant control over transferability through the `_mode` mechanism (7.4 Economic). The `MODE_TRANSFER_CONTROLLED` state… |
| **Upgrades** | 10/10 | Low | The contract is not designed with an upgradeability pattern (7.7 Upgrades). This means its logic cannot be modified or updated after deployment. Any changes or bug fixes would require a new contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — GoPlus SafeToken Locker |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Highly Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_mode` mechanism, specifically `MODE_TRANSFER_CONTROLLED`, allows only transfers where either the `from` or `to` address is the contract owner. This design choice makes the token highly centralized, as general users cannot freely transfer tokens among themselves. This significantly limits the token's utility, liquidity, and decentralization, concentrating power and control in the hands of the owner.

**Recommendation:** Evaluate if such a high degree of centralization aligns with the project's long-term vision. If a more decentralized model is desired, consider removing or modifying the `MODE_TRANSFER_CONTROLLED` state to allow broader transferability. Clearly communicate these transfer restrictions to all potential users and investors.


### `M-02` — Irreversible Loss of Transfer Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setMode` function contains a condition `if (_mode != MODE_NORMAL)` which prevents the owner from ever re-enabling transfer restrictions once the token's mode has been set to `MODE_NORMAL`. This means that if the owner transitions the token to `MODE_NORMAL` (fully unrestricted transfers), they permanently lose the ability to revert to `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`. This removes a core control mechanism designed into the contract, potentially hindering the project's ability to respond to unforeseen security incidents or market manipulations by re-imposing restrictions.

**Recommendation:** Modify the `setMode` function to allow the owner to transition between all defined modes (`MODE_NORMAL`, `MODE_TRANSFER_RESTRICTED`, `MODE_TRANSFER_CONTROLLED`) without permanent restrictions. For example, remove the `if (_mode != MODE_NORMAL)` condition to allow `_mode` to be set to any valid value at any time by the owner.


### `L-01` — Initial Transfer Restriction Requires Owner Action  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The token contract is initialized in `MODE_TRANSFER_RESTRICTED` in its constructor. This means that immediately after deployment, no token transfers are possible until the contract owner explicitly calls the `setMode` function to change it to `MODE_NORMAL` or `MODE_TRANSFER_CONTROLLED`. This introduces an operational dependency on the owner to perform an additional transaction post-deployment to enable basic token functionality.

**Recommendation:** Ensure that the contract owner is aware of this initial state and is prepared to execute the `setMode` transaction promptly after deployment if immediate transferability is desired. Alternatively, consider initializing the token in `MODE_NORMAL` if unrestricted transfers are the default intended behavior.


### `I-01` — Standard `unchecked` Usage for Arithmetic Operations  *(Severity: Informational · Status: Resolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes `unchecked` blocks for arithmetic operations such as `_balances[from] = fromBalance - amount;` and `_balances[to] += amount;`. These operations are preceded by `require` statements that ensure conditions like `fromBalance >= amount` are met, effectively preventing underflow. For additions, overflow is practically not an issue with `uint256` for typical token supplies. This is a standard and secure pattern in modern Solidity to optimize gas costs while maintaining safety.

**Recommendation:** No action required. This is a secure and gas-efficient practice.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9c27...c096`](https://bscscan.com/address/0x9c27c4072738cf4b7b0b7071af0ad5666bddc096) |
| **Network** | BNB Chain |
| **Price** | $0.0007034 |
| **24h Volume** | $50.4K |
| **Liquidity** | $97.9K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 28.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 132 buys / 99 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x72715ea48f381c417f2ab3ffe7c092033a077827)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/niannian-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*

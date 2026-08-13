---
token: Bedrock
ticker: BR
network: bsc
risk_score: 77
status: critical
date: 2026-08-13
---

# Bedrock (BR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 77/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bedrock-bsc)

---

## Audit Summary

The Bedrock token contract implements ERC20 with burnable functionality and robust access control. It features a centralized minting capability and a unique freezing mechanism allowing administrators to restrict user transfers to a designated recipient. While the code is well-structured, the extensive administrative powers introduce significant centralization risks, particularly concerning potential censorship or fund seizure.

> **Final Recommendation:** It is strongly recommended to implement multi-signature wallets for all critical roles, especially the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, and `FREEZER_ROLE`, to mitigate single points of failure and enhance security. Consider adding a time-lock mechanism for highly sensitive administrative actions, such as changing the `freezeToRecipient` or granting/revoking critical roles, to provide a window for community review and intervention. Additionally, clearly communicate the extent of centralized control and the implications of the freezing mechanism to all users to ensure transparency and informed participation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract leverages OpenZeppelin's battle-tested ERC20Burnable and AccessControl libraries, enhancing code security and adherence to established standards (7.2 Code Security). The implementation… |
| **Governance / Economics** | 1/10 | High | The protocol employs a robust `AccessControl` system to manage roles for minting and freezing, ensuring only authorized entities can perform these actions (7.3 Access Control). However, the… |
| **Upgrades** | 2/10 | High | The Bedrock contract is not designed as an upgradeable proxy, which simplifies its architecture by avoiding upgrade-specific complexities and potential vulnerabilities (7.7 Upgrades). This design… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.8% |
| **Top-3 Unlocked** | ⚠️ 99.6% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Centralized Control and Potential for Censorship/Seizure  *(Severity: Critical · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` and `FREEZER_ROLE` possess extensive power, including the ability to freeze user accounts and dictate that frozen funds can only be transferred to a specific `freezeToRecipient` address. This introduces a high degree of centralization and potential for censorship or even seizure of funds if the `freezeToRecipient` is maliciously controlled or if the role holders act maliciously. (7.3 Access Control, 7.4 Economic, 7.5 Governance)

**Recommendation:** Implement multi-signature control for critical roles, especially `DEFAULT_ADMIN_ROLE` and `FREEZER_ROLE`. Consider a time-lock for sensitive operations like changing `freezeToRecipient`. Clearly communicate these powers and their implications to all users.


### `H-01` — Unlimited Minting Capability  *(Severity: High · Status: Unresolved)*

The `MINTER_ROLE` has the ability to mint an arbitrary amount of new tokens via the `mint` function. While this might be an intended feature for token supply management, it poses a significant economic risk as uncontrolled or malicious minting can lead to hyperinflation and devaluation of the token. (7.4 Economic)

**Recommendation:** Implement a minting cap, a rate limit, or a multi-signature approval process for minting operations. Ensure the `MINTER_ROLE` is managed with the highest security standards, ideally by a multi-signature wallet or a robust governance mechanism.


### `M-01` — Gas Limit Concerns for Batch Operations  *(Severity: Medium · Status: Unresolved)*

The `batchTransfer`, `freezeUsers`, and `unfreezeUsers` functions iterate through arrays of recipients or users. If these arrays contain a very large number of elements, the transaction might exceed the block gas limit, causing the operation to fail. This can lead to denial of service for legitimate batch operations. (7.2 Code Security, 7.8 Operations)

**Recommendation:** Implement a maximum array size limit for these batch functions to prevent transactions from exceeding the block gas limit. Alternatively, provide alternative mechanisms for very large operations, such as pagination or Merkle tree-based claims, if such scale is anticipated.


### `L-01` — Single Point of Failure for Critical Roles  *(Severity: Low · Status: Unresolved)*

The constructor initially grants `DEFAULT_ADMIN_ROLE` and `FREEZER_ROLE` to a single `defaultAdmin` address. If this single address is compromised, an attacker gains full control over administrative functions, including minting, freezing, and role management, creating a single point of failure for the protocol's security. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Transfer `DEFAULT_ADMIN_ROLE` to a multi-signature wallet immediately after deployment. Ensure robust security practices (e.g., hardware wallets, strong authentication) for all addresses holding critical roles.


### `I-01` — Lack of Event Emission for `setFreezeToRecipient`  *(Severity: Informational · Status: Unresolved)*

The `setFreezeToRecipient` function allows the `DEFAULT_ADMIN_ROLE` to change the critical `freezeToRecipient` address. However, this function does not emit an event upon successful execution. This lack of an event makes it difficult to track changes to this address on-chain, impacting transparency and off-chain monitoring for users and auditors. (7.2 Code Security, 7.8 Operations)

**Recommendation:** Emit an event, such as `FreezeToRecipientChanged(address indexed oldRecipient, address indexed newRecipient)`, whenever `freezeToRecipient` is updated. This enhances transparency and allows for easier monitoring of critical parameter changes.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xff7d...6b41`](https://bscscan.com/address/0xff7d6a96ae471bbcd7713af9cb1feeb16cf56b41) |
| **Network** | BNB Chain |
| **Price** | $0.2303 |
| **24h Volume** | $1.59M |
| **Liquidity** | $1.23M |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 84.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3513 buys / 2652 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe2461367e562df374acf8d8a012729721ad5b486)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bedrock-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*

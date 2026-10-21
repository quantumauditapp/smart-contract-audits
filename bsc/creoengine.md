---
token: CreoEngine
ticker: CREO
network: bsc
risk_score: 67
status: high
date: 2026-09-12
---

# CreoEngine (CREO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/creoengine-bsc)

---

## Audit Summary

The CreoEngine BEP20 token implements standard token functionalities along with custom anti-sniper and anti-whale mechanisms. The contract uses SafeMath for arithmetic safety and Ownable for access control, with the owner being a 2/3 multisig. A critical design flaw in the anti-sniper mechanism could lead to legitimate users being unable to transfer their tokens, posing a significant risk to user funds.

> **Final Recommendation:** Prioritize a review and redesign of the anti-sniper mechanism to prevent the lockout of legitimate user funds. Implement a clear process for managing critical parameters like `tradingOpen` and `maxTxAmount`, potentially incorporating a timelock to enhance transparency and provide users with notice. Ensure all administrative actions emit events for improved auditability and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages SafeMath for arithmetic safety (7.2 Code Security) and adheres to the BEP20 standard. A custom anti-sniper mechanism is implemented, intended to prevent early trading… |
| **Governance / Economics** | 3/10 | High | The contract employs an Ownable pattern with a 2/3 multisig owner, enhancing access control (7.3 Access Control) compared to a single owner. The owner has significant control over 'tradingOpen'… |
| **Upgrades** | 6/10 | Medium | The CreoEngine contract is not designed with an upgrade mechanism (7.7 Upgrades). Any future modifications to the token logic would necessitate deploying a new contract and migrating existing token… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Flawed Anti-Sniper Mechanism Leading to Legitimate User Lockout  *(Severity: High · Status: Unresolved)*

The `_transfer` function marks the `recipient` as a sniper if a transfer occurs within `deadBlocks` after `launchedAt`. This logic means any user receiving tokens during this initial period, even legitimate buyers or users receiving tokens from the owner, will be permanently marked as a sniper. Once marked, these addresses are unable to transfer their tokens, effectively locking their funds indefinitely. This design flaw can lead to significant financial loss for innocent users.

**Recommendation:** Re-evaluate the anti-sniper logic. Consider alternative mechanisms that do not permanently lock legitimate users' funds. If a temporary restriction is desired, ensure there is a clear and automatic expiration or an owner-controlled mechanism to remove sniper status for legitimate users. For example, restrict transfers only for a specific duration or implement a whitelist for initial liquidity providers/buyers.


### `M-01` — Centralized Control Over Critical Parameters  *(Severity: Medium · Status: Unresolved)*

The `owner` (a 2/3 multisig) has extensive control over core contract functionalities, including `openTrading`, `maxTxAmount`, and the `_isSniper` list. While the multisig mitigates a single-point-of-failure, this level of control can significantly impact token tradability, user experience, and the overall economic model. For instance, the owner can unilaterally pause trading or restrict transaction amounts at will, affecting all token holders.

**Recommendation:** Consider implementing a timelock for critical parameter changes (e.g., `openTrading`, `maxTxAmount`) to provide transparency and allow users to react to impending changes. As the project matures, explore options for progressive decentralization or community governance over these parameters.


### `M-02` — Potential for Denial of Service via `tradingOpen` and `maxTxAmount`  *(Severity: Medium · Status: Unresolved)*

The owner can unilaterally set `tradingOpen` to `false`, effectively pausing all non-owner transfers. Additionally, the `maxTxAmount` can be set to a very low value, severely restricting trading for non-exempt addresses. While these features might be intended for emergency situations or launch control, they present a significant centralization risk and potential for denial of service for token holders, hindering liquidity and market operations.

**Recommendation:** Clearly define and communicate the circumstances under which `tradingOpen` would be toggled or `maxTxAmount` would be adjusted. Implement a timelock for changes to these critical variables to provide transparency and allow users to react. Consider adding a minimum threshold for `maxTxAmount` to prevent it from being set to an arbitrarily low value.


### `L-01` — Lack of Event Emission for Critical Administrative Actions  *(Severity: Low · Status: Unresolved)*

The provided code snippet shows `setMaxTxAmount` (truncated) and implies management of `_isMaxWalletExempt`. It is crucial that all state-changing administrative actions, especially those affecting core token mechanics like `maxTxAmount` or user exemptions, emit corresponding events. Without events, off-chain monitoring and transparency for users regarding these critical changes are significantly hampered.

**Recommendation:** Ensure all administrative functions that modify critical state variables (e.g., `maxTxAmount`, `_isMaxWalletExempt` status) emit corresponding events. This improves auditability, allows for off-chain tracking, and enhances transparency for the community.


### `I-01` — Old Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with Solidity version `0.5.12`. While `SafeMath` is used to mitigate integer overflow/underflow, newer compiler versions (e.g., 0.8.x) include built-in overflow/underflow checks by default, reducing reliance on external libraries and potentially improving gas efficiency. Newer versions also offer various language improvements and bug fixes.

**Recommendation:** Consider upgrading to a more recent Solidity compiler version (e.g., 0.8.x) for future deployments. This would allow for the removal of `SafeMath` (as arithmetic operations would revert on overflow/underflow by default) and leverage other compiler optimizations and security features.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9521...1eb7`](https://bscscan.com/address/0x9521728bf66a867bc65a93ece4a543d817871eb7) |
| **Network** | BNB Chain |
| **Price** | $0.002354 |
| **24h Volume** | $88.5K |
| **Liquidity** | $57.7K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 2y |
| **Top-10 Holders** | 58.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 760 buys / 691 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xf69760e797a7ccb8dde867ced92c32ee92b9e78b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/creoengine-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*

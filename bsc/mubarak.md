---
token: mubarak
ticker: MUBARAK
network: bsc
risk_score: 25
status: medium
date: 2026-08-11
---

# mubarak (MUBARAK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 25/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mubarak-bsc)

---

## Audit Summary

This audit covers a custom ERC20 token contract with added transfer control mechanisms. The contract implements standard ERC20 functionalities and introduces a `_mode` variable to restrict transfers. Key findings include an irreversible state change in the transfer mode mechanism and significant centralization of control over token transfers by the owner.

> **Final Recommendation:** It is strongly recommended to review the design of the `setMode` function, specifically the irreversible transition to `MODE_NORMAL`. If the intention is to retain the ability to restrict transfers in the future, this logic must be revised. Additionally, consider the implications of centralized control over token transfers and whether a multi-signature wallet or a time-locked governance mechanism could be introduced for critical functions like `setMode` to enhance security and decentralization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes standard OpenZeppelin patterns for ERC20 and Ownable functionalities, demonstrating a solid foundation (7.1 Architecture, 7.2 Code Security). The use of `unchecked` blocks is… |
| **Governance / Economics** | 5/10 | Medium | The token's economic model is heavily reliant on the owner's control over transferability (7.4 Economic). The `setMode` function allows the owner to permanently disable transfer restrictions by… |
| **Upgrades** | 10/10 | Low | The contract is not designed with upgradeability in mind (7.7 Upgrades). It is a standard implementation contract without proxy patterns. Therefore, any identified issues or desired feature changes… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 65.8% — GoPlus SafeToken Locker |
| **Top-1 Unlocked Holder** | 29.0% |
| **Top-3 Unlocked** | 34.1% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `H-01` — Irreversible Transfer Mode Change  *(Severity: High · Status: Unresolved)*

The `setMode` function contains a condition `if (_mode != MODE_NORMAL) { _mode = v; }`. This logic prevents the owner from changing the transfer mode once it has been set to `MODE_NORMAL`. If the owner ever sets the token to `MODE_NORMAL`, they permanently lose the ability to re-enable `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`, even in emergency situations. This represents an irreversible loss of a critical control mechanism (7.3 Access Control, 7.4 Economic).

**Recommendation:** Remove the `if (_mode != MODE_NORMAL)` condition from the `setMode` function if the intention is for the owner to always retain full control over the transfer mode. Alternatively, if the irreversible transition is intended, ensure this design choice is clearly documented and understood by all stakeholders, acknowledging the permanent loss of control.


### `M-01` — Centralized Control over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The `owner()` address has complete control over the token's transferability through the `setMode` function and the `_beforeTokenTransfer` hook. The owner can pause all transfers (`MODE_TRANSFER_RESTRICTED`) or restrict them to only involve the owner (`MODE_TRANSFER_CONTROLLED`). This introduces a single point of failure, as a compromised owner key could lead to censorship or manipulation of token transfers (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` role or introducing a time-lock mechanism for critical functions like `setMode`. This would distribute control and provide a delay for users to react to potentially malicious actions, enhancing security and decentralization.


### `L-01` — Initial Restricted Transfer State  *(Severity: Low · Status: Unresolved)*

Upon deployment, the token's `_mode` is initialized to `MODE_TRANSFER_RESTRICTED`. This means that immediately after deployment, no transfers of the token are possible until the owner explicitly calls `setMode` to change it to `MODE_NORMAL` or `MODE_TRANSFER_CONTROLLED`. This requires an immediate operational step from the owner for the token to become functional for general use (7.8 Operations).

**Recommendation:** Ensure that the operational team is aware of this initial state and has a clear plan for calling `setMode` to the desired initial operational mode shortly after deployment. Document this step in the deployment checklist.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5c85...46f6`](https://bscscan.com/address/0x5c85d6c6825ab4032337f11ee92a72df936b46f6) |
| **Network** | BNB Chain |
| **Price** | $0.01795 |
| **24h Volume** | $7.37M |
| **Liquidity** | $1.55M |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 84.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10198 buys / 9208 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x90a54475d512b8f3852351611c38fad30a513491)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mubarak-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*

---
token: Bnb Tiger Inu
ticker: BNBTIGER
network: bsc
risk_score: 32
status: low
date: 2026-09-04
---

# Bnb Tiger Inu (BNBTIGER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 32/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnb-tiger-inu-bsc)

---

## Audit Summary

This audit covers the provided Solidity code snippets, primarily focusing on the `Ownable` contract and common libraries. The core token contract implementation (BNBTiger) was not provided, limiting the scope of the analysis to general patterns and the `Ownable` logic. Key findings include potential denial of service due to the `lock` mechanism in `Ownable` and a single point of failure for regaining ownership.

> **Final Recommendation:** It is recommended to carefully review the `Ownable` contract's `lock` and `unlock` mechanisms. Consider implementing a multi-signature wallet for ownership to mitigate the single point of failure risk. Ensure that all critical administrative functions are designed to either operate autonomously during a lock period or have a robust, multi-party recovery mechanism. Additionally, clarify or remove the misleading error message in the `unlock` function.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture leverages standard libraries like SafeMath and Address, which enhance code security by preventing common integer vulnerabilities. The `Ownable` contract implements a `lock`… |
| **Governance / Economics** | 3/10 | High | The governance model, as defined by the `Ownable` contract, is highly centralized, with a single owner controlling all administrative functions. The `lock` mechanism, while intended to temporarily… |
| **Upgrades** | 7/10 | Low | The provided contract is not designed with an upgrade mechanism (7.7 Upgrades), meaning its logic cannot be modified after deployment. This eliminates upgrade-related risks such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `H-01` — Denial of Service via Ownable.lock()  *(Severity: High · Status: Unresolved)*

The `lock()` function in the `Ownable` contract sets the `_owner` to `address(0)` for a specified duration. During this period, any function protected by the `onlyOwner` modifier will be inaccessible. If critical administrative functions (e.g., pausing transfers, adjusting fees, emergency withdrawals) rely on `onlyOwner` permissions, the protocol could experience a denial of service, preventing essential operations or responses to emergencies.

**Recommendation:** Assess all owner-restricted functions in the main contract. If any are critical for ongoing operations or emergency responses, consider alternative access control mechanisms (e.g., time-locked multi-signature, governance vote) that remain functional during the lock period, or ensure the lock period is only applied when no critical owner actions are anticipated.


### `M-01` — Single Point of Failure for Ownership Recovery  *(Severity: Medium · Status: Unresolved)*

The `unlock()` function, which restores ownership after a `lock()` period, can only be called by the `_previousOwner` address. This creates a single point of failure. If the `_previousOwner` address is compromised, lost, or becomes inaccessible (e.g., if it's a contract that cannot initiate the call), the contract could remain permanently locked, or ownership could be transferred to an unauthorized entity after the lock period expires.

**Recommendation:** Implement a more robust ownership recovery mechanism. Consider using a multi-signature wallet for the `_previousOwner` or a time-locked recovery process that allows a community or a set of trusted parties to regain control, rather than relying on a single address.


### `L-01` — Misleading Error Message in unlock()  *(Severity: Low · Status: Unresolved)*

The `unlock()` function includes a revert message `"Contract is locked until 7 days"`. However, the actual lock duration (`_lockTime`) is dynamically set by the `time` parameter passed to the `lock()` function, not a fixed 7 days. This hardcoded message can be misleading to users regarding the actual remaining lock period.

**Recommendation:** Update the error message to accurately reflect the dynamic nature of the lock time. For example, remove the specific '7 days' reference or dynamically include the actual unlock timestamp in the error message.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xac68...dc2d`](https://bscscan.com/address/0xac68931b666e086e9de380cfdb0fb5704a35dc2d) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $32.3K |
| **Liquidity** | $1.16M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 69.3% of supply |
| **Buy / Sell Tax** | 9.0% / 9.0% |
| **24h Transactions** | 249 buys / 102 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5e1aab9d49f6c7122df7de4d6dbd5b03c1ebb0b7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnb-tiger-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*

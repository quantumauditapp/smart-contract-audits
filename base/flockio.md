---
token: FLock.io
ticker: FLOCK
network: base
risk_score: 84
status: critical
date: 2026-08-13
---

# FLock.io (FLOCK) — Smart Contract Security Analysis | Base

> **Risk Score: 84/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flockio-base)

---

## Audit Summary

The FlockTokenUpgradeable contract implements an ERC20 token with upgradeability, administrative controls for minting, burning, and blacklisting. While it leverages OpenZeppelin's secure upgradeable patterns and access control, a critical vulnerability exists where the intended daily mint limit is not enforced, allowing for uncontrolled token inflation by the administrator. High centralization of power also presents a significant risk.

> **Final Recommendation:** Prioritize fixing the critical bug where `dailyMintLimit` is not enforced in the `mint` function to prevent unintended token inflation. Implement the daily minting logic using the `lastMintedDay` and `amountMintedToday` variables. Strengthen access control by ensuring the `DEFAULT_ADMIN_ROLE` is managed by a robust multisignature wallet, similar to the proxy admin, to mitigate the risks associated with high centralization and potential misuse of powerful administrative functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract utilizes OpenZeppelin's upgradeable standards for ERC20 and AccessControl, enhancing code security (7.2). However, a critical vulnerability exists where the `dailyMintLimit` is declared… |
| **Governance / Economics** | 1/10 | High | The token's economic model is highly centralized, with an `onlyAdmin` role controlling all minting, burning, blacklisting, and critical parameter adjustments (7.4, 7.5). While this offers… |
| **Upgrades** | 2/10 | High | The contract employs the Transparent Upgradeable Proxy pattern with OpenZeppelin's upgradeable contracts, ensuring a robust and secure upgrade mechanism (7.7). The proxy's admin is managed by a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 82.8% |
| **Top-3 Unlocked** | ⚠️ 94.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Unenforced Daily Mint Limit  *(Severity: Critical · Status: Unresolved)*

The `dailyMintLimit` state variable is declared and can be set by the admin, but it is never used or enforced within the `mint` function. The `mint` function only checks against `maxTotalSupply`. This means that the administrator can mint any amount up to the `maxTotalSupply` in a single transaction, completely bypassing the intended daily limit mechanism. This poses a severe economic risk, as the token supply can be rapidly inflated beyond the protocol's stated daily constraints.

**Recommendation:** Implement the daily minting logic within the `mint` function. This should involve checking `lastMintedDay` and `amountMintedToday` against the `dailyMintLimit` to ensure that the total amount minted within a 24-hour period does not exceed the set limit. The `lastMintedDay` and `amountMintedToday` variables should be updated accordingly after each mint operation.


### `H-01` — High Centralization of Power  *(Severity: High · Status: Unresolved)*

The `onlyAdmin` role has extensive control over critical functions, including `mint`, `burnNetworkFees`, `addBatchToBlacklist`, `removeBatchFromBlacklist`, `setDailyMintLimit`, `addAdmin`, and `transferERC20`. This grants significant power to a single entity (or a small group if the admin role is a multisig) over the token's supply, transferability, and contract funds. The initial admin is set to `msg.sender` of the `initialize` function, which could be a single EOA, creating a single point of failure.

**Recommendation:** It is highly recommended that the `DEFAULT_ADMIN_ROLE` for the token contract be managed by a robust multisignature wallet with a sufficient threshold. This would distribute control, reduce the risk of a single point of failure, and require consensus for critical operations, enhancing the overall security and trust in the protocol.


### `M-01` — Admin Can Transfer Arbitrary ERC20 Tokens  *(Severity: Medium · Status: Unresolved)*

The `transferERC20` function allows the `onlyAdmin` role to transfer any ERC20 token from the contract's balance to any specified address. While restricted to the admin, this function could be misused if other ERC20 tokens are accidentally sent to the contract, or if the admin's private key is compromised. This effectively acts as a powerful backdoor for draining unintended assets from the contract.

**Recommendation:** Consider if the ability to transfer arbitrary ERC20 tokens is strictly necessary. If so, ensure robust operational procedures and multisig control for its execution. If not, remove or restrict this function to only allow transfers of the native token or specific whitelisted tokens. Alternatively, implement a time-locked withdrawal mechanism for non-native tokens to provide a window for users to react to suspicious activity.


### `L-01` — Blacklist Mechanism Limitations  *(Severity: Low · Status: Unresolved)*

The `notBlacklisted` modifier is applied to `transfer` and `transferFrom`, preventing blacklisted accounts from initiating token transfers. However, blacklisted accounts can still *receive* tokens. While this behavior might be intended (e.g., to allow funds to be sent to a blacklisted address for recovery), it could lead to confusion or unexpected scenarios regarding the full scope of the blacklist's impact.

**Recommendation:** Clearly document the intended behavior of the blacklist, specifically clarifying that blacklisted accounts can receive but not send tokens. If the intention was to prevent all interactions, consider adding checks on the recipient address as well, though this is less common for ERC20 blacklists.


### `I-01` — Unused `lastMintedDay` and `amountMintedToday` Variables  *(Severity: Informational · Status: Unresolved)*

The contract declares `lastMintedDay` and `amountMintedToday` mappings, which are typically used to implement daily minting limits. However, these variables are not used anywhere in the provided code. This indicates either an incomplete feature implementation or dead code, further highlighting the issue of the unenforced `dailyMintLimit` (C-01).

**Recommendation:** Either implement the intended daily minting logic using these variables in conjunction with `dailyMintLimit`, or remove them if the feature is no longer planned. Removing unused variables can slightly reduce contract size and improve clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5ab3...b691`](https://basescan.org/address/0x5ab3d4c385b400f3abb49e80de2faf6a88a7b691) |
| **Network** | Base |
| **Price** | $0.03008 |
| **24h Volume** | $415.8K |
| **Liquidity** | $154.2K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 70.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1089 buys / 1290 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xd7338b6f338da54b922bbbc6fbe3efedd5ce35fa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flockio-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*

---
token: Pieverse Token
ticker: PIEVERSE
network: bsc
risk_score: 99
status: critical
date: 2026-07-26
---

# Pieverse Token (PIEVERSE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 99/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pieverse-token-bsc)

---

## Audit Summary

The PieverseOFT contract implements a LayerZero-compatible Omnichain Fungible Token with features such as a global supply cap, time-locked transfers, and a whitelist system. The audit identified a Critical vulnerability related to the owner's ability to bypass the global supply cap, and High-severity issues concerning restricted cross-chain transfers for all users and the multisig's ability to indefinitely extend transfer locks. Several Medium and Low-severity findings highlight centralization risks and operational considerations. The contract generally follows good coding practices and utilizes standard libraries, but critical access control and economic logic flaws require immediate attention.

> **Final Recommendation:** It is critical to address the identified vulnerabilities, especially the owner's ability to bypass the global supply cap and the unintended blocking of cross-chain transfers for all users during the restricted period. The `setTransferAllowedTime` logic should be refined to ensure consistent grace period application and prevent indefinite lock extensions by the multisig. Review and strengthen the operational security for both the owner and multisig roles, considering additional decentralization or time-locks for highly sensitive functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract is built upon LayerZero's OFT standard, leveraging battle-tested components (7.1 Architecture). Code quality is generally good, utilizing Solidity 0.8+ for safety. However, a critical… |
| **Governance / Economics** | 1/10 | High | The economic model relies on a `MAX_SUPPLY` and `supplyAllChains` tracking, but the owner's `syncSupplyAllChains` function can subvert this cap (C-01, 7.4 Economic). Access control is split between… |
| **Upgrades** | 3/10 | High | The PieverseOFT contract is not designed as an upgradeable proxy. Therefore, direct upgradeability risks are not applicable to this specific contract. Any future changes would require a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Owner can bypass global supply cap via `syncSupplyAllChains`  *(Severity: Critical · Status: Unresolved)*

The `syncSupplyAllChains` function, callable by the contract owner, allows setting the `supplyAllChains` variable to any value up to `MAX_SUPPLY`. A malicious or compromised owner could repeatedly set `supplyAllChains` to a low value, then mint additional tokens up to `MAX_SUPPLY - supplyAllChains`, effectively bypassing the intended global supply cap and minting an arbitrary amount of tokens beyond `MAX_SUPPLY`.

**Recommendation:** Remove the `syncSupplyAllChains` function or restrict its functionality. If synchronization is necessary, consider allowing only increases to `supplyAllChains` (e.g., for recovery from undercounting) or implement a multi-signature approval and a time-lock for any changes, especially decreases, to this critical variable.


### `H-01` — Cross-chain transfers (burning) are blocked for ALL users during restricted period  *(Severity: High · Status: Unresolved)*

The `_update` function, which is called for all token transfers, unconditionally reverts if `to == address(0)` (burning) during the `transferAllowedTime` restricted period. This means that even whitelisted users cannot perform cross-chain transfers, as LayerZero's `_send` operation typically involves burning tokens on the source chain. This contradicts the presumed intent of the whitelist, which should allow whitelisted users to transfer tokens, including cross-chain, during the restricted period.

**Recommendation:** Modify the `_update` function to allow burning for whitelisted users during the restricted period. The logic should be similar to how regular transfers are handled: `else if (to == address(0)) { require(isWhitelisted[from], "Not whitelisted for burning during restricted period"); }`.


### `H-02` — Multisig can indefinitely extend transfer lock without grace period  *(Severity: High · Status: Unresolved)*

The `setTransferAllowedTime` function allows the `multisig` to set `transferAllowedTime` to *any* future timestamp if `transferAllowedTime > block.timestamp` and `ETA == 0`. This means that if the initial transfer lock is still active and no grace period has been set, the multisig can indefinitely extend the lock period without any time-based constraints, potentially leading to a permanent denial of service for non-whitelisted transfers.

**Recommendation:** Implement a consistent grace period mechanism for all updates to `transferAllowedTime`. Ensure that any extension of the lock period is subject to a time-lock or a maximum extension duration. Consider requiring a separate governance vote or a time-lock for significant extensions to this critical parameter.


### `M-01` — Centralization risk with `owner` and `multisig` roles  *(Severity: Medium · Status: Unresolved)*

The contract relies heavily on two privileged roles: the `owner` (managing minters and `syncSupplyAllChains`) and the `multisig` (managing the whitelist and `transferAllowedTime`). While using a multisig for the `multisig` role mitigates some risk, a compromise of either the `owner`'s private key or the `multisig`'s quorum could lead to significant control over token supply, transferability, and distribution, posing a single point of failure.

**Recommendation:** Ensure both the `owner` and `multisig` addresses are robustly secured (e.g., hardware wallets, strong operational security for multisig signers). Consider further decentralizing control over critical functions or implementing time-locks for highly sensitive operations to reduce the impact of a single point of compromise.


### `L-01` — Initial minting chain dependency  *(Severity: Low · Status: Unresolved)*

The constructor's initial minting logic is dependent on specific `chainId` values (Ethereum/Sepolia or BNB/Testnet). If the contract is deployed on a chain not explicitly listed in the `if/else if` statements (e.g., Arbitrum, Optimism, Base), no initial tokens will be minted. This might lead to unexpected operational behavior or require manual `mint` calls post-deployment, potentially causing delays or requiring additional administrative overhead.

**Recommendation:** Clearly document the intended deployment chains and initial distribution strategy. If deployment on other chains is anticipated, ensure a clear plan for initial token distribution, either by extending the `chainId` checks or by providing a post-deployment minting mechanism.


### `I-01` — `ETA` variable not reset after grace period  *(Severity: Informational · Status: Unresolved)*

The `ETA` variable, once set (e.g., `transferAllowedTime + 1 days`), is never explicitly reset to 0. This means that subsequent calls to `setTransferAllowedTime` will always be subject to the `ETA` constraint, even if `transferAllowedTime` has long passed. While not a direct vulnerability, this behavior might lead to less intuitive grace period logic or unexpected constraints on future `transferAllowedTime` updates.

**Recommendation:** Clarify the intended lifecycle of the `ETA` variable. If `ETA` is meant to be a temporary grace period, consider resetting it to 0 once `transferAllowedTime` has passed or after a certain condition is met to ensure the logic remains clear and predictable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0e63...25a9`](https://bscscan.com/address/0x0e63b9c287e32a05e6b9ab8ee8df88a2760225a9) |
| **Network** | BNB Chain |
| **Price** | $0.6897 |
| **24h Volume** | $48.4K |
| **Liquidity** | $25.3K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 84.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1302 buys / 1071 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Pieverse Token a scam?

Based on automated analysis, Pieverse Token scores 67/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Pieverse Token safe to buy?

Our scanner flagged a risk score of 67/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Pieverse Token been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x5f983a39df8bfa0763cbf3fa4321edc4f7c4b18b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pieverse-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*

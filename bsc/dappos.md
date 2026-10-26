---
token: DAPPOS
ticker: DOS
network: bsc
risk_score: 48
status: medium
date: 2026-09-01
---

# DAPPOS (DOS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dappos-bsc)

---

## Audit Summary

The DapposTokenOFT contract is an Omnichain Fungible Token (OFT) built on LayerZero v2, inheriting standard ERC-20 functionality and adding Pausable capabilities. The contract leverages well-audited OpenZeppelin and LayerZero libraries. Key risks identified are primarily related to centralized control by the owner (a 3/5 multisig) over critical functions like pausing and LayerZero configurations, as well as the inherent dependency on the LayerZero protocol's security. The contract is not upgradeable via proxy, but the LayerZero delegate can be changed by the owner.

> **Final Recommendation:** Prioritize robust operational security for the 3/5 multisig controlling the `owner` address, as it holds significant power over critical functions like pausing and LayerZero configurations. Implement strict internal procedures for all administrative actions, especially when setting LayerZero peers or changing the delegate address, to prevent misconfigurations or malicious updates. Regularly monitor LayerZero security announcements and ensure the configured endpoint and delegate contracts are trusted and up-to-date.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The DapposTokenOFT contract is a standard ERC-20 token integrated with LayerZero v2 for cross-chain functionality, leveraging battle-tested OpenZeppelin `Ownable` and `Pausable` libraries. The… |
| **Governance / Economics** | 1/10 | High | The governance and economic model of the DapposTokenOFT is straightforward, primarily revolving around the `owner` role. This role, currently held by a 3/5 multisig, possesses significant centralized… |
| **Upgrades** | 7/10 | Low | The DapposTokenOFT contract is not designed as an upgradeable proxy, meaning its core logic cannot be directly changed after deployment (7.7 Upgrades). However, the contract inherits a `setDelegate`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 3 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Critical Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` role, currently a 3/5 multisig, holds significant power, including the ability to pause all token transfers, set LayerZero peers, and change the LayerZero delegate. While a multisig mitigates single-point-of-failure, these centralized controls could still be exploited if the multisig signers are compromised or act maliciously. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Ensure robust operational security for the multisig. Consider implementing time-locks for critical operations or further decentralizing control if feasible in the future.


### `L-01` — Pausable Functionality as Denial of Service Vector  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `pause()` function, callable by the owner, can halt all token transfers indefinitely. While intended for emergency response, a compromised or malicious owner could use this to deny service to all token holders, preventing any movement of tokens. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Implement clear emergency procedures for the `pause` function. Consider adding a time-lock for `unpause()` or a community-driven unpause mechanism if decentralization is a future goal.


### `L-02` — Mutable LayerZero Delegate Address  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setDelegate` function allows the owner to change the LayerZero delegate address. A delegate contract can define custom logic for LayerZero messaging. A malicious or compromised owner could set a malicious delegate, potentially impacting cross-chain message processing or fee handling. (7.3 Access Control, 7.7 Upgrades)

**Recommendation:** Exercise extreme caution when setting or changing the LayerZero delegate. Only use audited and trusted delegate contracts. Consider adding a time-lock to the `setDelegate` function.


### `L-03` — Peer Configuration Criticality  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setPeer` function, controlled by the owner, is crucial for establishing trusted cross-chain communication paths. Incorrectly setting a peer address could lead to cross-chain messages being routed to unintended or malicious contracts, potentially resulting in loss of funds or failed transfers. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Implement strict verification processes for peer addresses before setting them. Double-check all peer configurations to ensure they correspond to the intended destination contracts on other chains.


### `I-01` — Reliance on LayerZero Protocol Security  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DapposTokenOFT` contract is built upon LayerZero v2, inheriting its cross-chain messaging capabilities. The security of the token's cross-chain functionality is directly dependent on the integrity and security of the LayerZero endpoint and its underlying protocol. Any vulnerabilities or misconfigurations within the LayerZero infrastructure could impact the token. (7.6 External)

**Recommendation:** Stay informed about LayerZero security updates and best practices. Regularly review LayerZero's audit reports and ensure the configured LayerZero endpoint is trusted and secure.


### `I-02` — Compiler Version Discrepancy  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DapposTokenOFT` contract uses `pragma solidity ^0.8.22`, while its LayerZero dependencies use `pragma solidity ^0.8.20`. Although `^0.8.22` is compatible with `^0.8.20`, using a consistent and pinned compiler version across all project files can prevent unexpected behavior due to minor compiler differences or bugs. (7.2 Code Security)

**Recommendation:** Consider aligning all `pragma solidity` statements to a single, pinned compiler version (e.g., `0.8.22`) for consistency and to ensure all code is compiled with the exact same rules.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb0f0...0e37`](https://bscscan.com/address/0xb0f09ea9ae0515c3551080d4a745c8115aa30e37) |
| **Network** | BNB Chain |
| **Price** | $0.2474 |
| **24h Volume** | $2.96M |
| **Liquidity** | $876.5K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 21d |
| **Top-10 Holders** | 93.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13137 buys / 15341 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xcbeaad783ffd2cea125e9d9b2ec21e639d20fa59)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dappos-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*

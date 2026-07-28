---
token: Block Street
ticker: BSB
network: bsc
risk_score: 81
status: critical
date: 2026-07-24
---

# Block Street (BSB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/block-street-bsc)

---

## Audit Summary

The audit of the TokenImplementation contract, serving as the logic for a BeaconProxy, reveals a well-structured ERC-20 token with standard functionalities. Key strengths include proper use of the `initializer` modifier for upgrade safety and adherence to basic ERC-20 standards. However, the contract exhibits a high degree of centralization, with a single owner having full control over token supply (mint/burn) and metadata updates. Additionally, while EIP-712 domain separator logic is present, the `permit` function itself is missing, indicating an incomplete feature implementation. The custom `Ownable` pattern also deviates from standard OpenZeppelin practices.

> **Final Recommendation:** It is recommended to evaluate the level of centralization and consider implementing a multi-signature wallet or a time-locked governance mechanism for critical functions like `mint`, `burn`, and `updateDetails` to mitigate single-point-of-failure risks. Additionally, consider either fully implementing the EIP-712 `permit` function to leverage the existing infrastructure or removing the unused EIP-712 related code to improve clarity. For the custom `Ownable` implementation, ensure clear documentation is provided to avoid developer confusion regarding expected ownership behaviors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical implementation of the Token contract is generally robust, adhering to ERC-20 standards for core functionalities like `transfer` and `approve`. Solidity 0.8.0+ provides automatic… |
| **Governance / Economics** | 1/10 | High | The governance and economic model of the Token contract are highly centralized. A single `owner` address possesses significant power, including the ability to `mint` and `burn` an arbitrary amount of… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for a BeaconProxy, leveraging OpenZeppelin's proxy patterns for upgradeability. The `initializer` modifier correctly prevents re-initialization on… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Token Supply and Metadata  *(Severity: High · Status: Unresolved)*

The `owner` address has the ability to `mint` and `burn` an arbitrary amount of tokens, directly affecting the total supply and value. Additionally, the `owner` can `updateDetails` (name, symbol) of the token. This grants significant centralized control over the token's economic properties and identity, posing a high risk if the owner's key is compromised or acts maliciously. This impacts 7.3 Access Control and 7.4 Economic aspects.

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance contract to control the `owner` address. For critical functions like `mint` and `burn`, consider requiring multiple approvals or a delay period. Clearly document the extent of owner privileges and the security measures in place for the owner's private key.


### `M-01` — Missing `permit` Function for EIP-712 Support  *(Severity: Medium · Status: Unresolved)*

The contract includes extensive logic for EIP-712 domain separator generation (`_initializePermitStateIfNeeded`, `_domainSeparatorV4`, `_buildDomainSeparator`) and imports `ECDSA`, indicating an intention to support EIP-712 `permit` functionality. However, the actual `permit` function, which allows users to approve token transfers via a signed message without on-chain transactions, is not implemented. This leaves the EIP-712 infrastructure present but unused, resulting in an incomplete feature. This impacts 7.1 Architecture and 7.2 Code Security.

**Recommendation:** Either fully implement the EIP-712 `permit` function to provide the intended functionality, or remove the unused EIP-712 related code and imports to reduce contract size and improve clarity if the feature is not desired.


### `L-01` — Custom `Ownable` Implementation Deviates from Standard  *(Severity: Low · Status: Unresolved)*

The contract imports OpenZeppelin's `Ownable.sol` but does not inherit from it. Instead, it implements its own `owner()` function and `onlyOwner` modifier, managing the `_state.owner` variable directly. While functionally correct for this contract, this deviation from standard OpenZeppelin patterns might lead to confusion or unexpected behavior for developers expecting the full `Ownable` interface (e.g., `transferOwnership`, `renounceOwnership`). This impacts 7.1 Architecture and 7.2 Code Security.

**Recommendation:** Consider either inheriting from OpenZeppelin's `Ownable` to leverage its battle-tested implementation and standard interface, or explicitly documenting the custom ownership management to clarify expected behavior and available functions.


### `I-01` — `updateDetails` Requires Sequence Increment  *(Severity: Informational · Status: Unresolved)*

The `updateDetails` function, which allows the owner to change the token's name and symbol, requires the `sequence_` parameter to be strictly greater than `_state.metaLastUpdatedSequence`. This mechanism prevents replaying old metadata updates but also implies that if an owner wishes to revert to a previous name/symbol (e.g., due to a typo), they must use a new, higher sequence number. This is a design choice, not a vulnerability, but it's an operational constraint. This impacts 7.8 Operations.

**Recommendation:** Ensure this design choice is well-documented for operators. If flexibility to revert to previous metadata is desired without incrementing a sequence, the `require` statement would need to be adjusted, but this would also introduce the risk of replay attacks for metadata updates.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x595d...79cc`](https://bscscan.com/address/0x595deaad1eb5476ff1e649fdb7efc36f1e4679cc) |
| **Network** | BNB Chain |
| **Price** | $0.1235 |
| **24h Volume** | $19.5K |
| **Liquidity** | $48.0K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 92.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 393 buys / 405 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Frequently Asked Questions

### Is Block Street a scam?

Based on automated analysis, Block Street scores 64/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Block Street safe to buy?

Our scanner flagged a risk score of 64/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Block Street been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xe62e359809d1d2396341b7c1ec81e205501870d0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/block-street-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*

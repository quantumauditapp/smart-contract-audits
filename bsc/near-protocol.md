---
token: NEAR Protocol
ticker: NEAR
network: bsc
risk_score: 82
status: high
date: 2026-09-28
---

# NEAR Protocol (NEAR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/near-protocol-bsc)

---

## Audit Summary

The BEP20 Token implementation contract exhibits a high overall risk level primarily due to centralized minting capabilities controlled by the owner and a critical code integrity issue with a truncated internal function. While the contract correctly implements the upgradeable proxy pattern and uses SafeMath for arithmetic operations, the owner's ability to mint tokens poses a significant economic risk. Additionally, the `_burnFrom` function is incomplete, indicating a potential flaw in the deployed code's completeness or quality. The owner also has the ability to irreversibly renounce ownership, which could lead to a loss of administrative control.

> **Final Recommendation:** It is strongly recommended to address the truncated `_burnFrom` function by completing or removing it to ensure code integrity and prevent potential runtime errors if the function is ever invoked. The centralized minting capability should be carefully considered; if not essential, it should be removed or placed under a more decentralized governance mechanism. Furthermore, the `renounceOwnership` function should be used with extreme caution, as its execution leads to an irreversible loss of administrative control. Consider implementing a multi-signature wallet for ownership to enhance security and prevent single points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract utilizes SafeMath for robust arithmetic operations, mitigating common integer overflow/underflow vulnerabilities. However, a significant technical flaw exists with the truncated… |
| **Governance / Economics** | 1/10 | High | The contract's economic model presents a high risk due to the centralized minting capability (H-02), allowing the owner to arbitrarily increase token supply and dilute value. While the `_mintable`… |
| **Upgrades** | 1/10 | High | The contract correctly implements the `Initializable` pattern and features an empty constructor (I-01), adhering to best practices for upgradeable proxy implementations. This design minimizes the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 66.5% |
| **Top-3 Unlocked** | 74.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Truncated `_burnFrom` Function  *(Severity: High · Status: Unresolved)*

The `_burnFrom` internal function is incomplete in the provided source code, ending abruptly. While this function is not currently called by any other function within the contract, its truncation represents a significant code integrity flaw. If a future function or an upgrade were to rely on `_burnFrom`, it would lead to runtime errors or unexpected behavior. This indicates a potential issue with the deployed code's completeness or quality.

**Recommendation:** Review the original source code for the `_burnFrom` function. If it is intended to be part of the contract, ensure its full and correct implementation. If it is not intended for use, consider removing the incomplete function to avoid confusion and potential future issues.


### `H-02` — Centralized Minting Capability  *(Severity: High · Status: Unresolved)*

The `mint` function allows the contract owner to create an arbitrary amount of new tokens, provided the `_mintable` flag is set to `true` during initialization. This centralized control over token supply introduces significant economic risk, as the owner can dilute the value of existing tokens at will, potentially harming token holders.

**Recommendation:** Evaluate if centralized minting is a necessary feature for the token's economic model. If not, consider removing the `mint` function and setting `_mintable` to `false` permanently. If minting is required, implement a more decentralized or time-locked mechanism, such as a governance-controlled minting schedule or a multi-signature approval process, to reduce the risk of arbitrary supply inflation.


### `M-01` — Irreversible Renouncement of Ownership  *(Severity: Medium · Status: Unresolved)*

The `renounceOwnership` function allows the current owner to transfer ownership to the zero address (`address(0)`). If executed, this action is irreversible and would leave the contract without an owner. Consequently, all `onlyOwner` functions, including `mint` (if `_mintable` is true) and `transferOwnership`, would become permanently inaccessible, potentially hindering future administrative actions or upgrades.

**Recommendation:** Owners should exercise extreme caution when using `renounceOwnership`. It is recommended to transfer ownership to a secure, multi-signature wallet or a robust governance contract instead of renouncing it to the zero address, unless the intention is to permanently decentralize control over all owner-restricted functions.


### `L-01` — Immutability of `_mintable` Flag  *(Severity: Low · Status: Unresolved)*

The `_mintable` flag, which controls whether new tokens can be minted, is set only during the `initialize` function and cannot be modified thereafter. This design choice means that the minting capability is permanently enabled or disabled based on the initial deployment configuration. While a clear design, it lacks flexibility for future adjustments to the token's economic policy.

**Recommendation:** If future flexibility is desired, consider implementing a function (restricted to the owner or governance) to toggle the `_mintable` flag. This would allow for dynamic adjustments to the token's minting policy without requiring a full contract upgrade.


### `I-01` — Standard Proxy Implementation Pattern  *(Severity: Informational · Status: Resolved)*

The contract correctly implements the `Initializable` pattern and has an empty `constructor`, which is standard practice for upgradeable contracts designed to be used as an implementation behind a proxy. This ensures proper initialization through the `initialize` function and avoids issues with proxy storage collisions.

**Recommendation:** No specific recommendation. This is a best practice for upgradeable contracts.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1fa4...5d63`](https://bscscan.com/address/0x1fa4a73a3f0133f0025378af00236f3abdee5d63) |
| **Network** | BNB Chain |
| **Price** | $5.1100 |
| **24h Volume** | $362.7K |
| **Liquidity** | $198.4K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 3y |
| **Top-10 Holders** | 40.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1887 buys / 1846 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x0246913ec96765bca457b0a3608872bba37d1d15)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/near-protocol-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*

---
token: Filecoin
ticker: FIL
network: bsc
risk_score: 54
status: medium
date: 2026-09-02
---

# Filecoin (FIL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/filecoin-bsc)

---

## Audit Summary

The audit of the BEP20 Token implementation contract identified a medium-level risk related to centralized control over token minting, which could lead to supply manipulation if the owner's key is compromised. Minor issues include the immutability of the mintable flag and an incomplete internal function. The contract demonstrates good practices for upgradeability and uses SafeMath to prevent arithmetic overflows. Overall, the contract is well-structured but requires careful management of the owner's privileges.

> **Final Recommendation:** It is strongly recommended to secure the owner's private key with robust measures, such as a multi-signature wallet, to mitigate the risk of centralized control over token minting. Consider the long-term implications of the immutable `_mintable` flag and ensure it aligns with the project's future vision. Complete the `_burnFrom` function to improve code quality and prevent potential issues if it is ever intended for use. Finally, evaluate upgrading to a more recent Solidity compiler version to benefit from enhanced security features and optimizations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates good technical practices by utilizing SafeMath for all arithmetic operations, effectively preventing integer overflow/underflow vulnerabilities (7.2 Code Security). It… |
| **Governance / Economics** | 3/10 | High | The contract implements a standard Ownable pattern, granting the _owner address significant control over critical functions such as mint and transferOwnership (7.3 Access Control). This centralized… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation, correctly using the Initializable base contract and an empty constructor (7.7 Upgrades). This setup ensures that state variables are… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 59.8% |
| **Top-3 Unlocked** | ⚠️ 82.3% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control of Token Supply  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_owner` address has the sole authority to mint new tokens if the `_mintable` flag is set to true during initialization. This introduces a single point of failure where a compromised owner key could lead to arbitrary inflation of the token supply, devaluing existing tokens. This impacts access control (7.3) and economic stability (7.4).

**Recommendation:** Implement a multi-signature wallet for the owner address to control critical functions like `mint`. This distributes control and requires multiple approvals for sensitive operations, significantly reducing the risk of a single point of compromise.


### `L-01` — Immutability of `_mintable` Flag  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_mintable` flag, which controls whether new tokens can be minted, is set only during the `initialize` function and cannot be changed thereafter. This design choice means the token's minting capability is permanently fixed upon deployment, which might limit future flexibility if the project's requirements evolve. This is a design consideration (7.1) and governance aspect (7.5).

**Recommendation:** If future flexibility is desired, consider adding an `onlyOwner` function to toggle the `_mintable` flag. Alternatively, clearly document this immutability as a core design decision for the token's economic model.


### `I-01` — Incomplete `_burnFrom` Function  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `_burnFrom` internal function is truncated and therefore incomplete. While this function is not called by any other public or internal function in the provided code, its incompleteness represents a code quality issue and a potential bug if it were intended for future use or if other parts of the system rely on its full implementation. This affects code security (7.2).

**Recommendation:** Complete the implementation of the `_burnFrom` function to ensure code correctness and maintainability. If it's not intended for use, consider removing it to avoid confusion.


### `I-02` — Use of Older Solidity Version  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `pragma solidity ^0.6.0`. While functional, newer Solidity versions (e.g., `^0.8.0`) offer additional security features (like default checked arithmetic), gas optimizations, and clearer error messages. Migrating to a newer version could improve overall code robustness and efficiency (7.2 Code Security).

**Recommendation:** Consider upgrading the Solidity compiler version to `^0.8.0` or higher. Thoroughly test the contract after migration to ensure compatibility and correct functionality.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0d8c...e153`](https://bscscan.com/address/0x0d8ce2a99bb6e3b7db580ed848240e4a0f9ae153) |
| **Network** | BNB Chain |
| **Price** | $0.7726 |
| **24h Volume** | $189.2K |
| **Liquidity** | $60.5K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 30.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6519 buys / 6873 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x16d7c51e9c59be9f18b19b608d53b37fa9890b8a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/filecoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*

---
token: MOMO
ticker: MOMO
network: ethereum
risk_score: 41
status: medium
date: 2026-08-11
---

# MOMO (MOMO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/momo-eth)

---

## Audit Summary

The MomoToken contract is a standard ERC20 token implementation, inheriting from OpenZeppelin's ERC20, ERC20Burnable, and ERC20Permit contracts. It features a fixed initial supply minted to a specified recipient during deployment. The contract exhibits a low overall risk profile due to its simplicity, reliance on battle-tested libraries, and lack of complex custom logic or privileged roles post-deployment. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** It is recommended to ensure the `initialRecipient` address provided during deployment is correct and secure, as all initial tokens will be minted to this address. Given the contract's immutable nature, any errors in the constructor parameters cannot be rectified post-deployment. For future developments, consider the implications of using draft standards like ERC20Permit and monitor their evolution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) of MomoToken is robust, leveraging OpenZeppelin's well-audited ERC20, ERC20Burnable, and ERC20Permit implementations. The custom logic is minimal, consisting solely… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) for MomoToken is simple and transparent: a fixed total supply is minted once at deployment, with no further inflation mechanisms. Deflation is possible only through standard… |
| **Upgrades** | 6/10 | Medium | The MomoToken contract is implemented as a standard, non-upgradeable contract. This design choice inherently eliminates all risks associated with upgrade mechanisms (7.7), such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 97.9% |
| **Top-3 Unlocked** | ⚠️ 99.4% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Unused State Variable `_PERMIT_TYPEHASH_DEPRECATED_SLOT`  *(Severity: Low · Status: Unresolved)*

The `ERC20Permit` contract declares a private state variable `bytes32 private _PERMIT_TYPEHASH_DEPRECATED_SLOT;` which is never assigned a value or used within the contract. This represents dead code and a minor inefficiency.

**Recommendation:** Remove the unused state variable `_PERMIT_TYPEHASH_DEPRECATED_SLOT` to improve code clarity and slightly reduce contract deployment size.


### `I-01` — Use of Draft ERC Standard  *(Severity: Informational · Status: Unresolved)*

The contract utilizes `ERC20Permit`, which is currently a 'draft' ERC standard (indicated by `draft-ERC20Permit.sol` in OpenZeppelin). While functional, draft standards are subject to change and may not be as widely adopted or battle-tested as finalized standards.

**Recommendation:** Be aware that draft standards may evolve. Monitor the status of ERC20Permit and consider the implications if the standard undergoes significant changes in the future. For production systems, finalized standards are generally preferred.


### `I-02` — Fixed Supply and No Central Control  *(Severity: Informational · Status: Unresolved)*

The MomoToken contract has a fixed `INITIAL_SUPPLY` minted entirely to a single recipient during construction. There are no owner-controlled minting, burning, pausing, or upgrade functionalities. This design ensures decentralization and predictability of the token supply.

**Recommendation:** This is a design choice that enhances decentralization and reduces governance risk. Ensure this aligns with the long-term vision for the token. No action is required if this is the intended design.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x664e...6e81`](https://etherscan.io/address/0x664e9d73db2a3514f6b437137de4779977a06e81) |
| **Network** | Ethereum |
| **Price** | $0.0006384 |
| **24h Volume** | $89.1K |
| **Liquidity** | $56.2K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 4d |
| **Top-10 Holders** | 71.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 318 buys / 172 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x9b84d57361364a8d219d9bbfefaa7ccf5d1ef833124f3749c930ba062b93a4e8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/momo-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*

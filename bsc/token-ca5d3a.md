---
token: 永生果蝇
ticker: 永生果蝇
network: bsc
risk_score: 18
status: low
date: 2026-09-19
---

# 永生果蝇 (永生果蝇) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-ca5d3a-bsc)

---

## Audit Summary

This audit covers the FlapTaxTokenV3 contract, an upgradeable ERC20 token with a dynamic tax mechanism. A critical portion of the `_liquidateTax` function was truncated in the provided source, preventing a comprehensive security assessment of the core tax collection and distribution logic. This significantly limits the scope and confidence of the audit, leading to a Critical overall risk level due to unverified core functionality.

> **Final Recommendation:** It is imperative to provide the complete source code for the `_liquidateTax` function to enable a full security assessment of the contract's core economic logic. Without this, the audit cannot provide full assurance. Review and consider decentralizing critical administrative functions where possible, or implementing multi-signature control for sensitive operations. Thoroughly test all state transitions and tax calculations, especially considering the time-based mechanisms and their interactions with external components.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's upgradeable standards for ERC20, Ownable, and Permit functionalities, demonstrating good practice in modularity and security patterns (7.1 Architecture, 7.2 Code… |
| **Governance / Economics** | 6/10 | Medium | The contract implements a dynamic tax system with various `PoolState`s and time-based transitions, managed by the owner (7.4 Economic, 7.5 Governance). The `onlyOwner` modifier grants the deployer… |
| **Upgrades** | 9/10 | Low | The contract utilizes the UUPS proxy pattern via OpenZeppelin's `Initializable` and `Upgradeable` contracts, providing a robust and well-understood upgrade mechanism (7.7 Upgrades). The constructor… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Potential for Tax Accumulation Without Liquidation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, which is responsible for processing collected taxes, is only triggered when a transfer's `to` address is the `mainPool`. If transfers to the `mainPool` are infrequent or cease, collected tax amounts held by the contract (`balanceOf(address(this))`) could accumulate indefinitely without being processed or distributed. This could lead to locked funds or delayed dividend payouts, impacting the economic model (7.4 Economic, 7.8 Operations).

**Recommendation:** Implement a mechanism to allow the owner or a designated role to manually trigger tax liquidation, or introduce a time-based fallback to process accumulated taxes if the `mainPool` condition is not met within a certain period. This ensures that collected taxes are always processed, regardless of transfer patterns.


### `M-02` — Incomplete `_liquidateTax` Function Prevents Full Audit  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `_liquidateTax` function is truncated. This function is called on every `_transfer` to the `mainPool` and is responsible for handling collected taxes, managing state transitions based on `taxExpirationTime` and `antiFarmerExpirationTime`, and potentially interacting with `taxProcessor` or `dividendContract`. Without the complete code, it is impossible to assess critical aspects such as reentrancy vulnerabilities, correct tax distribution logic, potential for fund locking, or proper handling of external calls. This severely limits the scope and confidence of the entire audit (7.2 Code Se

**Recommendation:** Provide the complete and untruncated source code for the `_liquidateTax` function to allow for a comprehensive security review of this critical component. A full audit cannot be completed without this information.


### `M-03` — Centralized Control via `onlyOwner`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `onlyOwner` modifier grants significant control over critical contract functions, including `startMigration` and `finalizeMigration`. This centralization of power means that a single compromised private key or a malicious owner could unilaterally alter the contract's operational state, potentially impacting token transfers, tax rates, and overall protocol stability. This introduces a single point of failure (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for the owner role to distribute control and reduce the risk associated with a single point of failure. For highly sensitive operations, a time-locked governance mechanism could be explored to provide transparency and allow users to react to proposed changes.


### `L-01` — Hardcoded `maxSupply` and Initial Mint to Deployer  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxSupply` of 1 billion tokens is hardcoded and all tokens are minted to `msg.sender` (the deployer) during the `initialize` function. This design centralizes the entire token supply in a single address at deployment, which could raise concerns regarding token distribution, market manipulation, or potential for a large single point of failure if the deployer's wallet is compromised (7.4 Economic).

**Recommendation:** While this might be an intentional design choice for specific tokenomics, consider documenting the distribution plan for the initial supply. For future projects, explore more decentralized initial distribution mechanisms or vesting schedules if broader community ownership is desired.


### `I-01` — Reliance on `block.timestamp` for Time-Sensitive Logic  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `block.timestamp` for time-sensitive logic, specifically for `taxExpirationTime` and `antiFarmerExpirationTime`. While common, `block.timestamp` can be manipulated by miners within a small window (up to 900 seconds on Ethereum, similar on BSC), potentially allowing them to slightly front-run or back-run state transitions if they have an economic incentive (7.2 Code Security).

**Recommendation:** For most applications, `block.timestamp` is sufficient. However, for highly critical time-sensitive operations where even minor manipulation could lead to significant economic advantage, consider using Chainlink Keepers or similar decentralized oracle networks for time-based triggers, or implement a time-weighted average of block timestamps if extreme precision and resistance to miner manipulation are paramount.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x225a...7777`](https://bscscan.com/address/0x225ad472938d116f957bf86fb6b611da144f7777) |
| **Network** | BNB Chain |
| **Price** | $0.0005391 |
| **24h Volume** | $738.2K |
| **Liquidity** | $75.5K |
| **Volume / Liquidity** | 9.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | 29.0% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 5543 buys / 3890 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xd7632dd04e030f17532a2b9524280f0c55f2ce9d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-ca5d3a-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-19*

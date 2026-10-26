---
token: BEM
ticker: BEM
network: bsc
risk_score: 11
status: low
date: 2026-08-30
---

# BEM (BEM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bem-bsc)

---

## Audit Summary

The PodToken contract is an ERC-20 token implementation based on OpenZeppelin's battle-tested libraries. It features a fixed maximum supply and a single, immutable minter address responsible for issuing tokens up to this cap. The contract's logic is straightforward, primarily extending standard ERC-20 functionality with a controlled minting mechanism. While technically sound, the centralized minter role introduces a medium economic risk due to its significant control over token supply.

> **Final Recommendation:** It is recommended to implement robust operational security for the `minter` address, ideally using a multi-signature wallet or a time-locked contract to mitigate the risk of a single point of failure. Ensure all integrations and user interfaces are aware of the 8-decimal standard to prevent display or calculation errors. Conduct thorough testing of any external systems interacting with the token to confirm correct handling of its specific decimal configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation of PodToken is robust, leveraging OpenZeppelin's ERC-20 standard for core token functionalities (7.2 Code Security). The contract's custom logic for minting is minimal… |
| **Governance / Economics** | 6/10 | Medium | The primary economic consideration is the centralized control over token minting (7.4 Economic). The `minter` address holds exclusive power to issue tokens up to the `MAX_SUPPLY`, which is a… |
| **Upgrades** | 4/10 | Medium | The PodToken contract is not designed to be upgradeable (7.7 Upgrades). It is a standard, non-proxy implementation, meaning its logic is immutable once deployed. This eliminates any risks associated… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.0% (≈ permanent lock) |
| **LP Locked** | 99.0% — Dead Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Minter Role  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `minter` address, set during contract deployment, has exclusive control over the `mint` function. This allows the `minter` to issue new tokens up to the `MAX_SUPPLY` (21,000,000 tokens with 8 decimals). This centralized control introduces a single point of failure; if the `minter`'s private key is compromised or if the `minter` acts maliciously, the entire remaining supply could be minted and potentially dumped, impacting token value and user trust. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) or a time-locked contract for the `minter` role. This would require multiple approvals or introduce a delay for minting operations, significantly reducing the risk associated with a single compromised key or malicious actor. Alternatively, if the `minter` is intended to be a DAO, ensure the DAO's governance is robust.


### `L-01` — Minter Key Management Considerations  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). If the `minter` address is an Externally Owned Account (EOA), it is inherently susceptible to private key compromise through phishing, malware, or poor key management practices. While the contract's logic is secure, the operational security of the `minter`'s private key is critical to the overall security of the token supply. (7.8 Operations)

**Recommendation:** It is strongly recommended that the `minter` address be controlled by a secure mechanism such as a hardware wallet, a multi-signature wallet, or a smart contract with robust access control and recovery features. Regular security audits and best practices for key management should be followed for the entity controlling the `minter` address.


### `I-01` — Non-Standard Decimals  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PodToken` contract explicitly sets `DECIMALS` to 8, overriding the default 18 used by many ERC-20 tokens and OpenZeppelin's base `ERC20` contract. While this is a valid design choice and correctly implemented, it deviates from the common standard. This requires all interacting dApps, exchanges, and wallets to correctly interpret the token's decimal places to prevent display errors, incorrect calculations, or user confusion. (7.1 Architecture)

**Recommendation:** Ensure that all documentation, user interfaces, and integrations clearly communicate and correctly handle the 8-decimal precision of the PodToken. Thoroughly test all external systems that interact with the token to confirm they correctly interpret and display token amounts.


### `I-02` — Fixed Supply and Immutability  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The PodToken contract is designed with a fixed `MAX_SUPPLY` of 21,000,000 tokens (with 8 decimals) and an immutable `minter` address set during construction. This design ensures that the total token supply cannot exceed a predefined limit and that the minting authority cannot be changed after deployment. This provides predictability and transparency regarding the token's economic model. (7.1 Architecture, 7.4 Economic)

**Recommendation:** No recommendation needed as this is a design feature. Maintain clear documentation of these immutable parameters for users and integrators.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5ce0...695a`](https://bscscan.com/address/0x5ce033b2bfca3af30b3e8c8457deaf776a8b695a) |
| **Network** | BNB Chain |
| **Price** | $13.2600 |
| **24h Volume** | $318.1K |
| **Liquidity** | $62.3K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 8d |
| **Top-10 Holders** | 17.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2014 buys / 2844 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x2f5ec19ab0583d3fcd9bcbcd9ab416d2858eea38)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bem-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

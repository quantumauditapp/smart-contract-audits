---
token: BREWCAT
ticker: BREWCAT
network: bsc
risk_score: 32
status: low
date: 2026-09-14
---

# BREWCAT (BREWCAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 32/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/brewcat-bsc)

---

## Audit Summary

The BrewToken contract is a standard ERC-20 token implementation, inheriting from battle-tested OpenZeppelin libraries. It features a fixed total supply minted at deployment and immutable metadata. The contract's simplicity and reliance on audited components contribute to a low overall risk profile. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** The BrewToken contract is a well-implemented ERC-20 token, leveraging industry-standard OpenZeppelin libraries. Its simplicity and lack of complex logic or privileged roles contribute to a strong security posture. It is recommended to ensure that the initial deployment parameters, such as `totalSupply_` and `recipient_`, are correctly configured, as these are immutable post-deployment. 

While the `tokenURI()` function is unusual for an ERC-20, it poses no direct security risk. Stakeholders should be aware of its static nature and the immutability of `metadataURI` if future metadata changes are ever considered for the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1 Architecture) of BrewToken is straightforward, implementing a standard ERC-20 token. Code security (7.2 Code Security) is robust due to its reliance on OpenZeppelin's… |
| **Governance / Economics** | 3/10 | High | The economic model (7.4 Economic) of BrewToken is simple and predictable: a fixed total supply is minted once during deployment to a specified recipient. There are no post-deployment minting or… |
| **Upgrades** | 6/10 | Medium | The BrewToken contract is not designed to be upgradeable (7.7 Upgrades), as it does not implement any proxy patterns. This eliminates the risks associated with upgradeability, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.0% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_⚪ 4 Informational_

### `I-01` — Unusual `tokenURI` Function for ERC-20  *(Severity: Informational · Status: Unresolved)*

The `BrewToken` contract includes a public `tokenURI()` function, which is typically associated with ERC-721 or ERC-1155 NFTs for retrieving metadata. While not a vulnerability, its presence on an ERC-20 token is unconventional and might lead to confusion or misinterpretation of the token's nature or capabilities by users or platforms expecting standard ERC-20 behavior. This falls under 7.1 Architecture.

**Recommendation:** Clarify the purpose of the `tokenURI()` function in documentation. If it serves no specific purpose for an ERC-20, consider removing it to avoid confusion and adhere strictly to ERC-20 standards. If it's intended for specific off-chain integrations, ensure those integrations are well-documented.


### `I-02` — Immutable `metadataURI` Post-Deployment  *(Severity: Informational · Status: Unresolved)*

The `metadataURI` variable is set only during the contract's construction and has no setter function, making it immutable after deployment. This means the token's associated metadata URI cannot be updated or changed in the future. This falls under 7.4 Economic and 7.8 Operations.

**Recommendation:** Confirm if the immutability of `metadataURI` is an intentional design choice. If there's a future need for dynamic metadata, consider implementing an owner-controlled function to update this URI. However, for a simple, static token, immutability can be a feature, ensuring predictability.


### `I-03` — Fixed Supply and Decentralized Control  *(Severity: Informational · Status: Unresolved)*

The `BrewToken` contract mints a fixed total supply to a specified recipient during deployment and lacks any further minting or burning capabilities exposed to external users. The `creator` and `brewFactory` addresses are immutable and hold no special privileges post-deployment. This design promotes a decentralized and predictable token economy, as no single entity can alter the supply or control core token functions after deployment. This is a strength in terms of 7.3 Access Control and 7.4 Economic.

**Recommendation:** No specific recommendation, as this is a positive security characteristic. Maintain clear documentation regarding the fixed supply and lack of administrative control post-deployment to manage user expectations.


### `I-04` — Reliance on Battle-Tested OpenZeppelin Libraries  *(Severity: Informational · Status: Unresolved)*

The `BrewToken` contract inherits its core ERC-20 functionality from OpenZeppelin's `ERC20` implementation. OpenZeppelin contracts are widely adopted, rigorously audited, and continuously reviewed by the community, significantly reducing the likelihood of common ERC-20 vulnerabilities such as reentrancy, integer overflows/underflows, and standard compliance issues. This contributes positively to 7.2 Code Security.

**Recommendation:** Continue to monitor OpenZeppelin's security advisories and updates. Ensure that the specific version of OpenZeppelin contracts used (`^0.8.20`) remains secure and compatible with the chosen Solidity compiler version.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9b2b...cfea`](https://bscscan.com/address/0x9b2bf8e150d0f316e3835da0bfdab5b96990cfea) |
| **Network** | BNB Chain |
| **Price** | $0.0003307 |
| **24h Volume** | $140.2K |
| **Liquidity** | $89.6K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 8d |
| **Top-10 Holders** | 37.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 547 buys / 704 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x30a8b6ba24d3649d66c5c40888dc4a3af0be404c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/brewcat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*

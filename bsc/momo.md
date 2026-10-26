---
token: MOMO
ticker: MOMO
network: bsc
risk_score: 33
status: low
date: 2026-09-12
---

# MOMO (MOMO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/momo-bsc)

---

## Audit Summary

The BrewToken contract is a standard ERC20 implementation inheriting from OpenZeppelin's battle-tested library. It includes immutable `creator` and `brewFactory` addresses and a fixed `metadataURI`. The contract's simplicity and reliance on well-audited components contribute to a low overall risk profile. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** Ensure that the chosen `metadataURI` is stable and points to a reliable source, as it cannot be changed after deployment. Consider implementing a mechanism for recovering accidentally sent ERC20 tokens (other than BrewToken itself) to the contract address, if such a feature is deemed necessary for operational robustness.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) is straightforward, implementing a standard ERC20 token with minimal custom logic. Code security (7.2) is robust due to the use of OpenZeppelin's ERC20 library, which… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4) is a simple fixed-supply ERC20 token, minted entirely during deployment. There are no complex tokenomics, fees, or rebase mechanisms, which simplifies economic analysis and… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable (7.7), as it does not implement any proxy patterns. This eliminates the risks associated with upgradeability, such as proxy misconfigurations or logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — Lack of Emergency Token Recovery  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BrewToken` contract does not include a function to recover arbitrary ERC20 tokens (other than BrewToken itself) that might be accidentally sent to the contract address. Such tokens would become permanently locked and inaccessible, leading to potential loss of funds if users or other contracts mistakenly send them.

**Recommendation:** Implement a `recoverERC20` function, callable by a trusted address (e.g., `creator` or a designated owner), to retrieve accidentally sent tokens. This enhances operational safety and prevents permanent loss of assets.


### `I-01` — Unconventional `tokenURI()` in ERC20  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BrewToken` contract includes a `tokenURI()` function, which is typically associated with ERC721 or ERC1155 NFTs for retrieving token-specific metadata. While not a vulnerability, its presence in an ERC20 token might lead to confusion regarding the token's nature or expected functionality among users or integrators.

**Recommendation:** Clarify the purpose of `tokenURI()` in documentation or consider if it's truly necessary for an ERC20 token. If it's intended for off-chain metadata, ensure the `metadataURI` is robust and its purpose is well-communicated.


### `I-02` — Immutable `metadataURI`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `metadataURI` variable is set only during contract construction and cannot be modified thereafter. This design choice makes the token's metadata immutable. If there's a future need to update or change the metadata (e.g., due to broken links or evolving project branding), this contract design would prevent it without a redeployment.

**Recommendation:** Confirm that the immutability of `metadataURI` aligns with the project's long-term requirements. If dynamic metadata is desired, a setter function with appropriate access control would be required in a future version or an upgradeable contract design.


### `I-03` — Unused Immutable Variables  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `creator` and `brewFactory` addresses are stored as immutable state variables but are not utilized in any access control mechanisms or special logic within the contract. They serve purely as informational fields, which might lead to questions about their practical purpose if not clearly documented.

**Recommendation:** Document the intended purpose of these variables clearly. If they are meant to signify origin or a related entity, ensure this is communicated to users. If they were intended for access control, consider adding functions that leverage them.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbc5f...4024`](https://bscscan.com/address/0xbc5ff7fe4d1b928423cf6c54bfa5f907130b4024) |
| **Network** | BNB Chain |
| **Price** | $0.00205 |
| **24h Volume** | $1.36M |
| **Liquidity** | $198.7K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 5d |
| **Top-10 Holders** | 33.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2058 buys / 1914 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xbed17ca05ca914ed977f86c53e8f2607d9f1c9ec)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/momo-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*

---
token: The Stonks Exchange
ticker: STONKEX
network: base
risk_score: 29
status: low
date: 2026-08-30
---

# The Stonks Exchange (STONKEX) — Smart Contract Security Analysis | Base

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-stonks-exchange-base)

---

## Audit Summary

The StonkToken contract is an ERC-20 token implementation, inheriting from OpenZeppelin's battle-tested ERC20 standard. The contract's primary custom logic involves a `tokenURI()` function that queries an external `launcher` contract for a base URI. The audit identified a medium-severity risk related to this external dependency, a low-severity architectural quirk, and an informational finding regarding initial token distribution. The core ERC-20 functionality is robust due to OpenZeppelin inheritance.

> **Final Recommendation:** It is recommended to carefully manage the `launcher` address, as its associated contract controls the `baseTokenURI` which influences how the token's metadata is presented. Ensure the `launcher` contract is secure and its `baseTokenURI` function is robust against manipulation. Additionally, consider documenting the intended use of the `tokenURI()` function for an ERC-20 token to clarify its purpose for users and integrators.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The StonkToken contract demonstrates good technical architecture (7.1) by inheriting from OpenZeppelin's ERC20, which provides a robust and audited foundation for token functionality. The custom… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4) of StonkToken is straightforward: a fixed total supply is minted entirely to the `launcher` address during deployment. This design choice centralizes initial token… |
| **Upgrades** | 6/10 | Medium | The StonkToken contract is not designed with upgradeability in mind (7.7). It is a standard, non-proxy implementation, meaning its logic cannot be altered post-deployment. This reduces complexity and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.5% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — External Dependency Risk in tokenURI Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `tokenURI()` function makes an external call to `IStonkLauncherBaseURI(launcher).baseTokenURI()`. While a `try/catch` block is used to handle reverts, a compromised or malicious `launcher` contract could return a `baseTokenURI` that points to a phishing site, misleading information, or content that misrepresents the StonkToken. This external dependency (7.6) introduces a risk to users who rely on the token's metadata for display or interaction.

**Recommendation:** Ensure the `launcher` address is controlled by a highly secure multi-signature wallet or a robust governance mechanism. Implement strict controls and auditing procedures for the `launcher` contract, especially for its `baseTokenURI()` function, to prevent it from returning malicious or misleading data. Consider adding a mechanism to update or disable the `launcher` address if it becomes compromised.


### `L-01` — Unconventional Use of tokenURI for ERC-20  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `tokenURI()` function is typically associated with ERC-721 or ERC-1155 NFTs, where it provides metadata for a specific `tokenId`. In this ERC-20 contract, `tokenURI()` returns metadata based on the contract's own address, not a token ID. While not a direct security vulnerability, this architectural choice (7.1) is unconventional for an ERC-20 and may lead to confusion or misinterpretation by platforms and users expecting ERC-721/1155 behavior or standard ERC-20 metadata practices.

**Recommendation:** Clearly document the intended purpose and usage of the `tokenURI()` function for the StonkToken. If the goal is general token metadata, consider if a different approach (e.g., off-chain metadata linked to the contract address) would be less ambiguous. If it's intended for specific platform integration, ensure that platform understands this unique implementation.


### `I-01` — Centralization of Initial Token Supply  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). During contract deployment, the entire `totalSupply_` is minted to the `launcher_` address. This design choice (7.4) means that the `launcher` address holds 100% of the initial token supply. While this is a valid design pattern, it implies significant control by the `launcher` over the token's initial distribution and market dynamics. Any compromise of the `launcher` address could lead to a large-scale token dump.

**Recommendation:** Ensure the `launcher` address is secured with robust measures, such as a hardware wallet or a multi-signature setup. If the intention is to distribute tokens, a clear and transparent distribution plan should be communicated to the community. Consider implementing time-locks or vesting schedules for large token holdings if appropriate for the project's tokenomics.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5ab0...80f5`](https://basescan.org/address/0x5ab000ff9b9ffe0349ce5ffa5fd86f217c3680f5) |
| **Network** | Base |
| **Price** | $0.00231 |
| **24h Volume** | $654.4K |
| **Liquidity** | $191.7K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 5d |
| **Top-10 Holders** | 29.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 867 buys / 699 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x7692acc1cdd771d09ebcae3663e1843b2911bec7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-stonks-exchange-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

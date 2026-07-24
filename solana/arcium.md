---
token: Arcium
ticker: ARX
network: solana
risk_score: 77
status: critical
date: 2026-06-23
---

# Arcium (ARX) — Smart Contract Security Analysis | Solana

> **Risk Score: 77/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arcium-sol)

---

## Audit Summary

The Arcium (ARX) SPL token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, its metadata is mutable, allowing changes to the token's name, symbol, or image post-launch. Holder distribution data was unavailable from chain-native RPC.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the metadata (name, symbol, image) aligns with current expectations, as it can be changed by an authority. Monitor the token's official communication channels for any announcements regarding metadata updates. Be aware that while direct holder distribution percentages were unavailable, third-party signals suggest high ownership concentration, which could impact market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Arcium (ARX) token is an SPL token operating under the `spl-token` program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing… |
| **Governance / Economics** | 1/10 | High | The token exhibits a healthy liquidity of $300,907 USD, with a very low 24-hour volume of $98 USD, resulting in a normal Volume/Liquidity Ratio of 0.00. The DEX pair has been active for 18 days… |
| **Upgrades** | 5/10 | Medium | The mint authority and freeze authority are both revoked, meaning the token's supply is fixed and accounts cannot be frozen. The token does not utilize Token-2022 extensions that introduce… |

## Security Findings

_🟢 1 Low_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata is mutable, meaning its name, symbol, or image can be changed post-launch. This introduces a risk of misrepresentation or rebranding without explicit holder consent.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ARXwZk...DrFs`](https://solscan.io/account/ARXwZkNAtzPfdcoqQiduJn8EPv9fKiDfGn2KyggyDrFs) |
| **Network** | Solana |
| **Price** | $0.1595 |
| **24h Volume** | $323 |
| **Liquidity** | $301.0K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 22h |
| **Top-10 Holders** | 92.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2891 buys / 3325 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Arcium a scam?

Based purely on the provided data, labeling Arcium (ARX) definitively as a "scam" is premature. While it exhibits positive traits like renounced ownership and no mint function, critical red flags exist. The contract is unverified, liquidity is unlocked, and a concerning 94.8% of the supply is concentrated among the top 10 holders. These factors contribute to its overall high-risk score of 63/100, indicating significant vulnerabilities that could be exploited.

### Is Arcium safe to buy?

Arcium (ARX) is assessed with a high-risk score of 63/100, indicating it is not considered safe for investment based on the current data. Key risk factors include the contract being unverified, extreme token concentration with 94.8% held by the top 10 wallets, and unlocked liquidity. These conditions create significant potential for market manipulation or sudden liquidity withdrawal. Investors should exercise extreme caution and be aware of these inherent volatilities.

### Has Arcium been audited?

No, the Arcium (ARX) contract has not been verified. Contract verification is a crucial first step for any public audit, as it allows external security firms and the community to scrutinize the underlying code for vulnerabilities or malicious functions. Without verification, there is no public access to the contract's source code, making it impossible to confirm its integrity or audit its security.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/frrzset56fhgmrumaewsc5ql1wfzecmfs2stuypayjvw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arcium-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-23*

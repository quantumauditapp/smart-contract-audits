---
token: Meteora
ticker: MET
network: solana
risk_score: 38
status: medium
date: 2026-06-21
---

# Meteora (MET) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meteora-sol)

---

## Audit Summary

The Meteora (MET) SPL token mint exhibits a low-risk profile with both mint and freeze authorities revoked, ensuring a fixed supply and unfreezable accounts. The primary concern identified is the mutability of its metadata, which allows for changes to branding post-launch. Holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** Before engaging with the Meteora (MET) token, holders should verify the current metadata (name, symbol, image) directly on-chain to ensure it aligns with their expectations and any off-chain branding. Monitor for any unexpected changes to the token's metadata, as this is the only identified mutable aspect. Continue to monitor market data for holder concentration if it becomes available, as this could impact price stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is implemented using the standard `spl-token` program. Both the mint authority and freeze authority have been revoked, which means no new tokens can be minted and no holder accounts can be… |
| **Governance / Economics** | 5/10 | Medium | The token demonstrates healthy market activity with over $51 million in DEX liquidity and a 24-hour volume of $157,839, resulting in a normal Volume/Liquidity Ratio of 0.00. The DEX pair has been… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, preventing any future changes to the token's supply or account freeze status. The underlying `spl-token` program is not subject to… |

## Security Findings

_🟢 1 Low_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata is mutable, as indicated by `metadata_mutable: True`. This means the token name, symbol, or image can be changed post-launch by an authorized party.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`METvsv...mWQL`](https://solscan.io/account/METvsvVRapdj9cFLzq4Tr43xK4tAjQfwX76z3n6mWQL) |
| **Network** | Solana |
| **Price** | $887.2900 |
| **24h Volume** | $178.5K |
| **Liquidity** | $332.61M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 68.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 273 buys / 261 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Meteora a scam?

Meteora carries a high-risk score of 56/100 based on available data. While ownership is renounced and no new tokens can be minted, significant concerns exist. The contract is unverified, meaning its code cannot be publicly scrutinized for vulnerabilities or hidden functions. Additionally, 68% of the supply is concentrated in the top 10 wallets, raising centralization risks. These factors warrant extreme caution.

### Is Meteora safe to buy?

Meteora is classified with a high-risk score of 56/100, suggesting it is not inherently safe to buy without significant due diligence. Key risk factors include an unverified contract, which prevents independent security audits, and highly centralized holdings, with 68.0% of the supply controlled by the top ten wallets. Additionally, the substantial liquidity, while impressive, is not locked, adding to potential vulnerabilities.

### Has Meteora been audited?

Based on the provided information, the Meteora contract is unverified. This means its source code has not been published and confirmed to match the deployed code on the blockchain. Without contract verification, a comprehensive security audit by independent third parties is practically impossible to conduct or validate, significantly increasing the uncertainty regarding its integrity.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/huprxabcjqyrhj6scpqxua6qqjss2ia1txmeeuvwphog)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meteora-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-21*

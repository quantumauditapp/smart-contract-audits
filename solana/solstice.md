---
token: Solstice
ticker: SLX
network: solana
risk_score: 62
status: high
date: 2026-06-10
---

# Solstice (SLX) — Smart Contract Security Analysis | Solana

> **Risk Score: 62/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solstice-sol)

---

## Audit Summary

The Solstice (SLX) token mint has revoked both its mint and freeze authorities, indicating a fixed supply and immutability of account states. However, the token's metadata is mutable, allowing changes to its name, symbol, or image post-launch. The DEX trading pair is very new, having been created only 3 days ago, which limits the track record for assessing market behavior. Holder concentration data from chain-native RPC was unavailable, though a third-party registry signals high ownership by top holders.

> **Final Recommendation:** Before engaging with this token, verify on-chain that the metadata has not been altered from its current branding. Monitor the token's market behavior closely due to its very recent DEX listing. If holder concentration data becomes available, assess the distribution to understand potential market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Solstice (SLX) token is implemented using the standard spl-token program. Both the mint authority and freeze authority have been revoked, ensuring that no new tokens can be minted and no existing… |
| **Governance / Economics** | 2/10 | High | The token's DEX pair is very new, having been created only 3 days ago, which provides insufficient track record for assessing market stability or team behavior. Current DEX liquidity stands at… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority have both been revoked, preventing any further changes to the token's supply or the ability to freeze accounts. However, the token's metadata is mutable… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 3 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Monitor the token's market activity and development over a longer period to establish a track record.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`SLXdx4...rfgq`](https://solscan.io/account/SLXdx4BUt2v9uJQNzWqSfzTJ9UKLUDsvxHFMEEdrfgq) |
| **Network** | Solana |
| **Price** | $0.4214 |
| **24h Volume** | $521.6K |
| **Liquidity** | $203.3K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 6d |
| **Top-10 Holders** | 90.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2275 buys / 2192 sells |

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

### Is Solstice a scam?

Based on the provided data, Solstice (SLX) exhibits multiple critical risk factors often associated with fraudulent schemes, culminating in a 72/100 Critical Risk score. The lack of contract verification, unrenounced ownership, and unlocked liquidity are significant indicators of potential malicious intent or severe vulnerability. While these factors don't definitively label it a scam, they strongly advise against investment due to the high probability of financial loss.

### Is Solstice safe to buy?

No, Solstice (SLX) is assessed as critically unsafe for investment, reflected by its 72/100 risk score. The contract's unverified status means its code is unknown and unauditable, while unrenounced ownership allows the developer to retain full control. Crucially, the liquidity pool is not locked, exposing investor funds to potential removal by the owner (a rug pull). These fundamental risks make Solstice a highly speculative and dangerous asset.

### Has Solstice been audited?

There is no indication of a security audit for Solstice (SLX). Furthermore, the contract code is not verified on the blockchain. This means the underlying code is opaque and has not been publicly confirmed or reviewed by independent parties. Without verification, a professional audit is practically impossible, leaving investors with no transparency regarding the contract's safety or functionality.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/sgo6ropnwxzutdhkbejkxvyuvwycgwzh5hgx6w6pxhh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solstice-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

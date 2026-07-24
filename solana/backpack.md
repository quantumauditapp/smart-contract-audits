---
token: Backpack
ticker: BP
network: solana
risk_score: 100
status: critical
date: 2026-06-14
---

# Backpack (BP) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/backpack-sol)

---

## Audit Summary

This audit identifies critical risks due to active Mint and Freeze authorities, both held by `GySFHFS5ZiN4Z5YnyPZcjjxpYcGvD7qHZYVjE9QzMHVH`, allowing for unlimited token minting and account freezing. Additionally, token metadata is mutable, enabling post-launch changes to branding. Holder distribution data was unavailable from chain-native RPC for a complete assessment of concentration risk.

> **Final Recommendation:** Before engaging with this token, holders should verify on-chain that the Mint Authority has been permanently revoked to ensure the token supply is fixed. Similarly, confirm the Freeze Authority is nullified to prevent any potential confiscation of funds. It is also advisable to monitor the token's metadata for any unexpected alterations to its name, symbol, or image.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 2/10 | High | The token is implemented using the classic `spl-token` program (v3). A critical concern is the active Mint Authority, `GySFHFS5ZiN4Z5YnyPZcjjxpYcGvD7qHZYVjE9QzMHVH`, which allows for arbitrary… |
| **Governance / Economics** | 1/10 | High | The token exhibits healthy market activity with a total DEX liquidity of $2,161,273 and a 24-hour volume of $813,689. The Volume/Liquidity Ratio is 0.38, indicating normal trading patterns, and the… |
| **Upgrades** | 3/10 | High | The Mint Authority and Freeze Authority remain active, allowing for potential future changes to the token's supply and the state of holder accounts. Additionally, the token's metadata is mutable… |

## Security Findings

_🔴 2 Critical · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is GySFHFS5ZiN4Z5YnyPZcjjxpYcGvD7qHZYVjE9QzMHVH. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. (Fact: Mint Authority: GySFHFS5ZiN4Z5YnyPZcjjxpYcGvD7qHZYVjE9QzMHVH)

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is GySFHFS5ZiN4Z5YnyPZcjjxpYcGvD7qHZYVjE9QzMHVH. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds. (Fact: Freeze Authority: GySFHFS5ZiN4Z5YnyPZcjjxpYcGvD7qHZYVjE9QzMHVH)

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch. (Fact: metadata_mutable: True)

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BPxxfR...jPCy`](https://solscan.io/account/BPxxfRCXkUVhig4HS1Lh7kZqV6SPJhzfEk4x6fVBjPCy) |
| **Network** | Solana |
| **Price** | $0.4674 |
| **24h Volume** | $190.4K |
| **Liquidity** | $2.14M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 98.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1148 buys / 700 sells |

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

### Is Backpack a scam?

Backpack (BP) shows critical risk factors. The contract is unverified, lacking transparency for investors. A staggering 99.0% of supply is held by the top 10 wallets, indicating extreme centralization risk. Crucially, liquidity is not locked, posing a clear withdrawal risk. While ownership is renounced and new tokens cannot be minted, these combined factors contribute to its 'High Risk' assessment.

### Is Backpack safe to buy?

No, Backpack (BP) is not safe to buy, indicated by its High Risk score of 58/100. Core issues include its unverified contract, which lacks transparency for investors. A critical 99.0% of the supply is controlled by the top 10 holders, posing extreme centralization risk. Crucially, liquidity is not locked, meaning it can be withdrawn. These factors make it highly speculative and risky.

### Has Backpack been audited?

No, the Backpack (BP) contract is unverified. Its deployed code isn't publicly matched against source code. Therefore, an independent security audit cannot be publicly confirmed. This lack of transparency prevents investors from assessing the contract's safety, significantly contributing to its high-risk profile.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/6qz7thwqvcjf3hydglukalbuk6eyjkezxzmwlaeiwfjd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/backpack-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-14*

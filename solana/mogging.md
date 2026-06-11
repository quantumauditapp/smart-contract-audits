---
token: mogging
ticker: MOGGING
network: solana
risk_score: 41
status: medium
date: 2026-06-10
---

# mogging (MOGGING) — Smart Contract Security Analysis | Solana

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mogging-sol)

---

## Audit Summary

This audit of the mogging SPL Token Mint found no critical or high-severity risks based on the provided on-chain data and external security signals. Key authorities such as mint and freeze are revoked, and no Token-2022 extensions posing significant risks are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available data, the mogging token mint appears to have a robust security posture with no identified critical or high-severity vulnerabilities. The revocation of mint and freeze authorities significantly reduces centralisation risk. Holders should note that holder concentration data was not available, so a manual check of top holders might be prudent if this is a concern. For enhanced due diligence, consider a Premium Deploy option to conduct deeper analysis into the token's ecosystem and community.

## Security Analysis

This audit of the mogging SPL Token Mint found no critical or high-severity risks based on the provided on-chain data and external security signals. Key authorities such as mint and freeze are revoked, and no Token-2022 extensions posing significant risks are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

Based on the available data, the mogging token mint appears to have a robust security posture with no identified critical or high-severity vulnerabilities. The revocation of mint and freeze authorities significantly reduces centralisation risk. Holders should note that holder concentration data was not available, so a manual check of top holders might be prudent if this is a concern. For enhanced due diligence, consider a Premium Deploy option to conduct deeper analysis into the token's ecosystem and community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, as confirmed by RPC data, indicating that no single entity can mint new tokens or freeze existing h |
| **Governance / Economics** | 6/10 | Low | DEX liquidity for the token is $52,842, which is above the very low liquidity threshold. The 24-hour volume is $8,484, resulting in a healthy Volume/Liquidity Ratio of 0.16, not indicative of wash tra |
| **Upgrades** | 6/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's core parameters cannot be altered by an external key. The token utilizes the spl-token-2022 program, but no specific exten |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5oq4zK...pump`](https://solscan.io/account/5oq4zKetRkUMMrFtkWH7r1Q6HZJMsTjgCeU6isgYpump) |
| **Network** | Solana |
| **Price** | $0.0003518 |
| **24h Volume** | $165.5K |
| **Liquidity** | $57.3K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 27.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 860 buys / 750 sells |

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

### Is mogging a scam?

Based on the available data, mogging exhibits several high-risk characteristics. The unverified contract, unrenounced ownership, and unlocked liquidity are significant red flags. While the data doesn't definitively label it a scam, these elements create a high potential for developer-induced issues or asset withdrawal, warranting extreme caution. Investors should be aware of these fundamental security gaps.

### Is mogging safe to buy?

Mogging is currently classified as 'High Risk' with a score of 61/100, indicating it is not safe for most investors. Key risks include the contract not being verified, unrenounced ownership allowing potential developer manipulation, and unlocked liquidity exposing funds to potential rug pulls. These factors collectively highlight significant vulnerabilities, suggesting investors face substantial security risks when considering this token.

### Has mogging been audited?

The mogging contract is reported as 'not verified.' This means its code has not been published and confirmed on the blockchain. Without verification, assessing its functionality or security through an audit is severely hampered. Investors cannot independently inspect the contract, posing a significant transparency and trust risk.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5gjuboxlt8te68gvoaxttsx6pwfw1uzlsvhcp35esyxz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mogging-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

---
token: LMAO!
ticker: LMAO!
network: solana
risk_score: 70
status: high
date: 2026-06-10
---

# LMAO! (LMAO!) — Smart Contract Security Analysis | Solana

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lmao-sol)

---

## Audit Summary

The LMAO! SPL token mint audit reveals a critical operational risk due to its default frozen account state, requiring manual unfreezing for new holders. While mint and freeze authorities are revoked, and metadata is immutable, the lack of holder concentration data prevents a full assessment of economic centralization risks. RugCheck.xyz provides a low risk score of 1/100, but the default frozen state remains a significant concern for user experience and accessibility.

> **Final Recommendation:** Holders should be aware that new token accounts for LMAO! are created in a frozen state, making them unspendable until an authorized party explicitly unfreezes them. It is crucial to confirm the availability and responsiveness of the issuer or an active authority to perform this unfreezing operation. Without this, newly acquired tokens may be inaccessible. Additionally, while liquidity is reasonable, the absence of holder concentration data means potential risks from large holders cannot be fully evaluated. For enhanced security and operational control, consider a Premium Deploy option that allows for custom configuration of default account states and provides transparent holder distribution metrics.

## Security Analysis

The LMAO! SPL token mint audit reveals a critical operational risk due to its default frozen account state, requiring manual unfreezing for new holders. While mint and freeze authorities are revoked, and metadata is immutable, the lack of holder concentration data prevents a full assessment of economic centralization risks. RugCheck.xyz provides a low risk score of 1/100, but the default frozen state remains a significant concern for user experience and accessibility.

Holders should be aware that new token accounts for LMAO! are created in a frozen state, making them unspendable until an authorized party explicitly unfreezes them. It is crucial to confirm the availability and responsiveness of the issuer or an active authority to perform this unfreezing operation. Without this, newly acquired tokens may be inaccessible. Additionally, while liquidity is reasonable, the absence of holder concentration data means potential risks from large holders cannot be fully evaluated. For enhanced security and operational control, consider a Premium Deploy option that allows for custom configuration of default account states and provides transparent holder distribution metrics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 2/10 | High | The LMAO! token is an SPL token operating on the Solana blockchain, utilizing the standard `spl-token` program. Both the mint authority and freeze authority have been successfully revoked, indicating  |
| **Governance / Economics** | 2/10 | Medium | The token exhibits a healthy liquidity of $261,633 USD on DEXs, with a 24-hour volume of $169,130 USD, resulting in a normal volume/liquidity ratio of 0.65. The DEX pair has been active for 236 days,  |
| **Upgrades** | 1/10 | Low | The LMAO! token mint has a robust configuration regarding mutability and upgrades. Both the mint authority and freeze authority have been revoked, preventing any future changes to the token supply or  |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority. This is indicated by `GoPlus.default_account_state: 1`.

**Recommendation:** Confirm an active issuer is available to unfreeze accounts; otherwise the token is unspendable.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H74CYm...pump`](https://solscan.io/account/H74CYmXgMkYHYuSRsZt6RJb4NYp2u72Vw8BS5huApump) |
| **Network** | Solana |
| **Price** | $0.002858 |
| **24h Volume** | $362.8K |
| **Liquidity** | $249.3K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 23.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

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

## Sources

- [View on DexScreener](https://dexscreener.com/solana/afayrfh7huynkv5mbvbnrhwx29m9jzul3ysgtqz69auv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lmao-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

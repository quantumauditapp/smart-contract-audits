---
token: US BLACKWHALE COIN
ticker: USBC
network: solana
risk_score: 41
status: medium
date: 2026-06-15
---

# US BLACKWHALE COIN (USBC) — Smart Contract Security Analysis | Solana

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-blackwhale-coin-sol)

---

## Audit Summary

This audit of the US BLACKWHALE COIN (USBC) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and deterministic rules. The mint and freeze authorities are revoked, and no Token-2022 extensions posing significant risks (like transfer hooks or permanent delegates) are active. Holder concentration data was unavailable, and while the RugCheck score is very low (1/100), it does not trigger a specific 'Rugged' verdict finding under our deterministic rules.

> **Final Recommendation:** Based on the available on-chain data and deterministic rules, the USBC token mint presents a low technical risk profile, primarily due to the revocation of mint and freeze authorities and the absence of risky Token-2022 extensions. However, the RugCheck score of 1/100 is a significant external signal that warrants extreme caution, despite not triggering a specific 'Rugged' finding under our strict rules. Investors should conduct thorough due diligence beyond on-chain metadata, including researching the project team, community sentiment, and the reasons behind the low RugCheck score, before engaging with this token. If holder concentration data becomes available, it should be reviewed to assess potential market manipulation risks. For premium deployments, consider integrating real-time RugCheck API monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.2 Code Security: The USBC token is implemented using the modern spl-token-2022 program, indicating support for advanced features. 7.3 Access Control: Crucially, both the mint auth |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic: The token has a total DEX liquidity of $14,121, which is moderate and does not trigger a 'Very Low Liquidity' warning. The 24-hour volume to liquidity ratio is 0.61, which is considered  |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority is revoked, meaning the token supply cannot be increased, providing certainty for holders. The token uses the spl-token-2022 program, which supports various extensions |

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
| **Contract** | [`EA6jvQ...pump`](https://solscan.io/account/EA6jvQhjR2iMkRaVy9P9drM2ExowaFZWGn3Uo8FPpump) |
| **Network** | Solana |
| **Price** | $0.0002945 |
| **24h Volume** | $401.9K |
| **Liquidity** | $58.6K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 3d |
| **Top-10 Holders** | 31.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7852 buys / 6185 sells |

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

### Is US BLACKWHALE COIN a scam?

While ownership is renounced and no mint function exists, these positives are overshadowed by critical red flags. The unverified contract means the code's true nature is unknown, and unlocked liquidity allows for potential removal, both common traits in scam projects. The high-risk score of 46/100 indicates significant concerns, advising extreme caution rather than labeling it definitively.

### Is US BLACKWHALE COIN safe to buy?

Based on the available data, USBC is not considered safe for investment. The contract remains unverified, preventing transparency and auditability. Critically, liquidity is not locked, which means it could be removed by providers, leading to a potential rug pull. Furthermore, concentrated holdings by the top 10 wallets introduce additional market manipulation risk.

### Has US BLACKWHALE COIN been audited?

No, a thorough security audit of USBC is not publicly verifiable because its contract has not been verified. Without a verified contract, the underlying code is not transparently available for review by auditors or the public. This makes independent assessment of its security, functionality, and adherence to claimed features impossible.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/e98eyybmtmbkxwycnrdbcdkj6hfas3hzxg2lkdq1htd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-blackwhale-coin-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-15*

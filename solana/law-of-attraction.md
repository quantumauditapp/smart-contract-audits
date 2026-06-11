---
token: Law Of Attraction
ticker: LOA
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# Law Of Attraction (LOA) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/law-of-attraction-sol)

---

## Audit Summary

The Law Of Attraction (LOA) token mint shows no critical or high-severity risks based on available on-chain data and external security signals. Key authorities like mint and freeze are revoked, and no Token-2022 extensions posing immediate risks are active. Holder concentration data was unavailable, and RugCheck flagged "Top 10 holders high ownership" without a "RUGGED" verdict.

> **Final Recommendation:** Based on the available on-chain data, the Law Of Attraction (LOA) token mint appears to have a low-risk profile regarding its core token mechanics. Both mint and freeze authorities are revoked, which is a strong positive indicator for supply and account security. No concerning Token-2022 extensions are active, and metadata is immutable. Users can verify these authority revocations on-chain before interacting with the token. 

However, holder concentration data was unavailable from direct RPC queries, and RugCheck flagged "Top 10 holders high ownership" and "High holder correlation." While not triggering a critical finding in this audit, this suggests a potential for market manipulation or significant price impact from large holders. Users should consider this aspect and the general market dynamics before engaging with the token. For a premium deployment, ensure comprehensive liquidity p…

## Security Analysis

The Law Of Attraction (LOA) token mint shows no critical or high-severity risks based on available on-chain data and external security signals. Key authorities like mint and freeze are revoked, and no Token-2022 extensions posing immediate risks are active. Holder concentration data was unavailable, and RugCheck flagged "Top 10 holders high ownership" without a "RUGGED" verdict.

Based on the available on-chain data, the Law Of Attraction (LOA) token mint appears to have a low-risk profile regarding its core token mechanics. Both mint and freeze authorities are revoked, which is a strong positive indicator for supply and account security. No concerning Token-2022 extensions are active, and metadata is immutable. Users can verify these authority revocations on-chain before interacting with the token. 

However, holder concentration data was unavailable from direct RPC queries, and RugCheck flagged "Top 10 holders high ownership" and "High holder correlation." While not triggering a critical finding in this audit, this suggests a potential for market manipulation or significant price impact from large holders. Users should consider this aspect and the general market dynamics before engaging with the token. For a premium deployment, ensure comprehensive liquidity p…

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is an SPL Token-2022 mint (7.1 Architecture). Its mint authority is revoked (7.3 Access Control), preventing further token creation and supply dilution. The freeze authority is also revoked  |
| **Governance / Economics** | 10/10 | Low | The token has a liquidity of $155,548 USD and a 24-hour volume of $222,714 USD, resulting in a normal Volume/Liquidity Ratio of 1.43 (7.4 Economic). The DEX pair is 18 days old, providing some track r |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the core parameters of the token supply and account control cannot be changed (7.7 Upgrades). The token is an SPL Token-2022, but no u |

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
| **Contract** | [`EhHyfj...pump`](https://solscan.io/account/EhHyfjRwj2jhmSE7GW5uJfizaLcNDa5C4HWPiSqjpump) |
| **Network** | Solana |
| **Price** | $0.003599 |
| **24h Volume** | $855.4K |
| **Liquidity** | $140.0K |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 13d |
| **Top-10 Holders** | 61.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5537 buys / 4489 sells |

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

### Is Law Of Attraction a scam?

Based on the available data, Law Of Attraction exhibits several high-risk characteristics, including an unverified contract, unrenounced ownership, and unlocked liquidity. These factors indicate potential vulnerabilities and central control. While a "scam" determination is subjective, these red flags suggest a significant risk profile for investors, warranting extreme caution before engagement.

### Is Law Of Attraction safe to buy?

Law Of Attraction is classified with a high-risk score of 62/100. It is not considered safe due to critical risk factors such as an unverified contract, meaning its code is not publicly auditable, and unrenounced ownership, which leaves significant control with the deployer. Additionally, its unlocked liquidity exposes investors to potential withdrawal risks.

### Has Law Of Attraction been audited?

The provided data indicates that the Law Of Attraction contract is currently unverified. This means its code has not been published or independently reviewed on the blockchain explorer, which is a prerequisite for security audits. Therefore, there is no public information to confirm whether a formal security audit has been conducted or completed.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/enymbpwxnvj7ebav3d9stticmidtm658lorfqvlwvscf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/law-of-attraction-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

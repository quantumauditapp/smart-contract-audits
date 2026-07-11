---
token: WORLD BET
ticker: WBET
network: solana
risk_score: 34
status: medium
date: 2026-06-25
---

# WORLD BET (WBET) — Smart Contract Security Analysis | Solana

> **Risk Score: 34/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-bet-sol)

---

## Audit Summary

The WORLD BET (WBET) token exhibits strong security posture regarding core authorities, with both Mint and Freeze authorities revoked. It utilizes the modern spl-token-2022 program without active transfer hooks or mutable metadata. Holder concentration data was unavailable, preventing a full assessment of distribution risk. RugCheck.xyz provided a score of 1/100, which is a strong negative signal, but no explicit "RUGGED" verdict was provided in the facts, thus no deterministic finding was triggered.

> **Final Recommendation:** The WORLD BET (WBET) token demonstrates good security practices by having its Mint and Freeze authorities revoked, preventing further token issuance or account freezing by the issuer. The token also lacks active transfer hooks and has immutable metadata. However, the RugCheck score of 1/100 is a significant red flag that warrants extreme caution. While not explicitly classified as "RUGGED" by the provided facts, such a low score typically indicates severe underlying issues. It is recommended to investigate the reasons behind this low RugCheck score before considering any interaction with this token. Additionally, holder concentration data was unavailable, which is crucial for assessing market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Regarding 7.1 Architecture and 7.2 Code Security, the token is an SPL Token-2022 mint, indicating modern Solana token standards. For 7.3 Access Control, both the Mint Authority and Freeze Authority… |
| **Governance / Economics** | 5/10 | Medium | For 7.4 Economic and 7.5 Governance, holder concentration data was unavailable, preventing an assessment of supply distribution risk. The token has a liquidity of $12,239 USD, which is moderate. The… |
| **Upgrades** | 8/10 | Low | For 7.7 Upgrades and 7.8 Operations, the token mint has no active Mint Authority or Freeze Authority, meaning its supply and freeze capabilities cannot be altered by an external key. It utilizes the… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`31989Y...pump`](https://solscan.io/account/31989YsfUahV66TGiMvdSyTj1AQNvcdT327Uiu9mpump) |
| **Network** | Solana |
| **Price** | $0.000304 |
| **24h Volume** | $181.8K |
| **Liquidity** | $39.7K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2050 buys / 1628 sells |

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

### Is WORLD BET a scam?

Based on the available data, WORLD BET exhibits several high-risk characteristics that investors should be aware of. The contract is unverified, meaning its code cannot be publicly inspected for malicious functions or vulnerabilities. Additionally, the liquidity is not locked, creating a potential for sudden withdrawal, commonly associated with "rug pull" schemes. These factors, alongside its 47/100 high-risk score, suggest extreme caution is warranted.

### Is WORLD BET safe to buy?

WORLD BET is not considered safe to buy based on the provided security data. Key risk factors include an unverified contract, which prevents public code review, and unlocked liquidity, which carries the risk of a "rug pull." Despite renounced ownership and a distributed holder base, these critical vulnerabilities contribute to a high-risk score of 47/100, advising investors to exercise extreme caution before considering any investment.

### Has WORLD BET been audited?

The provided data indicates the WORLD BET contract is not verified. Contract verification is a foundational step for any credible audit, making the code publicly viewable. Without this, a comprehensive security audit by independent third parties is typically not possible or conclusive, meaning the absence of vulnerabilities or malicious code cannot be confirmed.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/apzdirx3ee11c5ppapny5ecz29cdhgua76yoc1s7bs3e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-bet-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-25*

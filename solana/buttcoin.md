---
token: Buttcoin
ticker: BUTTCOIN
network: solana
risk_score: 19
status: low
date: 2026-06-26
---

# Buttcoin (BUTTCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/buttcoin-sol)

---

## Audit Summary

The Buttcoin SPL Token Mint (Cm6fNnMk7NfzStP9CZpsQA2v3jjzbcYGAxdJySmHpump) demonstrates a robust configuration with both mint and freeze authorities revoked, limiting central control. Liquidity is substantial, and trading volume appears normal. However, a very low RugCheck score of 1/100 indicates significant external risk, despite no specific deterministic findings being triggered by the audit rules. Holder concentration data was unavailable.

> **Final Recommendation:** Based on the on-chain facts and deterministic rules, the Buttcoin token mint appears to have a secure configuration with no active central authorities. However, the extremely low RugCheck score of 1/100 is a critical external signal (7.6 External) that warrants immediate and thorough investigation. Holders should understand the implications of this score, which often points to developer history or LP movements, before engaging with the token. A Premium Deploy option would involve a deeper dive into the RugCheck data and any associated off-chain information to fully understand the flagged risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Buttcoin SPL Token Mint (Cm6fNnMk7NfzStP9CZpsQA2v3jjzbcYGAxdJySmHpump) is configured using the spl-token-2022 program (7.1 Architecture). Both the mint authority and freeze authority have been rev |
| **Governance / Economics** | 7/10 | Low | The token exhibits a healthy liquidity of $737,207 USD with a 24-hour volume of $564,674 USD, resulting in a normal volume/liquidity ratio of 0.77 (7.4 Economic). The DEX pair has been active for 171  |
| **Upgrades** | 8/10 | Low | The token's core authorities, including mint and freeze, have been permanently revoked (7.7 Upgrades), ensuring no further changes to supply or account status by a central party. Key Token-2022 extens |

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
| **Contract** | [`Cm6fNn...pump`](https://solscan.io/account/Cm6fNnMk7NfzStP9CZpsQA2v3jjzbcYGAxdJySmHpump) |
| **Network** | Solana |
| **Price** | $0.01732 |
| **24h Volume** | $495.2K |
| **Liquidity** | $740.4K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 15.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2257 buys / 2524 sells |

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

### Is Buttcoin a scam?

Based on the data, it's not possible to definitively label Buttcoin as a scam, but significant red flags exist. The contract is unverified, meaning its underlying code is opaque, and liquidity is unlocked, creating 'rug pull' potential. While ownership is renounced and no mint function exists, these critical vulnerabilities warrant extreme caution, aligning with a medium risk assessment.

### Is Buttcoin safe to buy?

Buttcoin is not considered safe for investment due to critical risks. Its contract is unverified, blocking independent security audits and transparency. More importantly, liquidity is not locked, exposing investors to a 'rug pull' risk. These fundamental vulnerabilities, contributing to its medium risk score of 34/100, mean capital loss is a significant possibility.

### Has Buttcoin been audited?

No, Buttcoin's contract is unverified on-chain. This means its code cannot be publicly inspected for vulnerabilities or malicious functions. Without contract verification, a meaningful security audit is impossible, leaving investors with no independent assurance regarding the contract's safety or integrity.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/ffcygssgwhfora9rxxka48p8yfoz8tsw85jpo3cqhdys)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/buttcoin-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-26*

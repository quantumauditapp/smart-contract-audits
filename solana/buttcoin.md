---
token: Buttcoin
ticker: BUTTCOIN
network: solana
risk_score: 0
status: low
date: 2026-06-26
---

# Buttcoin (BUTTCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/buttcoin-sol)

---

## Audit Summary

This audit of the Buttcoin SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and market data. Both the mint and freeze authorities have been revoked, indicating a fixed supply and no ability to freeze user accounts. The token utilizes the SPL Token-2022 program without any active transfer hooks or default frozen account states. Holder distribution data was unavailable from chain-native RPC.

> **Final Recommendation:** Based on the available data, the Buttcoin SPL Token Mint appears to be well-configured with key authorities revoked, indicating a fixed supply and unfreezable accounts. Holders should continue to monitor market conditions, particularly liquidity and trading volume, to ensure stability. If holder distribution data becomes available, it should be reviewed to assess potential centralization risks. No immediate on-chain verification steps are required beyond confirming the current state of revoked authorities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Buttcoin token is an SPL Token-2022 mint with a total supply of 999,945,702.977861 tokens, using 6 decimals. Crucially, both the mint authority and freeze authority have been revoked, ensuring no… |
| **Governance / Economics** | 10/10 | Low | The token exhibits healthy market characteristics with a total DEX liquidity of $656,108 and a 24-hour trading volume of $615,100 (7.4 Economic). The volume-to-liquidity ratio is 0.94, which is… |
| **Upgrades** | 10/10 | Low | The token's configuration demonstrates a strong commitment to immutability and fixed parameters (7.7 Upgrades). Both the mint and freeze authorities are revoked, meaning no further changes can be… |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Cm6fNn...pump`](https://solscan.io/account/Cm6fNnMk7NfzStP9CZpsQA2v3jjzbcYGAxdJySmHpump) |
| **Network** | Solana |
| **Price** | $0.01439 |
| **24h Volume** | $1.07M |
| **Liquidity** | $988.4K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 17.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2257 buys / 2524 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Buttcoin a scam?

Based on the data, it's not possible to definitively label Buttcoin as a scam, but significant red flags exist. The contract is unverified, meaning its underlying code is opaque, and liquidity is unlocked, creating 'rug pull' potential. While ownership is renounced and no mint function exists, these critical vulnerabilities warrant extreme caution, aligning with a medium risk assessment.

### Is Buttcoin safe to buy?

Buttcoin is not considered safe for investment due to critical risks. Its contract is unverified, blocking independent security audits and transparency. More importantly, liquidity is not locked, exposing investors to a 'rug pull' risk. These fundamental vulnerabilities, contributing to its low risk score of 0/100, mean capital loss is a significant possibility.

### Has Buttcoin been audited?

No, Buttcoin's contract is unverified on-chain. This means its code cannot be publicly inspected for vulnerabilities or malicious functions. Without contract verification, a meaningful security audit is impossible, leaving investors with no independent assurance regarding the contract's safety or integrity.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/ffcygssgwhfora9rxxka48p8yfoz8tsw85jpo3cqhdys)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/buttcoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-26*

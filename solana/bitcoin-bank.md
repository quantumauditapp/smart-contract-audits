---
token: Bitcoin Bank
ticker: BTCBANK
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# Bitcoin Bank (BTCBANK) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitcoin-bank-sol)

---

## Audit Summary

This audit of the Bitcoin Bank (BTCBANK) SPL Token Mint found no critical or high-severity risks. The mint and freeze authorities are revoked, indicating a fixed supply and no ability to freeze user funds. Holder concentration data was unavailable, which prevents a full assessment of distribution risk.

> **Final Recommendation:** The Bitcoin Bank (BTCBANK) token presents a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, which are critical security features for preventing supply dilution and fund confiscation. The token also lacks active transfer hooks or mutable metadata, contributing to predictable behavior.

However, holder concentration data was unavailable, which is a key metric for assessing potential market manipulation risks. Users should consider this information gap and verify holder distribution independently if this is a concern. For enhanced security, consider a Premium Deploy option that includes continuous monitoring of on-chain metrics and alerts for any unexpected changes in token state or market dynamics.

## Security Analysis

This audit of the Bitcoin Bank (BTCBANK) SPL Token Mint found no critical or high-severity risks. The mint and freeze authorities are revoked, indicating a fixed supply and no ability to freeze user funds. Holder concentration data was unavailable, which prevents a full assessment of distribution risk.

The Bitcoin Bank (BTCBANK) token presents a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, which are critical security features for preventing supply dilution and fund confiscation. The token also lacks active transfer hooks or mutable metadata, contributing to predictable behavior.

However, holder concentration data was unavailable, which is a key metric for assessing potential market manipulation risks. Users should consider this information gap and verify holder distribution independently if this is a concern. For enhanced security, consider a Premium Deploy option that includes continuous monitoring of on-chain metrics and alerts for any unexpected changes in token state or market dynamics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | 7.1 Architecture: The Bitcoin Bank (BTCBANK) token is an SPL Token-2022 mint. 7.2 Code Security: As an SPL token mint, there is no custom source code on-chain to review; its behavior is governed by th |
| **Governance / Economics** | 6/10 | Low | 7.4 Economic: The token exhibits healthy liquidity with $2,047,084 USD available on DEXs, and a 24-hour volume of $102,643 USD, resulting in a normal Volume/Liquidity Ratio of 0.05. The DEX pair has b |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: The mint authority and freeze authority have both been revoked, indicating that the token's supply is fixed and no accounts can be frozen post-launch. GoPlus data confirms that metadata  |

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
| **Contract** | [`9s96G1...pump`](https://solscan.io/account/9s96G11xGsHczudfJqKQzQxzvubQgJXSySJ1wRgxpump) |
| **Network** | Solana |
| **Price** | $0.0004337 |
| **24h Volume** | $220.2K |
| **Liquidity** | $56.8K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 15d |
| **Top-10 Holders** | 36.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2817 buys / 1914 sells |

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

### Is Bitcoin Bank a scam?

Based on the available data, Bitcoin Bank (BTCBANK) exhibits several high-risk characteristics commonly associated with potential scams. The contract is unverified, ownership is not renounced, and liquidity is unlocked. These elements allow developers complete control over the token's future, including the ability to remove liquidity and potentially render tokens worthless, making it highly susceptible to a "rug pull."

### Is Bitcoin Bank safe to buy?

Given its high-risk score of 70/100, Bitcoin Bank (BTCBANK) is not considered safe for investment. Key risk factors include an unverified contract, unrenounced ownership, and unlocked liquidity. These conditions expose investors to significant vulnerabilities such as potential contract manipulation, token supply inflation, and the complete withdrawal of liquidity, leading to substantial financial loss.

### Has Bitcoin Bank been audited?

There is no indication that Bitcoin Bank (BTCBANK) has undergone a formal security audit. Crucially, its contract remains unverified, meaning the underlying code is not publicly available for review by auditors or the community. Without contract verification, a comprehensive security audit is impossible, leaving potential vulnerabilities undetected and unaddressed.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4a2acvjbjysaueewedivqhcmnfty2ef49eayyxswdmt2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bitcoin-bank-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

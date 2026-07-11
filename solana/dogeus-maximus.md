---
token: Dogeus Maximus
ticker: DOGEUS
network: solana
risk_score: 43
status: medium
date: 2026-06-10
---

# Dogeus Maximus (DOGEUS) — Smart Contract Security Analysis | Solana

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dogeus-maximus-sol)

---

## Audit Summary

The Dogeus Maximus (DOGEUS) SPL token mint has revoked its mint and freeze authorities, indicating a fixed supply and no ability to freeze user funds. No Token-2022 extensions that introduce centralisation risks, such as transfer hooks or permanent delegates, are active. Holder concentration data was unavailable, and RugCheck.xyz did not flag the token as rugged, resulting in a low overall risk assessment based on the available facts.

> **Final Recommendation:** Based on the available on-chain data and external security signals, the Dogeus Maximus (DOGEUS) token appears to be well-configured from a security perspective, with critical authorities revoked and no risky Token-2022 extensions active. However, holder concentration data was unavailable, which is a key factor for assessing market manipulation risk.
For a comprehensive understanding, it is recommended to monitor holder distribution as this data becomes available. Always exercise caution with new tokens and consider the overall market conditions and project fundamentals beyond the technical configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Dogeus Maximus (DOGEUS) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing  |
| **Governance / Economics** | 5/10 | Medium | The token has a liquidity of $28,870 USD and a 24-hour volume of $206,256 USD. The Volume/Liquidity Ratio is 7.14, which is not indicative of wash trading according to the defined threshold. The DEX p |
| **Upgrades** | 8/10 | Low | The mint authority has been revoked, meaning the token's supply parameters cannot be altered. No Token-2022 extensions that allow for future modifications to core token behavior (e.g., transfer hook u |

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
| **Contract** | [`FeMrhD...pump`](https://solscan.io/account/FeMrhDeddUvuzo25RZriZD6Te8xy3tdyKLLXBhEEpump) |
| **Network** | Solana |
| **Price** | $0.0002051 |
| **24h Volume** | $109.4K |
| **Liquidity** | $43.3K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 10d |
| **Top-10 Holders** | 31.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1636 buys / 1297 sells |

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

### Is Dogeus Maximus a scam?

The provided data indicates several high-risk factors commonly associated with potential malicious projects, such as an unverified contract and unrenounced ownership. While these do not definitively confirm it as a scam, they significantly raise the risk of developer manipulation or a rug-pull, contributing to its high risk score of 68/100. Investors should exercise extreme caution and conduct thorough due diligence.

### Is Dogeus Maximus safe to buy?

Based on the security analysis, Dogeus Maximus presents substantial risks that make it unsafe for typical investment. The contract is unverified, ownership is not renounced, and liquidity is not locked. These factors indicate a high potential for developer manipulation or liquidity withdrawal, resulting in a high risk score of 68/100. Investing under these conditions carries a significant risk of capital loss.

### Has Dogeus Maximus been audited?

The contract for Dogeus Maximus is listed as 'False' for verification, meaning its code has not been publicly confirmed to match the deployed version on the blockchain. This is distinct from a formal security audit by an independent firm, which assesses code for vulnerabilities and security flaws. The current status indicates that no such audit information is available through contract verification.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/eysderowtsftm1x5abw5hwuhrvmv88gozsvdecpar38f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dogeus-maximus-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

---
token: spucex
ticker: SPCX
network: solana
risk_score: 38
status: medium
date: 2026-06-16
---

# spucex (SPCX) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spucex-sol)

---

## Audit Summary

The spucex (SPCX) token mint has no critical authorities enabled, with both mint and freeze authorities revoked. No Token-2022 extensions like transfer hooks or permanent delegates are active. However, holder concentration data was unavailable, preventing a full assessment of supply distribution risk.

> **Final Recommendation:** The spucex (SPCX) token presents a low technical risk profile due to the revocation of critical mint and freeze authorities and the absence of complex Token-2022 extensions. However, the lack of holder concentration data means that potential risks from concentrated supply cannot be fully assessed. Users should also note that RugCheck.xyz assigned a very low score of 1/100, which, while not triggering a specific "RUGGED" verdict per our rules, suggests caution.

For a Premium Deploy option, consider a comprehensive on-chain analysis of the token's transaction history and holder movements to gain insights into supply distribution and potential whale activity, which was unavailable in this report. This would provide a more complete picture of economic risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The spucex (SPCX) token is an SPL Token-2022 mint with address 9qpDk7hGSHqyfMGDT7p4zFQ35aGff248Qes48CgLpump. Both the mint authority and freeze authority have been revoked, meaning no new tokens can b |
| **Governance / Economics** | 5/10 | Medium | The token has a total DEX liquidity of $23,766 (Fact: "Liquidity (USD): $23,766"). The 24-hour trading volume is $28,752, resulting in a healthy Volume/Liquidity Ratio of 1.21, which does not indicate |
| **Upgrades** | 8/10 | Low | The token mint's critical authorities, Mint Authority and Freeze Authority, have been revoked, indicating a fixed supply and unfreezable accounts (Fact: "Mint Authority: revoked (None)", "Freeze Autho |

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
| **Contract** | [`9qpDk7...pump`](https://solscan.io/account/9qpDk7hGSHqyfMGDT7p4zFQ35aGff248Qes48CgLpump) |
| **Network** | Solana |
| **Price** | $0.0002492 |
| **24h Volume** | $324.6K |
| **Liquidity** | $51.4K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 5d |
| **Top-10 Holders** | 34.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3303 buys / 2657 sells |

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

### Is spucex a scam?

While spucex (SPCX) exhibits some positive attributes like renounced ownership and no mint function, critical red flags prevent a definitive 'safe' assessment. The contract is unverified, meaning its code isn't publicly reviewable for safety. Crucially, liquidity is not locked, creating a high risk of a rug pull where funds could be withdrawn. These factors elevate the potential for significant investor risk, though the data doesn't conclusively label it a scam.

### Is spucex safe to buy?

Investing in spucex (SPCX) carries significant risk based on the available data. The primary concerns include the unverified contract, which means its code hasn't been publicly scrutinized for vulnerabilities or malicious functions. Furthermore, the liquidity is not locked, leaving it susceptible to sudden withdrawal by providers, which could drastically impact trading. The concentration of 34.6% of supply among the top 10 holders also adds to market manipulation potential. Caution and thorough personal research are strongly advised.

### Has spucex been audited?

The spucex (SPCX) contract is listed as 'Contract verified: False.' This indicates its code has not been publicly published on the blockchain explorer. Without this fundamental transparency, a formal security audit cannot be performed or independently verified. Consequently, investors lack the assurance an audit would provide regarding the contract's integrity and potential vulnerabilities remain opaque.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4zbjvljgqjt8pkzjdphset2c2rvnz1ws76tbc4kvaxwt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spucex-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-16*

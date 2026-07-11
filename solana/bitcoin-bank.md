---
token: Bitcoin Bank
ticker: BTCBANK
network: solana
risk_score: 35
status: medium
date: 2026-06-10
---

# Bitcoin Bank (BTCBANK) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitcoin-bank-sol)

---

## Audit Summary

The Bitcoin Bank (BTCBANK) SPL Token Mint on Solana demonstrates a strong technical configuration with both mint and freeze authorities revoked, preventing further token issuance or account freezing. No Token-2022 extensions like transfer hooks or permanent delegates are active, and metadata is immutable. Holder concentration data was unavailable for this audit, which is a key factor for assessing market manipulation risk.

> **Final Recommendation:** This token presents a low technical risk profile due to the revocation of critical authorities and the absence of mutable features or active Token-2022 extensions that could alter token behavior. Holders should be aware that holder concentration data was not available for this audit, which is an important factor for assessing potential market manipulation. It is recommended to monitor on-chain holder distribution independently before making significant investments. No further technical audit is required for the mint configuration itself.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.6 External: The SPL Token Mint is configured using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The token has a total DEX liquidity of $35,597, with a 24-hour volume of $27,761. The Volume/Liquidity Ratio is 0.78, indicating normal trading activity without signs of wash trading. Th |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority and freeze authority are both revoked, indicating that the token's supply and account freezing capabilities are fixed. GoPlus data confirms that metadata is immutable, |

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
| **Top-10 Holders** | 37.3% of supply |
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

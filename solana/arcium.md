---
token: Arcium
ticker: ARX
network: solana
risk_score: 57
status: high
date: 2026-06-23
---

# Arcium (ARX) — Smart Contract Security Analysis | Solana

> **Risk Score: 57/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arcium-sol)

---

## Audit Summary

This audit of the Arcium (ARX) SPL token mint found no critical or high-severity issues based on the available on-chain data and external security signals. Both mint and freeze authorities have been revoked, indicating a fixed supply and immutable freeze status. Holder concentration data was unavailable, which prevents a full assessment of distribution risk.

> **Final Recommendation:** The Arcium (ARX) token mint appears to be well-configured with critical authorities revoked, offering a fixed supply and immutable freeze status. Investors should note the absence of holder concentration data, which is crucial for assessing potential market manipulation risks. It is recommended to monitor for this data if it becomes available.

For a Premium Deploy, consider implementing a robust monitoring solution for holder distribution and liquidity metrics, and conduct ongoing due diligence on the project's ecosystem and team, especially given the relatively new pair age.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.2 Code Security: The Arcium (ARX) token is an SPL token mint operating on the Solana blockchain using the standard `spl-token` program. This token mint has robust security configu |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The token exhibits moderate liquidity with $306,291 USD in total DEX liquidity. The 24-hour trading volume is $3,984 USD, resulting in a healthy Volume/Liquidity Ratio of 0.01, which doe |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The token mint's critical authorities, Mint Authority and Freeze Authority, have been revoked, indicating that the token's supply and freeze capabilities are immutable. GoPlus data confi |

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
| **Contract** | [`ARXwZk...DrFs`](https://solscan.io/account/ARXwZkNAtzPfdcoqQiduJn8EPv9fKiDfGn2KyggyDrFs) |
| **Network** | Solana |
| **Price** | $0.404 |
| **24h Volume** | $1.21M |
| **Liquidity** | $336.3K |
| **Volume / Liquidity** | 3.6× |
| **Token Age** | 22h |
| **Top-10 Holders** | 94.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2891 buys / 3325 sells |

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

### Is Arcium a scam?

Based purely on the provided data, labeling Arcium (ARX) definitively as a "scam" is premature. While it exhibits positive traits like renounced ownership and no mint function, critical red flags exist. The contract is unverified, liquidity is unlocked, and a concerning 94.8% of the supply is concentrated among the top 10 holders. These factors contribute to its overall high-risk score of 63/100, indicating significant vulnerabilities that could be exploited.

### Is Arcium safe to buy?

Arcium (ARX) is assessed with a high-risk score of 63/100, indicating it is not considered safe for investment based on the current data. Key risk factors include the contract being unverified, extreme token concentration with 94.8% held by the top 10 wallets, and unlocked liquidity. These conditions create significant potential for market manipulation or sudden liquidity withdrawal. Investors should exercise extreme caution and be aware of these inherent volatilities.

### Has Arcium been audited?

No, the Arcium (ARX) contract has not been verified. Contract verification is a crucial first step for any public audit, as it allows external security firms and the community to scrutinize the underlying code for vulnerabilities or malicious functions. Without verification, there is no public access to the contract's source code, making it impossible to confirm its integrity or audit its security.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/frrzset56fhgmrumaewsc5ql1wfzecmfs2stuypayjvw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arcium-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-23*

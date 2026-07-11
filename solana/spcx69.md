---
token: SPCX69
ticker: SPCX69
network: solana
risk_score: 21
status: medium
date: 2026-06-17
---

# SPCX69 (SPCX69) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spcx69-sol)

---

## Audit Summary

The SPCX69 SPL Token Mint exhibits a robust security posture with no critical or high-severity issues identified based on the available on-chain data and external security signals. Both mint and freeze authorities are revoked, and no permanent delegate or transfer hook extensions are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available data, SPCX69 appears to be a well-configured SPL Token-2022 mint with key authorities revoked, indicating a commitment to immutability and decentralization of core token functions. Holders should be aware that holder concentration data was unavailable, which is a common limitation for new tokens and prevents a full assessment of distribution risk. It is recommended to monitor on-chain holder distribution as this data becomes available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.3 Access Control: The SPCX69 token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked (None), ensuring no new tokens can be minted and no ex |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The token exhibits good liquidity with $207,698 USD on DEXs and a 24-hour volume of $1,397,421 USD. The Volume/Liquidity Ratio is 6.73, which is within acceptable limits and does not ind |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority and freeze authority are both revoked, meaning the token's core parameters (supply, freeze capability) cannot be altered. The token utilizes the spl-token-2022 program |

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
| **Contract** | [`SPCXwB...3N69`](https://solscan.io/account/SPCXwBHVrKpRqMRawL3NNvt1sXP2Yf3edwRbta53N69) |
| **Network** | Solana |
| **Price** | $0.003701 |
| **24h Volume** | $805.3K |
| **Liquidity** | $161.0K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 4d |
| **Top-10 Holders** | 8.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14725 buys / 5805 sells |

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

### Is SPCX69 a scam?

Based on the provided data, we cannot definitively label SPCX69 as a scam. The renounced ownership and lack of a mint function reduce common scam vectors. However, the unverified contract and unlocked liquidity introduce significant risks that could potentially lead to investor losses. These elements require thorough individual assessment before concluding its legitimacy or malicious intent.

### Is SPCX69 safe to buy?

SPCX69 carries notable risks that prevent it from being considered truly 'safe.' The contract's unverified status means its code cannot be publicly scrutinized for vulnerabilities or malicious functions. Furthermore, the unlocked liquidity presents a substantial risk, as it could be removed at any time, impacting the token's market stability. Investors should proceed with caution, acknowledging these significant financial risks.

### Has SPCX69 been audited?

The SPCX69 contract is not verified, meaning its code is not publicly accessible for review. This is distinct from a security audit. The provided data does not confirm if SPCX69 has undergone a formal independent audit. This lack of transparency regarding the code and its security significantly elevates investor risk.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5qphhqpaw3cz5anbnhqgzjxjm7ennrka6hwtzhmxj2dr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spcx69-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-17*

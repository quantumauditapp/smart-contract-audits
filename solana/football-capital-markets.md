---
token: Football Capital Markets
ticker: FCM
network: solana
risk_score: 35
status: medium
date: 2026-06-10
---

# Football Capital Markets (FCM) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/football-capital-markets-sol)

---

## Audit Summary

The Football Capital Markets (FCM) SPL token mint exhibits strong security configurations with both mint and freeze authorities revoked, preventing further token issuance or account freezing. No Token-2022 extensions that grant administrative control, such as Transfer Hook or Permanent Delegate, are active, and metadata is immutable. Holder concentration data was unavailable, which is a key missing piece for a complete risk assessment.

> **Final Recommendation:** Based on the available on-chain data, the FCM token mint appears to be securely configured with no active administrative authorities that could manipulate supply, freeze accounts, or alter token metadata. The absence of a transfer hook or permanent delegate also reduces operational risks. However, a complete assessment of market manipulation risk is hindered by the unavailability of holder concentration data. Prospective holders should consider the unknown distribution of tokens and monitor for any future changes in liquidity or trading patterns. For a premium deployment, ensuring all relevant market data, including holder distribution, is available for analysis would provide a more comprehensive risk profile.

## Security Analysis

The Football Capital Markets (FCM) SPL token mint exhibits strong security configurations with both mint and freeze authorities revoked, preventing further token issuance or account freezing. No Token-2022 extensions that grant administrative control, such as Transfer Hook or Permanent Delegate, are active, and metadata is immutable. Holder concentration data was unavailable, which is a key missing piece for a complete risk assessment.

Based on the available on-chain data, the FCM token mint appears to be securely configured with no active administrative authorities that could manipulate supply, freeze accounts, or alter token metadata. The absence of a transfer hook or permanent delegate also reduces operational risks. However, a complete assessment of market manipulation risk is hindered by the unavailability of holder concentration data. Prospective holders should consider the unknown distribution of tokens and monitor for any future changes in liquidity or trading patterns. For a premium deployment, ensuring all relevant market data, including holder distribution, is available for analysis would provide a more comprehensive risk profile.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | 7.1 Architecture & 7.2 Code Security: The FCM token is an SPL Token-2022 mint. Both the Mint Authority and Freeze Authority are revoked (None), indicating that no entity can mint new tokens or freeze  |
| **Governance / Economics** | 6/10 | Low | 7.4 Economic: The token has a healthy liquidity of $172,411 USD on DEXs. The 24-hour volume of $511,644 USD results in a Volume/Liquidity Ratio of 2.97, which is considered normal and does not signal  |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: The token's Mint and Freeze authorities are revoked, meaning no further administrative control can be exercised over the token's supply or account states. As an SPL Token-2022, it suppor |

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
| **Contract** | [`Hkpi2S...pump`](https://solscan.io/account/Hkpi2SkNWm5LogyY1Bz4zYTq5REVvco2aYWd1tYppump) |
| **Network** | Solana |
| **Price** | $0.004738 |
| **24h Volume** | $222.9K |
| **Liquidity** | $175.0K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 12d |
| **Top-10 Holders** | 61.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7986 buys / 3573 sells |

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

### Is Football Capital Markets a scam?

While the data does not definitively label Football Capital Markets as a scam, it exhibits several high-risk characteristics. The unverified contract, unrenounced ownership, and unlocked liquidity create conditions where malicious actions are possible. These factors contribute to its 61/100 high-risk score, warranting extreme caution from potential investors regarding the project's long-term viability and integrity.

### Is Football Capital Markets safe to buy?

Football Capital Markets is currently assessed as having a high-risk profile (61/100), suggesting it is not safe for typical investment. Key safety concerns include the contract not being verified, ownership not being renounced, and the project's liquidity not being locked. These elements mean the project's integrity is heavily reliant on the developer's trustworthiness, which carries inherent risks for investors.

### Has Football Capital Markets been audited?

The Football Capital Markets contract is reported as "unverified." This means its source code has not been publicly provided or confirmed to match the deployed code on the blockchain. Without contract verification, a thorough and verifiable security audit is practically impossible for external parties. This lack of transparency prevents independent review of its functionalities and security.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/rxfkdunvinpubdzdyn68rtm3bh2t9s5jytpai8e4zbi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/football-capital-markets-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

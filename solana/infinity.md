---
token: infinity
ticker: INFINITY
network: solana
risk_score: 63
status: high
date: 2026-06-28
---

# infinity (INFINITY) — Smart Contract Security Analysis | Solana

> **Risk Score: 63/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/infinity-sol)

---

## Audit Summary

This audit of the infinity (infinity) SPL token mint reveals a critical risk: RugCheck.xyz assigns a score of 1/100, strongly indicating a rugged project. While mint and freeze authorities are revoked, and metadata is immutable, the extreme negative signal from RugCheck.xyz overshadows these positive attributes. Holder concentration data was unavailable.

> **Final Recommendation:** Given the critical 'RugCheck Flagged as Rugged' finding, it is strongly recommended to avoid any interaction with this token. While some technical aspects like revoked authorities and immutable metadata are positive, the severe negative signal from RugCheck.xyz indicates a high probability of malicious intent or project failure. Do not purchase, hold, or trade this token.

For future token considerations, always prioritize tokens with a clean RugCheck score, sufficient liquidity, and transparent holder distribution. A Premium Deploy option would involve a comprehensive review of the project's off-chain documentation, team background, and community sentiment, which is beyond the scope of this on-chain data audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | 7.1 Architecture & 7.3 Access Control: The infinity token is an SPL Token-2022 mint on Solana. Both the mint authority and freeze authority have been revoked, which prevents the creation of new… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic: The token has a total DEX liquidity of $15,866 USD, with a 24-hour volume of $7,752 USD. The volume/liquidity ratio is 0.49, which is considered normal and does not suggest wash… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades: The token's core parameters, such as minting and freezing capabilities, are fixed due to the revocation of both mint and freeze authorities. The token utilizes the spl-token-2022… |

## Security Findings

_🔴 1 Critical_

### `C-01` — RugCheck Flagged as Rugged  *(Severity: Critical · Status: Unresolved)*

RugCheck.xyz classifies this token as rugged based on its own dataset (developer history, LP movements). The RugCheck Score is 1 / 100, indicating an extremely high risk.

**Recommendation:** Do not interact with this token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H7t7oK...pump`](https://solscan.io/account/H7t7oKniUDhyMaJqsEt5ajQJ2TkxBxiPA9FXEHmUpump) |
| **Network** | Solana |
| **Price** | $0.00004381 |
| **24h Volume** | $112.5K |
| **Liquidity** | $15.2K |
| **Volume / Liquidity** | 7.4× |
| **Token Age** | 6d |
| **Top-10 Holders** | 37.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2763 buys / 42245 sells |

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

### Is infinity a scam?

Based on the available data, INFINITY exhibits several high-risk characteristics that are often associated with less secure tokens. The unverified contract, unlocked liquidity, and concentrated holdings by the top 10 wallets are notable concerns. While ownership is renounced and no new tokens can be minted, these other factors contribute to a high-risk profile (47/100), suggesting caution is warranted rather than a definitive 'scam' label.

### Is infinity safe to buy?

Investing in INFINITY carries significant risks, evidenced by its 47/100 high-risk score. The contract's unverified status means its underlying code is not transparently auditable by the public. Furthermore, the unlocked liquidity creates potential for liquidity removal, and the substantial holdings by the top 10 wallets introduce centralization concerns. These factors collectively indicate a high degree of caution is advisable, as the asset is not considered safe.

### Has infinity been audited?

The provided data indicates that INFINITY's contract has not been verified. This means the deployed code cannot be easily reviewed by the public or independent auditors to confirm its integrity and security. Without contract verification, a comprehensive security audit is significantly hindered, making it challenging to establish the token's safety and functionality based on its code.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gy45dwdqvelwhpcwid1dxfaygdy4s97xmdcv8xfjjcoa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/infinity-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-28*

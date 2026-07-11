---
token: Football Capital Markets
ticker: FCM
network: solana
risk_score: 44
status: medium
date: 2026-06-10
---

# Football Capital Markets (FCM) — Smart Contract Security Analysis | Solana

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/football-capital-markets-sol)

---

## Audit Summary

The Football Capital Markets (FCM) SPL Token Mint exhibits strong security configurations with both mint and freeze authorities revoked, preventing further token issuance or account freezing. No critical Token-2022 extensions like permanent delegates or transfer hooks are active. However, holder concentration data is unavailable, which prevents a full assessment of potential market manipulation risks.

> **Final Recommendation:** Given the revoked mint and freeze authorities, the token's supply is fixed, and user accounts cannot be frozen. The absence of active Token-2022 extensions like transfer hooks and permanent delegates reduces operational risks. However, the lack of holder concentration data means the distribution of tokens among top accounts remains unknown, which could indicate potential for price volatility from large holders. Users should consider this data gap and monitor on-chain holder distribution if possible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Football Capital Markets (FCM) token is implemented using the `spl-token-2022` program, indicating modern Solana token standards. Access control is robust, with both the mint authority and freeze… |
| **Governance / Economics** | 5/10 | Medium | Economically, the token exhibits moderate liquidity of $193,546 USD with a 24-hour trading volume of $1,069,454 USD, suggesting active trading (7.4 Economic). The pair is relatively new, at 16 days… |
| **Upgrades** | 8/10 | Low | The token's upgradeability posture is secure, as both mint and freeze authorities are revoked, preventing any unilateral changes to token supply or account status (7.7 Upgrades). Furthermore, GoPlus… |

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
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

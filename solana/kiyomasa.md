---
token: Kiyomasa
ticker: 清正
network: solana
risk_score: 66
status: high
date: 2026-06-14
---

# Kiyomasa (清正) — Smart Contract Security Analysis | Solana

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kiyomasa-sol)

---

## Audit Summary

The Kiyomasa SPL Token Mint is configured with no active mint or freeze authorities, indicating a fixed supply and immutable account states. No high-risk flags were reported by third-party registries, and the token does not utilize potentially risky Token-2022 extensions like transfer hooks or default frozen accounts. Holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** Holders should monitor on-chain for any changes to the token's configuration, although current settings indicate immutability. Verify the token's liquidity and trading volume on DEXs before making significant trades, especially given the lack of holder distribution data. Confirm that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Kiyomasa token operates on the spl-token-2022 program. Both the mint authority and freeze authority are revoked, ensuring no new tokens can be minted and no accounts can be frozen. The token does… |
| **Governance / Economics** | 1/10 | High | The token exhibits moderate liquidity at $18,423 USD, with a 24-hour volume of $5,481 USD. The pair has been active for 111 days, providing a reasonable track record. The Volume/Liquidity Ratio is… |
| **Upgrades** | 5/10 | Medium | The token's configuration is highly immutable, as both the mint and freeze authorities have been revoked. No Token-2022 extensions that would allow for future modifications, such as transfer hook… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ANP1wJ...pump`](https://solscan.io/account/ANP1wJHYWYQPfrZvg8FnjduwfBVJhRV3xqKcs3yapump) |
| **Network** | Solana |
| **Price** | $0.00002417 |
| **24h Volume** | $1.9K |
| **Liquidity** | $16.4K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 57.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2989 buys / 2871 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Kiyomasa a scam?

Based on available data, Kiyomasa (清正) exhibits characteristics often associated with high-risk projects, such as an unverified contract and unlocked liquidity, which are concerning. However, ownership has been renounced and no mint function exists, mitigating certain developer-controlled rug pull vectors. While these red flags necessitate extreme caution and vigilance from investors, we cannot definitively label it a scam based solely on the provided data.

### Is Kiyomasa safe to buy?

Kiyomasa (清正) carries significant security risks that suggest it is not a safe investment. The contract is unverified, preventing public code review and potential hidden vulnerabilities. Crucially, liquidity is not locked, meaning the funds enabling trading can be removed by liquidity providers, risking a 'rug pull' and rendering tokens untradable. These fundamental issues, alongside some holder concentration, indicate a high-risk environment for potential buyers.

### Has Kiyomasa been audited?

There is no information indicating Kiyomasa (清正) has undergone a formal security audit. Moreover, the contract is explicitly listed as 'False' for verification. This means its source code is not publicly available or confirmed to match the deployed bytecode on the blockchain. This lack of transparency and an independent audit makes it challenging to assess the contract's integrity and security, posing a significant risk.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/dkg6ternfkmeelmxcvxwobzzzqi7vtpkco6gqvukf33c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kiyomasa-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-14*

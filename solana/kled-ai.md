---
token: Kled AI
ticker: KLED
network: solana
risk_score: 23
status: medium
date: 2026-06-27
---

# Kled AI (KLED) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kled-ai-sol)

---

## Audit Summary

This audit of the KLEDAI (KLED) SPL token mint found that both the mint and freeze authorities have been revoked, indicating a fixed supply and unfreezable accounts. However, the token's metadata remains mutable, allowing for potential changes to its name, symbol, or image. Holder concentration data was unavailable from chain-native RPC sources, preventing an assessment of supply distribution risk.

> **Final Recommendation:** Holders should verify the token's metadata (name, symbol, image) against official sources and monitor for any changes, as the metadata is mutable. Due to the unavailability of holder distribution data, it is advisable to exercise caution regarding potential market manipulation from concentrated holdings. The revocation of mint and freeze authorities provides a degree of security against supply dilution and account freezing.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The KLEDAI (KLED) token is an SPL token operating under the spl-token program. Both the mint authority and freeze authority have been revoked (None), ensuring that no new tokens can be minted and no… |
| **Governance / Economics** | 7/10 | Low | DEX market data indicates a liquidity of $496,380 USD and a 24-hour trading volume of $16,198 USD. The volume/liquidity ratio is 0.03, which is considered normal and does not suggest wash trading.… |
| **Upgrades** | 8/10 | Low | The mint and freeze authorities are both revoked, meaning these core parameters cannot be changed. The token's metadata, including its name, symbol, or image, is mutable. This allows for post-launch… |

## Security Findings

_🟢 1 Low_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata is mutable, as indicated by 'metadata_mutable: True'. This means the token name, symbol, or image can be changed post-launch by an authorized party.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding. Monitor for any changes to the token's name, symbol, or image.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`1zJX5g...W6jm`](https://solscan.io/account/1zJX5gRnjLgmTpq5sVwkq69mNDQkCemqoasyjaPW6jm) |
| **Network** | Solana |
| **Price** | $0.02324 |
| **24h Volume** | $1.71M |
| **Liquidity** | $629.4K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 23.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1679 buys / 1926 sells |

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

### Is Kled AI a scam?

Based on the available data, Kled AI presents a mixed security profile rather than definitive proof of a scam. Ownership is renounced and no mint function exists, which are positive indicators. However, the contract is not verified, and liquidity is not locked, introducing significant risks like hidden malicious code or potential liquidity removal. Investors should understand these dual aspects of its profile.

### Is Kled AI safe to buy?

Buying Kled AI carries notable risks primarily due to the unverified contract and unlocked liquidity. An unverified contract prevents code scrutiny, while unlocked liquidity means funds can be withdrawn at any time, potentially leading to a rug pull. While ownership is renounced, these substantial risks warrant extreme caution and thorough personal due diligence before considering an investment.

### Has Kled AI been audited?

The provided data indicates that the Kled AI contract is not verified. This means the contract's source code has not been publicly matched and confirmed, which is distinct from a formal security audit by an independent firm. Without verification or an audit, it is challenging to assess the underlying code's security or integrity.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4sbywy5uuxybwuj8fwhdfxun6mbtacrqbjwiz9mxworp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kled-ai-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-27*

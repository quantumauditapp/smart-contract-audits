---
token: TAPE
ticker: TAPE
network: solana
risk_score: 43
status: medium
date: 2026-06-16
---

# TAPE (TAPE) — Smart Contract Security Analysis | Solana

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tape-sol)

---

## Audit Summary

The TAPE SPL token mint demonstrates a strong security posture with both Mint and Freeze authorities permanently revoked, preventing further supply inflation or asset confiscation. No malicious Token-2022 extensions like transfer hooks or permanent delegates are active, and metadata is immutable. However, holder concentration data was unavailable, precluding an assessment of supply distribution risk.

> **Final Recommendation:** Based on the audit, the TAPE token exhibits a secure on-chain configuration with critical authorities revoked and no concerning Token-2022 extensions active. Holders can be confident that the supply is fixed and their assets cannot be frozen or transferred without consent by an authority. The primary remaining unknown is holder concentration, which could impact price stability if a few large holders decide to sell. Investors should consider the moderate liquidity and the unknown holder distribution when making investment decisions. For enhanced due diligence, consider a Premium Deploy option to monitor holder movements and liquidity trends over time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The TAPE token is configured using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, preventing further token issuance or freezing of user accounts. No Transf |
| **Governance / Economics** | 5/10 | Medium | The token exhibits moderate liquidity with $28,027 USD available on DEXs. The 24-hour trading volume of $13,433 USD results in a healthy Volume/Liquidity Ratio of 0.48, indicating normal trading activ |
| **Upgrades** | 8/10 | Low | The token's configuration is robust against unauthorized changes, as both the Mint and Freeze authorities have been permanently revoked. GoPlus data indicates that the token's metadata, including name |

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
| **Contract** | [`7QXDpK...pump`](https://solscan.io/account/7QXDpKoeEe9hJjiYTw6NmaAyyqX1KyBfvVXq3F24pump) |
| **Network** | Solana |
| **Price** | $0.0001286 |
| **24h Volume** | $143.4K |
| **Liquidity** | $27.0K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 15d |
| **Top-10 Holders** | 47.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2001 buys / 1507 sells |

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

### Is TAPE a scam?

Based on the available data, TAPE exhibits several characteristics associated with higher-risk projects, such as an unverified contract and unlocked liquidity, which could enable adverse actions like a rug pull. However, the ownership is renounced, and no new tokens can be minted. This combination means while not definitively a scam based solely on this data, significant risks are present that investors must acknowledge.

### Is TAPE safe to buy?

TAPE is not considered safe to buy without significant caution due to multiple risk factors. The unverified contract prevents code scrutiny, while unlocked liquidity exposes investors to potential withdrawal by providers. Furthermore, concentrated holdings by the top 10 wallets introduce market manipulation risks. Investors should proceed with extreme diligence and understand the implications of these identified vulnerabilities.

### Has TAPE been audited?

No, TAPE's contract is explicitly listed as 'not verified.' This means the smart contract code has not been publicly provided on the blockchain explorer for review. While this isn't a formal security audit by a third-party firm, the lack of verification prevents basic community scrutiny and independent assessment of its safety and functionality.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/2vnczdyzep9z253d1b8tambns4t1swp2chcppuqtnp5p)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tape-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-16*

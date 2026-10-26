---
token: mogging
ticker: MOGGING
network: solana
risk_score: 17
status: low
date: 2026-06-10
---

# mogging (MOGGING) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mogging-sol)

---

## Audit Summary

This audit of the mogging SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. Both mint and freeze authorities are revoked, and no Token-2022 extensions posing significant risks are active. Holder distribution data was unavailable, preventing an assessment of supply concentration.

> **Final Recommendation:** Prospective holders should monitor the token's liquidity and trading volume for any significant changes. It is also recommended to regularly check for the availability of holder distribution data to assess potential concentration risks. Verify on-chain that the mint and freeze authorities remain revoked before making any investment decisions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mogging token is implemented using the spl-token-2022 program. Crucially, both the mint authority and freeze authority have been revoked, preventing further token issuance or freezing of holder… |
| **Governance / Economics** | 7/10 | Low | The token exhibits moderate liquidity at $41,670, with a healthy 24-hour volume of $6,238, resulting in a normal Volume/Liquidity Ratio of 0.15. The DEX pair has been active for 121 days, providing a… |
| **Upgrades** | 10/10 | Low | The token's mint and freeze authorities are permanently revoked, meaning no further tokens can be minted and no accounts can be frozen. Metadata is immutable, preventing changes to the token's name… |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5oq4zK...pump`](https://solscan.io/account/5oq4zKetRkUMMrFtkWH7r1Q6HZJMsTjgCeU6isgYpump) |
| **Network** | Solana |
| **Price** | $0.00003873 |
| **24h Volume** | $127 |
| **Liquidity** | $27.1K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 58.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 860 buys / 750 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is mogging a scam?

Based on the available data, mogging exhibits several high-risk characteristics. The unverified contract, unrenounced ownership, and unlocked liquidity are significant red flags. While the data doesn't definitively label it a scam, these elements create a high potential for developer-induced issues or asset withdrawal, warranting extreme caution. Investors should be aware of these fundamental security gaps.

### Is mogging safe to buy?

Mogging is currently classified as 'Low Risk' with a score of 17/100, indicating it is not safe for most investors. Key risks include the contract not being verified, unrenounced ownership allowing potential developer manipulation, and unlocked liquidity exposing funds to potential rug pulls. These factors collectively highlight significant vulnerabilities, suggesting investors face substantial security risks when considering this token.

### Has mogging been audited?

The mogging contract is reported as 'not verified.' This means its code has not been published and confirmed on the blockchain. Without verification, assessing its functionality or security through an audit is severely hampered. Investors cannot independently inspect the contract, posing a significant transparency and trust risk.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5gjuboxlt8te68gvoaxttsx6pwfw1uzlsvhcp35esyxz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mogging-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

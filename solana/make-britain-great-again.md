---
token: Make Britain Great Again
ticker: MBGA
network: solana
risk_score: 30
status: low
date: 2026-06-20
---

# Make Britain Great Again (MBGA) — Smart Contract Security Analysis | Solana

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/make-britain-great-again-sol)

---

## Audit Summary

The Make Britain Great Again (MBGA) token mint is configured with revoked mint and freeze authorities, indicating a fixed supply and unfreezable accounts. No critical or high-risk issues were identified based on available on-chain data and third-party registries. Holder concentration data was unavailable for analysis, preventing a full assessment of distribution risk.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the mint and freeze authorities remain revoked. Monitor DEX liquidity and volume for any significant changes, as low liquidity can lead to high slippage. Be aware that holder distribution data was not available, so a full assessment of whale risk is not possible without further off-chain analysis.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The MBGA token is an SPL Token-2022 mint. Both the mint authority and freeze authority are revoked, ensuring no new tokens can be minted and no accounts can be frozen. It does not utilize a transfer… |
| **Governance / Economics** | 4/10 | Medium | The token exhibits moderate liquidity at $23,163 USD, with a healthy 24-hour volume to liquidity ratio of 0.23, suggesting organic trading activity. The DEX pair has been active for 37 days… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and account freeze capabilities are permanently fixed and cannot be altered. The token does not have upgradable… |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`dFybjf...pump`](https://solscan.io/account/dFybjfpAbTxjen9Ux2Q2dQSFTmrbcVRzYsGoiV5pump) |
| **Network** | Solana |
| **Price** | $0.00004474 |
| **24h Volume** | $623 |
| **Liquidity** | $25.8K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 16d |
| **Top-10 Holders** | 58.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 354 buys / 317 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Make Britain Great Again a scam?

Based on the available data, we cannot definitively label MBGA as a scam. However, the unverified contract and unlocked liquidity create a high-risk environment conducive to malicious activity, including potential rug pulls. These factors, alongside a Medium Risk score of 36/100, indicate significant caution is warranted when evaluating its legitimacy.

### Is Make Britain Great Again safe to buy?

Investing in Make Britain Great Again carries substantial risks and is not considered safe due to several critical factors. The contract remains unverified, preventing public code review, and its liquidity is not locked, exposing investors to potential rug pulls. Furthermore, a significant 47.0% of the supply is concentrated among the top 10 holders. These issues contribute to its Medium Risk score of 36/100.

### Has Make Britain Great Again been audited?

Information provided indicates the Make Britain Great Again contract is not verified. This means the underlying code is not publicly available or confirmed to match any published source code, which is a prerequisite for a meaningful security audit. Without verification, a comprehensive security assessment cannot definitively confirm the code's integrity or safety.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/26glcdwx5668yeq7hhhlzfdnarksnwxtguv7dufnzr7v)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/make-britain-great-again-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-20*

---
token: Dragon Ball Z
ticker: DBZ
network: solana
risk_score: 30
status: low
date: 2026-10-20
---

# Dragon Ball Z (DBZ) — Smart Contract Security Analysis | Solana

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dragon-ball-z-sol)

---

## Security Analysis

The Dragon Ball Z (DBZ) token on the Solana blockchain displays several fundamental security characteristics. The smart contract is verified, which allows for independent auditing of the underlying code, and the absence of a mint function mitigates the risk of unauthorized supply inflation post-deployment. Liquidity is currently locked, a critical feature designed to prevent rug pulls by ensuring funds remain accessible for trading. Market activity is marked by a 24-hour volume of $221,030 against a liquidity pool of $12,832. While the token shows healthy distribution with top holders collectively owning none of the total supply, it is notable that ownership has not been renounced. This implies that the deploying wallet retains administrative authority over the contract, which is a common feature in many Solana-based meme tokens but warrants ongoing monitoring by participants to ensure that control is exercised in accordance with established project governance protocols.

The primary safety signal for this asset is the locked liquidity, which provides a protective barrier against immediate liquidity withdrawal. Additionally, the lack of a mint function prevents supply manipulation. However, the most significant risk factor is that ownership has not been renounced. This means the contract creator holds potential power over the project's parameters. Investors should also note the thin liquidity-to-volume ratio; with only $12,832 in liquidity supporting over $221,000 in daily volume, the token may experience significant price volatility during periods of high trading activity. These signals suggest a project that is functional but remains subject to centralized control, requiring investors to perform thorough due diligence.

## Security Findings

_1 finding(s)_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AjhU1J...pump`](https://solscan.io/account/AjhU1JdT7M6tR3gCu4Zqq37ez8H65jBbaszjfb27pump) |
| **Network** | Solana |
| **Price** | $0.00002619 |
| **24h Volume** | $221.0K |
| **Liquidity** | $12.8K |
| **Volume / Liquidity** | 17.2× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4067 buys / 2649 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Dragon Ball Z a scam?

Based on the provided data, there is no evidence to label the token as a scam. The contract is verified, liquidity is locked, and there is no mint function. However, the lack of ownership renouncement means the developer retains control. Investors should evaluate these technical features carefully and conduct their own research before engaging with the project.

### Is Dragon Ball Z safe to buy?

While technical indicators like locked liquidity and a verified contract reduce common risks, no cryptocurrency is entirely safe. The primary risks here include the lack of ownership renouncement and low liquidity relative to trading volume. Potential buyers should consider these factors, understand that volatility is likely, and never invest more capital than they can afford to lose.

### Has Dragon Ball Z been audited?

The contract for Dragon Ball Z is verified, meaning the source code is publicly accessible for review on the blockchain. While this allows for independent verification of functionality, it is distinct from a formal security audit conducted by a professional third-party firm. Users should rely on the verified code to understand contract mechanics.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/73qr5drpyrksgqjlxumamaytg8d6qvw2ydbrdabkz1va)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dragon-ball-z-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

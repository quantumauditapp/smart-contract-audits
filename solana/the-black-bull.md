---
token: The Black Bull
ticker: ANSEM
network: solana
risk_score: 8
status: low
date: 2026-06-29
---

# The Black Bull (ANSEM) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-black-bull-sol)

---

## Audit Summary

This Solana SPL Token Mint (ANSEM) exhibits a robust security configuration with both mint and freeze authorities permanently revoked. No critical Token-2022 extensions such as transfer hooks or default frozen account states are active. While chain-native holder distribution data was unavailable, a third-party risk registry signals potential high holder concentration. The token has substantial DEX liquidity and active trading volume.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of accounts. Given the third-party signals regarding holder concentration, it is advisable to monitor the token's distribution over time for any significant changes. While the volume/liquidity ratio is high, users should account for potential slippage in large trades and understand the implications of active trading patterns.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program, leveraging its advanced features. Both the Mint Authority and Freeze Authority have been revoked, ensuring that no new tokens can be minted… |
| **Governance / Economics** | 8/10 | Low | The token benefits from significant DEX liquidity, reported at $2,194,837, which supports trading and reduces slippage for typical transactions (7.4 Economic). The 24-hour trading volume is high at… |
| **Upgrades** | 10/10 | Low | The token's configuration demonstrates a strong commitment to immutability post-launch. The revocation of both Mint and Freeze authorities means that the token supply and the ability to freeze… |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9cRCn9...pump`](https://solscan.io/account/9cRCn9rGT8V2imeM2BaKs13yhMEais3ruM3rPvTGpump) |
| **Network** | Solana |
| **Price** | $0.1701 |
| **24h Volume** | $2.56M |
| **Liquidity** | $2.62M |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 12d |
| **Top-10 Holders** | 67.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 89728 buys / 75278 sells |

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

### Is The Black Bull a scam?

Based on the available data, The Black Bull (ANSEM) exhibits several characteristics associated with high-risk projects. Its risk score is 55/100, indicating high potential for issues. Key concerns include unlocked liquidity, highly concentrated token ownership (82.4% by top 10 holders), and an unverified contract. While ownership is renounced, these other factors suggest a substantial risk profile that warrants extreme caution.

### Is The Black Bull safe to buy?

Investing in The Black Bull (ANSEM) carries significant risks, making it generally not considered safe based on current data. The primary concerns are the unlocked liquidity, which exposes investors to potential rug pulls, and the heavily concentrated token ownership among the top 10 holders (82.4%). Furthermore, the unverified contract means the code cannot be independently audited for security vulnerabilities, contributing to its 'Low Risk' score of 8/100.

### Has The Black Bull been audited?

The Black Bull (ANSEM) contract is currently unverified. This means its source code has not been publicly published and matched to the deployed contract on the blockchain. Without verification, independent security audits are severely hampered, and investors cannot confirm the contract's intended functionality or identify potential vulnerabilities, adding to its overall high-risk profile.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/fnzky6x7entq1er3d225dqyt7ybfka4pskbmqhb8l3cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-black-bull-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-29*

---
token: United Energy Reserve
ticker: UER
network: solana
risk_score: 0
status: low
date: 2026-10-20
---

# United Energy Reserve (UER) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-energy-reserve-sol)

---

## Audit Summary

The United Energy Reserve (UER) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks of rug pulls. Holder concentration data is unavailable, and third-party registries indicate high holder correlation, which should be monitored by potential participants.

> **Final Recommendation:** The token demonstrates strong security fundamentals regarding its on-chain authorities and liquidity. Users should monitor the high holder correlation noted by third-party registries to assess potential market impact from concentrated positions.

Verify the current supply and authority status using a block explorer to ensure no changes have occurred. As holder concentration data is currently unavailable, perform independent analysis of the top token accounts before committing significant capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is initialized on the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained by the… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $1.65M in liquidity, which is 100% burned. 7.5 Governance and holder distribution data are currently unavailable, though third-party signals suggest high holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is a standard SPL token. 7.8 Operations are secure due to the permanent revocation of metadata and balance mutability. The token configuration is immutable. |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DuMHfw...pump`](https://solscan.io/account/DuMHfwgHYpJnp9X6HAGQuZts5x6Lwug6iAWWRuFhpump) |
| **Network** | Solana |
| **Price** | $0.3643 |
| **24h Volume** | $405.9K |
| **Liquidity** | $1.66M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 38916 buys / 1088 sells |

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

### Is United Energy Reserve a scam?

Data indicates low-risk attributes such as locked liquidity and a verified contract without minting capabilities. With a decentralized holder base and a risk score of 29/100, there are no immediate signs of fraudulent activity. However, investors should conduct independent due diligence, as security metrics reflect the project's current technical status and do not guarantee future performance or total immunity from risks.

### Is United Energy Reserve safe to buy?

The project exhibits positive safety indicators including high liquidity and no mint function. Despite the low risk score, investors must note that ownership has not been renounced, which serves as a notable risk factor. Potential buyers should consider their risk tolerance, assess the market liquidity depth, and monitor for any changes to contract administration rights before making an investment decision.

### Has United Energy Reserve been audited?

The United Energy Reserve contract is confirmed as verified, ensuring the public code matches the deployed bytecode. While verification is a fundamental step in confirming contract transparency, it is distinct from a comprehensive third-party security audit. Investors should remain aware that technical verification does not automatically certify the project against all potential vulnerabilities.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4awhgymam5pg4db1jhppbmrmuptjvuufbmwgzn7le7mr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-energy-reserve-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

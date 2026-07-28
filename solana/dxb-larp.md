---
token: DXB LARP
ticker: LARP
network: solana
risk_score: 83
status: critical
date: 2026-07-25
---

# DXB LARP (LARP) — Smart Contract Security Analysis | Solana

> **Risk Score: 83/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dxb-larp-sol)

---

## Audit Summary

This audit of the DXB LARP (LARP) SPL token mint identifies significant risks primarily related to market stability and holder concentration. The top 10 token accounts control 94.37% of the total supply, posing a high risk of price manipulation or sudden sell-offs. Additionally, the token exhibits very low DEX liquidity at $2,183, making large trades highly susceptible to slippage. The DEX pair is also very new, having been created only 5 days ago, which limits the track record for assessing market behavior. Third-party registry data on holder distribution was unavailable.

> **Final Recommendation:** Prospective holders should exercise extreme caution due to the high concentration of tokens among a few holders and the very low liquidity. Before acquiring this token, verify the current holder distribution on-chain to assess any changes in concentration. Monitor DEX liquidity closely, as insufficient liquidity will severely impact the ability to trade without significant price impact. Given the very new pair age, observe trading patterns and community activity for an extended period to gain a better understanding of its stability and potential risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The DXB LARP token is implemented using the standard `spl-token` program, which is a well-established and audited program on Solana. Key administrative authorities, including the Mint Authority and… |
| **Governance / Economics** | 1/10 | High | The economic stability of the DXB LARP token is highly concerning due to extreme holder concentration, with the top 10 token accounts holding 94.37% of the total supply. This level of concentration… |
| **Upgrades** | 6/10 | Medium | The DXB LARP token mint exhibits a fixed configuration for core parameters. Both the Mint Authority and Freeze Authority have been permanently revoked, ensuring that no new tokens can be minted and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Raydium Lock |

## Security Findings

_🟠 2 High · 🟡 1 Medium_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

Top 10 token accounts hold 94.37% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to concentrated holdings. Verify current holder distribution on-chain before making investment decisions.


### `H-02` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,183. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Be aware that trading this token will incur high slippage. Large positions are difficult to exit without substantial price impact. Monitor liquidity levels closely.


### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 5 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Exercise caution due to the limited operational history of the DEX pair. Observe market behavior and project developments for a longer period before committing significant capital.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`67zHAw...GreN`](https://solscan.io/account/67zHAwrdHwpvbF8psA4hYCSFarcCaFBmXNhE2HPrGreN) |
| **Network** | Solana |
| **Price** | $0.00000176 |
| **24h Volume** | $708 |
| **Liquidity** | $2.2K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 3d |
| **Top-10 Holders** | 94.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 712 buys / 450 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is DXB LARP a scam?

Based on automated analysis, DXB LARP scores 82/100 (Critical Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is DXB LARP safe to buy?

Our scanner flagged a risk score of 82/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has DXB LARP been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/h6htb2dtovuzbx3mepyvxnuk5gjdxosjqx2eo7bmf1fh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dxb-larp-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-25*

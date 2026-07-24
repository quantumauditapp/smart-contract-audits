---
token: WORLD BET
ticker: WBET
network: solana
risk_score: 93
status: critical
date: 2026-06-25
---

# WORLD BET (WBET) — Smart Contract Security Analysis | Solana

> **Risk Score: 93/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-bet-sol)

---

## Audit Summary

The WORLD BET (WBET) token mint on Solana has revoked both its Mint and Freeze authorities, which is a positive security characteristic as it prevents further token dilution or account freezing. However, the token exhibits very low liquidity, with only $4,086 in total DEX liquidity, making large positions difficult to exit without significant slippage. Holder distribution data was unavailable from chain-native RPC.

> **Final Recommendation:** Prospective holders should be aware of the extremely low liquidity, which poses a significant risk for exiting positions. Verify on-chain that the Mint and Freeze authorities remain revoked to ensure the supply is fixed and accounts cannot be frozen. Monitor DEX liquidity and trading volume closely, as these metrics are critical for assessing market viability and price stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The WORLD BET (WBET) token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, indicating that no new tokens can be minted and no holder… |
| **Governance / Economics** | 1/10 | High | The token exhibits very low liquidity, with only $4,086 in total DEX liquidity, which can lead to severe slippage for any significant trade. The 24-hour volume is $13, and the Volume/Liquidity Ratio… |
| **Upgrades** | 4/10 | Medium | The token's Mint Authority and Freeze Authority are both revoked, meaning core parameters related to supply and account control cannot be changed. The token does not have upgradable transfer fees or… |

## Security Findings

_🟠 1 High_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $4,086. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the low liquidity in any swap calculation and be aware of the potential for significant price impact on trades.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`31989Y...pump`](https://solscan.io/account/31989YsfUahV66TGiMvdSyTj1AQNvcdT327Uiu9mpump) |
| **Network** | Solana |
| **Price** | $0.00000224 |
| **24h Volume** | $14 |
| **Liquidity** | $3.7K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | 89.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2050 buys / 1628 sells |

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

### Is WORLD BET a scam?

Based on the available data, WORLD BET exhibits several high-risk characteristics that investors should be aware of. The contract is unverified, meaning its code cannot be publicly inspected for malicious functions or vulnerabilities. Additionally, the liquidity is not locked, creating a potential for sudden withdrawal, commonly associated with "rug pull" schemes. These factors, alongside its 47/100 high-risk score, suggest extreme caution is warranted.

### Is WORLD BET safe to buy?

WORLD BET is not considered safe to buy based on the provided security data. Key risk factors include an unverified contract, which prevents public code review, and unlocked liquidity, which carries the risk of a "rug pull." Despite renounced ownership and a distributed holder base, these critical vulnerabilities contribute to a high-risk score of 47/100, advising investors to exercise extreme caution before considering any investment.

### Has WORLD BET been audited?

The provided data indicates the WORLD BET contract is not verified. Contract verification is a foundational step for any credible audit, making the code publicly viewable. Without this, a comprehensive security audit by independent third parties is typically not possible or conclusive, meaning the absence of vulnerabilities or malicious code cannot be confirmed.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/apzdirx3ee11c5ppapny5ecz29cdhgua76yoc1s7bs3e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-bet-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-25*

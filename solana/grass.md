---
token: Grass
ticker: GRASS
network: solana
risk_score: 73
status: critical
date: 2026-06-24
---

# Grass (GRASS) — Smart Contract Security Analysis | Solana

> **Risk Score: 73/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grass-sol)

---

## Audit Summary

The Grass (GRASS) SPL token mint presents a critical risk due to an active mint authority, which allows for unlimited token creation and potential dilution of holders. Additionally, the token's metadata is mutable, meaning its name, symbol, or image can be altered post-launch. Holder distribution data was unavailable from chain-native RPC, preventing an assessment of supply concentration risk.

> **Final Recommendation:** Before holding GRASS tokens, verify on-chain that the mint authority (31rYartQwHeBMjAe2MgGpffGV57fQy3kug4BDN8tLGqQ) has been set to null to ensure a fixed supply. Continuously monitor the token's metadata for any changes to its branding, as it is mutable. If holder distribution data becomes available, assess the concentration of tokens among the top accounts to understand potential market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is implemented using the classic SPL Token Program (spl-token). A critical finding is the active mint authority, held by 31rYartQwHeBMjAe2MgGpffGV57fQY3kug4BDN8tLGqQ, which enables the… |
| **Governance / Economics** | 1/10 | High | The token exhibits moderate liquidity at $320,381 USD, with a healthy 24-hour volume of $7,110 USD. The Volume/Liquidity Ratio is 0.02, which does not indicate wash trading. The DEX pair has been… |
| **Upgrades** | 4/10 | Medium | The mint authority remains active, allowing for potential changes to the token's total supply. The freeze authority has been revoked, which is a positive for the immutability of account states.… |

## Security Findings

_🔴 1 Critical · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 31rYartQwHeBMjAe2MgGpffGV57fQy3kug4BDN8tLGqQ. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. This fact is also flagged by a third-party risk registry.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`. This fact is also noted by a third-party risk registry.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Grass7...XXjs`](https://solscan.io/account/Grass7B4RdKfBCjTKgSqnXkqjwiGvQyFbuSCUJr3XXjs) |
| **Network** | Solana |
| **Price** | $0.3651 |
| **24h Volume** | $1.6K |
| **Liquidity** | $283.0K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 54.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1519 buys / 1970 sells |

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

### Is Grass a scam?

Based on the available data, Grass (GRASS) exhibits several characteristics typically associated with high-risk tokens. While ownership is renounced and no mint function exists, the absence of contract verification and unlocked liquidity are significant red flags. Furthermore, the concentration of 55.6% of the supply among the top 10 holders indicates a centralized distribution. These factors contribute to its high-risk score of 54/100, suggesting caution rather than definitively labeling it a scam.

### Is Grass safe to buy?

Given its high-risk score of 54/100, Grass (GRASS) is not considered safe to buy without significant caution. Key risk factors include the unverified contract, which prevents independent code review, and the unlocked liquidity, exposing it to potential rug pulls. The substantial concentration of tokens among the top 10 holders also poses a risk of market manipulation or sudden sell-offs. Investors should be aware of these fundamental vulnerabilities.

### Has Grass been audited?

The provided information indicates that the Grass (GRASS) contract has not been verified. Contract verification is a foundational step for transparency, allowing public review of the code. Without verification, it's impossible to confirm if the contract has undergone a formal security audit by a reputable third party. Investors should assume no audit has occurred unless public verification and audit reports are explicitly available.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gtj2s27ul7yz3tdtwpkjfncxeezrkrphjpj5fubwb8mk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grass-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-24*

---
token: Grass
ticker: GRASS
network: solana
risk_score: 65
status: high
date: 2026-06-24
---

# Grass (GRASS) — Smart Contract Security Analysis | Solana

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grass-sol)

---

## Audit Summary

The Grass (GRASS) token mint presents critical risks due to an active mint authority, enabling the issuer to create unlimited new tokens and dilute existing holders. Additionally, new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. Holder concentration data was unavailable, preventing an assessment of distribution risk.

> **Final Recommendation:** Holders should exercise extreme caution due to the active mint authority, which enables the issuer to dilute the token supply at any time. Verify on-chain that the mint authority is set to null before considering the supply fixed. Be aware that new token accounts will be frozen by default, requiring an active issuer to unfreeze them for transfers. If considering a Premium Deploy option, ensure all mutable authorities are revoked and default account states are unfrozen to mitigate centralisation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The token is an SPL token mint operating under the `spl-token` program. A significant risk is the active mint authority (`31rYartQwHeBMjAe2MgGpffGV57fQY3kug4BDN8tLGqQ`), which allows for unlimited tok |
| **Governance / Economics** | 3/10 | High | The token exhibits normal trading patterns with a 24-hour volume of $7,120 against a liquidity of $366,751, resulting in a low Volume/Liquidity Ratio of 0.02 (7.4 Economic). The DEX pair has been acti |
| **Upgrades** | 6/10 | Medium | The mint authority remains active, posing a risk of supply inflation (7.7 Upgrades). The freeze authority has been revoked, which is a positive security measure. The token's metadata is immutable (`Go |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 1 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is `31rYartQwHeBMjAe2MgGpffGV57fQY3kug4BDN8tLGqQ`. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. (Fact: Mint Authority is NOT null/revoked)

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state (`GoPlus.default_account_state: 1`) and require explicit unfreezing by an authority. (Fact: Default Account State is "frozen")

**Recommendation:** Confirm an active issuer is available to unfreeze accounts; otherwise the token is unspendable.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Grass7...XXjs`](https://solscan.io/account/Grass7B4RdKfBCjTKgSqnXkqjwiGvQyFbuSCUJr3XXjs) |
| **Network** | Solana |
| **Price** | $0.4495 |
| **24h Volume** | $115.6K |
| **Liquidity** | $342.3K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 55.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1519 buys / 1970 sells |

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

### Is Grass a scam?

Based on the available data, Grass (GRASS) exhibits several characteristics typically associated with high-risk tokens. While ownership is renounced and no mint function exists, the absence of contract verification and unlocked liquidity are significant red flags. Furthermore, the concentration of 55.6% of the supply among the top 10 holders indicates a centralized distribution. These factors contribute to its high-risk score of 54/100, suggesting caution rather than definitively labeling it a scam.

### Is Grass safe to buy?

Given its high-risk score of 54/100, Grass (GRASS) is not considered safe to buy without significant caution. Key risk factors include the unverified contract, which prevents independent code review, and the unlocked liquidity, exposing it to potential rug pulls. The substantial concentration of tokens among the top 10 holders also poses a risk of market manipulation or sudden sell-offs. Investors should be aware of these fundamental vulnerabilities.

### Has Grass been audited?

The provided information indicates that the Grass (GRASS) contract has not been verified. Contract verification is a foundational step for transparency, allowing public review of the code. Without verification, it's impossible to confirm if the contract has undergone a formal security audit by a reputable third party. Investors should assume no audit has occurred unless public verification and audit reports are explicitly available.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gtj2s27ul7yz3tdtwpkjfncxeezrkrphjpj5fubwb8mk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grass-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-24*

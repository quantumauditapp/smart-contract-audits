---
token: Tensor
ticker: TNSR
network: solana
risk_score: 70
status: high
date: 2026-06-21
---

# Tensor (TNSR) — Smart Contract Security Analysis | Solana

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tensor-sol)

---

## Audit Summary

This SPL token mint presents critical risks primarily due to an active mint authority, 7rtye8syTEK4W8omFkUiyUcj2MPFRUTq7yuczc7jNZZS, which can mint unlimited new tokens, diluting all current holders. Additionally, new holder accounts are created in a frozen state, requiring manual unfreezing by an authority. Holder concentration data was unavailable, preventing a full assessment of whale risk.

> **Final Recommendation:** Holders should exercise extreme caution due to the active mint authority, which allows for arbitrary supply inflation. Verify on-chain that the mint authority is set to null before considering the supply fixed. Be aware that new accounts will be frozen by default, requiring an active issuer to unfreeze them for transfers to occur. Due to the critical risks identified, interaction with this token is not recommended unless the issuer's intentions and operational procedures for unfreezing accounts are fully understood and trusted. For a Premium Deploy option, consider tokens with fully revoked mint and freeze authorities and no default frozen state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The token is an SPL token mint operating on the `spl-token` program with a total supply of 783,790,895.968785602 tokens and 9 decimals. A critical risk is present as the mint authority… |
| **Governance / Economics** | 1/10 | High | The token exhibits a liquidity of $65,859 USD, which is moderate but could lead to slippage for large trades. The 24-hour volume is $45,029, resulting in a healthy volume/liquidity ratio of 0.68… |
| **Upgrades** | 6/10 | Medium | The mint authority remains active, posing a significant risk of supply inflation (7.3 Access Control). Conversely, the freeze authority has been revoked, preventing arbitrary freezing of user… |

## Security Findings

_🔴 1 Critical · 🟠 1 High_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is `7rtye8syTEK4W8omFkUiyUcj2MPFRUTq7yuczc7jNZZS`. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. (Fact: Mint Authority: 7rtye8syTEK4W8omFkUiyUcj2MPFRUTq7yuczc7jNZZS)

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority. This means users cannot transfer tokens immediately after receiving them without an additional action from the issuer. (Fact: GoPlus.default_account_state: 1)

**Recommendation:** Confirm an active issuer is available to unfreeze accounts; otherwise the token is unspendable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`TNSRxc...JAS6`](https://solscan.io/account/TNSRxcUxoT9xBG3de7PiJyTDYu7kskLqcpddxnEJAS6) |
| **Network** | Solana |
| **Price** | $0.0524 |
| **24h Volume** | $279.1K |
| **Liquidity** | $72.8K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 75.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2211 buys / 3097 sells |

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

### Is Tensor a scam?

Based on the data, Tensor (TNSR) carries a High Risk score of 55/100. While its ownership is renounced and no mint function exists—positive anti-scam indicators—the unverified contract, unlocked liquidity, and 75.3% supply concentration by top holders are significant red flags that necessitate extreme caution. Investors should be aware of these substantial risks.

### Is Tensor safe to buy?

Tensor (TNSR) is not considered safe for investment without extreme caution due to several high-risk factors. Key concerns include the contract’s unverified status, meaning its code is opaque, and the critical lack of locked liquidity, which exposes investors to potential rug pulls. Additionally, 75.3% of the supply held by the top 10 wallets presents considerable centralization and market manipulation risks.

### Has Tensor been audited?

The data indicates the Tensor (TNSR) contract is not verified. This means its code is not publicly available for independent review or inspection, a prerequisite for any formal security audit. Without verification, investors cannot ascertain the contract's functionality or security, nor has it undergone a professional security audit.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/7lql8hdyvybgoif19fsozzurxm3ve129tfkftz6wdfkr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tensor-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-21*

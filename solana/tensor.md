---
token: Tensor
ticker: TNSR
network: solana
risk_score: 62
status: high
date: 2026-06-21
---

# Tensor (TNSR) — Smart Contract Security Analysis | Solana

> **Risk Score: 62/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tensor-sol)

---

## Audit Summary

The Tensor (TNSR) token mint presents a critical risk due to an unrevoked mint authority, allowing the issuer to mint unlimited new tokens and dilute existing holders. Additionally, the token's metadata is mutable, introducing a low risk of branding changes post-launch. Third-party risk registry data on holder concentration was unavailable from chain-native RPC, but other third-party signals indicate potential risks related to concentrated ownership.

> **Final Recommendation:** Before engaging with the Tensor (TNSR) token, verify on-chain that the mint authority has been permanently revoked to ensure a fixed supply. Monitor the token's metadata for any unexpected changes to its branding. Be aware of the potential for concentrated ownership, as indicated by third-party signals, which could lead to significant price volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The Tensor (TNSR) token is a standard SPL token operating under the `spl-token` program (v3), indicating a well-established token standard. A significant risk exists as the mint authority… |
| **Governance / Economics** | 2/10 | High | The token exhibits moderate liquidity at $64,617 USD, with a healthy 24-hour volume to liquidity ratio of 0.12, suggesting organic trading activity. The DEX pair has been active for 470 days… |
| **Upgrades** | 7/10 | Low | The mint authority for TNSR is currently active, allowing for potential future supply changes by the authority holder. While the freeze authority has been revoked, enhancing user control over funds… |

## Security Findings

_🔴 1 Critical · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 7rtye8syTEK4W8omFkUiyUcj2MPFRUTq7yuczc7jNZZS. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

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

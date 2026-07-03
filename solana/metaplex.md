---
token: Metaplex
ticker: MPLX
network: solana
risk_score: 60
status: high
date: 2026-07-03
---

# Metaplex (MPLX) — Smart Contract Security Analysis | Solana

> **Risk Score: 60/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metaplex-sol)

---

## Audit Summary

This audit of the Metaplex Token (MPLX) mint identifies critical risks primarily due to an unrevoked mint authority, allowing the holder of key BHkk3RTd4Ue6JnqXpa9QHTXbn575ycR8hxVmYx4E254k to mint unlimited tokens. Additionally, new holder accounts are created in a frozen state, requiring manual unfreezing. Holder concentration data was unavailable, preventing assessment of whale risk.

> **Final Recommendation:** Holders should exercise extreme caution due to the active mint authority (BHkk3RTd4Ue6JnqXpa9QHTXbn575ycR8hxVmYx4E254k), which can dilute all token holders at any time. It is strongly recommended to verify on-chain that the mint authority is set to null before considering the supply fixed. Additionally, be aware that new token accounts will be created in a frozen state, requiring an active issuer to unfreeze them for transfers to occur. If the issuer becomes unresponsive, tokens in new accounts could become unspendable.

## Security Analysis

This audit of the Metaplex Token (MPLX) mint identifies critical risks primarily due to an unrevoked mint authority, allowing the holder of key BHkk3RTd4Ue6JnqXpa9QHTXbn575ycR8hxVmYx4E254k to mint unlimited tokens. Additionally, new holder accounts are created in a frozen state, requiring manual unfreezing. Holder concentration data was unavailable, preventing assessment of whale risk.

Holders should exercise extreme caution due to the active mint authority (BHkk3RTd4Ue6JnqXpa9QHTXbn575ycR8hxVmYx4E254k), which can dilute all token holders at any time. It is strongly recommended to verify on-chain that the mint authority is set to null before considering the supply fixed. Additionally, be aware that new token accounts will be created in a frozen state, requiring an active issuer to unfreeze them for transfers to occur. If the issuer becomes unresponsive, tokens in new accounts could become unspendable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | 7.1 Architecture & 7.2 Code Security: The Metaplex Token (MPLX) is a standard SPL token operating under the `spl-token` program. The mint authority, held by BHkk3RTd4Ue6JnqXpa9QHTXbn575ycR8hxVmYx4E254 |
| **Governance / Economics** | 3/10 | High | 7.4 Economic: The token exhibits substantial liquidity with $1,945,247 USD on DEXs and a 24-hour trading volume of $2,749,225 USD. The volume/liquidity ratio is 1.41, which is within normal parameters |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades: The mint authority remains active, allowing for potential future supply changes. However, the freeze authority has been revoked, preventing future freezing of accounts by a central entit |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 1 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is BHkk3RTd4Ue6JnqXpa9QHTXbn575ycR8hxVmYx4E254k. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. (Fact: Mint Authority: BHkk3RTd4Ue6JnqXpa9QHTXbn575ycR8hxVmYx4E254k)

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority. (Fact: GoPlus.default_account_state: 1)

**Recommendation:** Confirm an active issuer is available to unfreeze accounts; otherwise the token is unspendable.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`METAew...Y18m`](https://solscan.io/account/METAewgxyPbgwsseH8T16a39CQ5VyVxZi9zXiDPY18m) |
| **Network** | Solana |
| **Price** | $0.03976 |
| **24h Volume** | $2.75M |
| **Liquidity** | $1.95M |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 64.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4448 buys / 4447 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/solana/bxrhw4q1wtrwjkj1c4nr4yjcrl2uusoju4g1bvenspzk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metaplex-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-03*

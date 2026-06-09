---
token: 🦎
ticker: LIZARD
network: solana
risk_score: 85
status: critical
date: 2026-05-12
---

# 🦎 (LIZARD) — Smart Contract Security Analysis | Solana

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-sol)

---

## Audit Summary

This audit of the 🦎 (LIZARD) SPL Token Mint reveals a critical inconsistency: the mint account is reported as uninitialized, yet external data indicates active trading and liquidity. This fundamental discrepancy poses a severe risk to users, as an uninitialized token cannot be traded or hold value. Key token metrics like supply and decimals are also unknown, further hindering a reliable assessment. While mint and freeze authorities are appropriately revoked, the overall lack of verifiable on-chain data and conflicting information necessitates extreme caution.

> **Final Recommendation:** The critical finding regarding the uninitialized state of the mint account, coupled with reported liquidity, presents a significant and immediate risk to potential users. This fundamental contradiction suggests either a severe data integrity issue or a deliberate attempt to mislead. Users are strongly advised to verify the token's initialization status directly on the Solana blockchain before any interaction. 

Given the high-risk profile, we recommend extreme caution. For projects seeking to establish trust and transparency, a Premium Deploy option would include a full audit of the token's smart contract, comprehensive on-chain data verification, and continuous monitoring to ensure all reported metrics align with the token's actual state.

## Security Analysis

This audit of the 🦎 (LIZARD) SPL Token Mint reveals a critical inconsistency: the mint account is reported as uninitialized, yet external data indicates active trading and liquidity. This fundamental discrepancy poses a severe risk to users, as an uninitialized token cannot be traded or hold value. Key token metrics like supply and decimals are also unknown, further hindering a reliable assessment. While mint and freeze authorities are appropriately revoked, the overall lack of verifiable on-chain data and conflicting information necessitates extreme caution.

The critical finding regarding the uninitialized state of the mint account, coupled with reported liquidity, presents a significant and immediate risk to potential users. This fundamental contradiction suggests either a severe data integrity issue or a deliberate attempt to mislead. Users are strongly advised to verify the token's initialization status directly on the Solana blockchain before any interaction. 

Given the high-risk profile, we recommend extreme caution. For projects seeking to establish trust and transparency, a Premium Deploy option would include a full audit of the token's smart contract, comprehensive on-chain data verification, and continuous monitoring to ensure all reported metrics align with the token's actual state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The technical assessment reveals a critical inconsistency: the token mint account is reported as uninitialized (`Initialized: False`), yet external data sources indicate active trading and significant |
| **Governance / Economics** | 6/10 | Medium | From a governance and economic perspective, the token exhibits a mixed profile. A significant strength is the revocation of both Mint Authority and Freeze Authority, which prevents further token issua |
| **Upgrades** | 6/10 | Low | The token mint account itself is a data structure governed by the SPL Token Program, which is maintained by Solana Labs. As such, the mint account is not directly upgradable by the token's creators, p |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 2 Informational_

### `C-01` — Uninitialized Mint Account with Reported Liquidity  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account is reported as `Initialized: False`. However, external data from dexscreener indicates significant liquidity ($34,460) and trading volume ($7,377) associated with this address. An uninitialized SPL Token Mint cannot be traded, hold value, or have a defined supply/decimals. This severe data inconsistency suggests a potential scam or a critical misrepresentation of the token's operational status, posing an immediate threat to user funds.

**Recommendation:** Users should exercise extreme caution and verify the actual initialization status of the mint account directly on-chain using Solana explorers or RPC calls. Do not interact with this token if it is indeed uninitialized, as any reported liquidity or trading activity would be misleading or fraudulent.


### `H-01` — Lack of Transparency on Core Token Metrics  *(Severity: High · Status: Unresolved)*

Key token metrics such as `Supply (raw)`, `Decimals`, and `Holder distribution` are reported as `unknown`. This lack of fundamental transparency prevents users from accurately assessing the token's economic properties, including total dilution, potential inflation, or concentration risks. This issue is exacerbated by the `Initialized: False` status, which inherently means these details would be undefined.

**Recommendation:** For any legitimate token, all critical metadata should be publicly verifiable and accessible on-chain. Users should avoid tokens where such fundamental economic data is unavailable or obscured, as it hinders informed decision-making and increases investment risk.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Unresolved)*

Both the `Mint Authority` and `Freeze Authority` for the token have been `revoked (None)`. This means no new tokens can be minted into circulation, and no individual token accounts can be frozen by a central authority.

**Recommendation:** This is generally considered a positive security practice for established tokens, as it removes central control over token supply and user assets, enhancing decentralization and reducing the risk of arbitrary inflation or censorship. However, it also means there is no mechanism for the project team to mint tokens for ecosystem growth or to freeze malicious accounts in case of an exploit.


### `I-02` — Absence of External Security Signals  *(Severity: Informational · Status: Unresolved)*

Data from external security auditors and risk assessment platforms, specifically GoPlus Solana and RugCheck, is `unavailable`. This means there is no independent third-party assessment or automated red-flag analysis available for this token.

**Recommendation:** While not a direct vulnerability, the absence of external security signals means users must rely solely on available on-chain data and their own due diligence. This is particularly challenging given the other identified data inconsistencies and lack of transparency, increasing the burden on individual users to assess risk.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`347k5f...bonk`](https://solscan.io/account/347k5f1wlrye81rorclbwdr6k3ecrunaqetqpw6pbonk) |
| **Network** | Solana |
| **Price** | $0.0001683 |
| **24h Volume** | $206.8K |
| **Liquidity** | $58.6K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 9mo |
| **Top-10 Holders** | N/A of supply |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gcgn1netxzanrvfzfno1w1br5vdvug7mysxdcgsrfsm4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-12*

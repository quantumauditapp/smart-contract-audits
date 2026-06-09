---
token: Official Bridge Currency
ticker: OBC
network: solana
risk_score: 85
status: critical
date: 2026-05-12
---

# Official Bridge Currency (OBC) — Smart Contract Security Analysis | Solana

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/official-bridge-currency-sol)

---

## Audit Summary

The audit of the Official Bridge Currency (OBC) SPL Token Mint reveals a critical issue: the token mint is uninitialized. This fundamental flaw prevents the token from functioning correctly, despite positive indicators regarding revoked authorities and immutable configurations. Any liquidity associated with this token is at significant risk due to its non-functional state.

> **Final Recommendation:** It is critically important to address the uninitialized state of the Official Bridge Currency (OBC) SPL Token Mint. If the intention is for this token to be functional, it must be properly initialized to define its supply, decimals, and enable minting. Failure to do so means any existing liquidity is paired with a non-functional asset, posing a significant risk to all participants. If the token cannot be initialized, all associated liquidity should be withdrawn, and the token considered defunct. For future token deployments, consider a Premium Deploy option that includes pre-deployment verification of all critical parameters, ensuring the token is fully functional and secure from inception.

## Security Analysis

The audit of the Official Bridge Currency (OBC) SPL Token Mint reveals a critical issue: the token mint is uninitialized. This fundamental flaw prevents the token from functioning correctly, despite positive indicators regarding revoked authorities and immutable configurations. Any liquidity associated with this token is at significant risk due to its non-functional state.

It is critically important to address the uninitialized state of the Official Bridge Currency (OBC) SPL Token Mint. If the intention is for this token to be functional, it must be properly initialized to define its supply, decimals, and enable minting. Failure to do so means any existing liquidity is paired with a non-functional asset, posing a significant risk to all participants. If the token cannot be initialized, all associated liquidity should be withdrawn, and the token considered defunct. For future token deployments, consider a Premium Deploy option that includes pre-deployment verification of all critical parameters, ensuring the token is fully functional and secure from inception.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The primary technical concern (7.2 Code Security) is the uninitialized state of the SPL Token Mint, rendering it non-functional. While positive aspects include revoked Mint and Freeze Authorities (7.3 |
| **Governance / Economics** | 6/10 | High | The economic viability (7.4 Economic) of the Official Bridge Currency is severely compromised by its uninitialized state. Despite having $4,603 in liquidity, this capital is effectively tied to a non- |
| **Upgrades** | 6/10 | Low | SPL Token Mints are not directly upgradeable in the context of their specific parameters once initialized. The underlying SPL Token Program (7.7 Upgrades) is managed by Solana governance, but this aud |

## Security Findings

_🔴 1 Critical · ⚪ 2 Informational_

### `C-01` — Uninitialized SPL Token Mint  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint for 'Official Bridge Currency (OBC)' at address `2necwdgejstlv2yrfmsjtindwyvj7snnucqjwgc5ydk1` is reported as `Initialized: False`. An uninitialized token mint cannot function correctly; it lacks defined supply, decimals, and the ability to mint new tokens. This renders the token non-functional and any associated liquidity effectively tied to a non-existent asset.

**Recommendation:** The token mint must be properly initialized to become functional. This involves setting the supply, decimals, and potentially the mint authority. If initialization is not possible or intended, all associated liquidity should be withdrawn, and the token considered non-viable to prevent further economic loss.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Unresolved)*

The Mint Authority and Freeze Authority for the Official Bridge Currency (OBC) token have both been revoked (`None`). This is a positive security practice, as it prevents further token minting or freezing of token accounts by a central authority, enhancing decentralization and reducing potential for malicious control. However, this positive aspect is currently overshadowed by the uninitialized state of the mint.

**Recommendation:** Maintain revoked authorities once the token is properly initialized and fully deployed. This configuration is generally recommended for fully decentralized tokens.


### `I-02` — Immutable Token Configuration  *(Severity: Informational · Status: Unresolved)*

External security signals indicate that several key token properties are immutable, including `balance_mutable: False`, `closable: False`, `freezable: False`, `non_transferable: False`, `transfer_fee_upgradable: False`, `transfer_hook_upgradable: False`, and `metadata_mutable: False`. These settings prevent unauthorized modifications to token behavior, fees, or metadata post-deployment, contributing to predictable and secure token operations. This is a strong security posture for a token, assuming it becomes functional.

**Recommendation:** Ensure these immutable configurations remain in place. This design choice enhances trust and predictability for token holders. This is a good practice for token deployments.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2necwd...ydk1`](https://solscan.io/account/2necwdgejstlv2yrfmsjtindwyvj7snnucqjwgc5ydk1) |
| **Network** | Solana |
| **Price** | $0.002121 |
| **24h Volume** | $332.5K |
| **Liquidity** | $69.0K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 5d |
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

- [View on DexScreener](https://dexscreener.com/solana/drkhakh4eb7ncrs5odcowbvjcrasuazbtxvedezaaxkm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/official-bridge-currency-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-12*

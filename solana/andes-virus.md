---
token: Andes Virus
ticker: ANDV
network: solana
risk_score: 35
status: medium
date: 2026-05-14
---

# Andes Virus (ANDV) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/andes-virus-sol)

---

## Audit Summary

The Andes Virus (ANDV) SPL Token Mint is currently uninitialized, preventing any token operations. While Mint and Freeze Authorities are revoked, indicating a secure configuration post-initialization, the token cannot function until it is properly initialized. Key details like decimals and total supply are unknown due to this uninitialized state. The token exhibits normal liquidity and volume ratios for its age.

> **Final Recommendation:** The Andes Virus (ANDV) SPL Token Mint is currently in an uninitialized state, rendering it non-functional. While the revocation of Mint and Freeze Authorities indicates a strong security posture against centralized control post-initialization, this state prevents any token operations, including issuance or trading. It is imperative to properly initialize the mint to define its decimals and supply, enabling its intended use. Users should exercise caution until the mint is fully initialized and its parameters are confirmed.

## Security Analysis

The Andes Virus (ANDV) SPL Token Mint is currently uninitialized, preventing any token operations. While Mint and Freeze Authorities are revoked, indicating a secure configuration post-initialization, the token cannot function until it is properly initialized. Key details like decimals and total supply are unknown due to this uninitialized state. The token exhibits normal liquidity and volume ratios for its age.

The Andes Virus (ANDV) SPL Token Mint is currently in an uninitialized state, rendering it non-functional. While the revocation of Mint and Freeze Authorities indicates a strong security posture against centralized control post-initialization, this state prevents any token operations, including issuance or trading. It is imperative to properly initialize the mint to define its decimals and supply, enabling its intended use. Users should exercise caution until the mint is fully initialized and its parameters are confirmed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token mint has both its Mint Authority and Freeze Authority revoked, which is a strong security posture against unauthorized token creation or asset freezing (7.3 Access Control). This prevents po |
| **Governance / Economics** | 6/10 | Low | The token exhibits a normal Volume/Liquidity Ratio of 0.10, suggesting healthy trading activity relative to its liquidity (7.4 Economic). With revoked authorities, there is no centralized governance o |
| **Upgrades** | 6/10 | Low | As an SPL Token Mint with revoked authorities, the core parameters are immutable once initialized, providing predictability and preventing unauthorized changes (7.7 Upgrades). This design choice enhan |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Uninitialized SPL Token Mint  *(Severity: Medium · Status: Unresolved)*

The SPL Token Mint is reported as `Initialized: False`. An uninitialized mint cannot be used to create tokens or perform any token operations. This state prevents the token from functioning as intended and could indicate an incomplete deployment or an error in the initialization process.

**Recommendation:** The mint must be properly initialized by calling the `InitializeMint` instruction of the SPL Token Program. This will set the supply, decimals, and assign authorities (or confirm their revocation).


### `L-01` — Unknown Decimals  *(Severity: Low · Status: Unresolved)*

The number of decimals for the token is reported as `unknown`. While this is a direct consequence of the mint being uninitialized, it means users cannot accurately determine the token's divisibility. This lack of information is crucial for correct display and interaction with the token in wallets and exchanges.

**Recommendation:** Ensure the mint is initialized with a clearly defined number of decimals. This information should be readily available to users post-initialization.


### `I-01` — Unknown Supply  *(Severity: Informational · Status: Unresolved)*

The total supply of the token is reported as `unknown`. This is an expected state for an uninitialized mint. Once initialized, the supply will be set, and if a mint authority were present and not revoked, it could potentially be changed.

**Recommendation:** After initialization, the total supply will be established. If the intention is for a fixed-supply token, ensure the mint authority remains revoked.


### `I-02` — Revoked Authorities  *(Severity: Informational · Status: Unresolved)*

Both Mint Authority and Freeze Authority are reported as `revoked (None)`. This indicates that no new tokens can be minted (unless re-enabled by a new authority, which is unlikely for a revoked state) and no tokens can be frozen. This is generally a positive security feature for a fixed-supply token, preventing malicious inflation or arbitrary freezing of user funds. However, given the mint is uninitialized, these revocations are currently moot as the token cannot function.

**Recommendation:** If the intention is for a fixed-supply, non-freezable token, maintaining revoked authorities post-initialization is a good practice to enhance trust and security.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`jvktlf...pump`](https://solscan.io/account/jvktlflnngpm7eds9kepyqpxuy8hpgtzohlfm4spump) |
| **Network** | Solana |
| **Price** | $0.0004631 |
| **24h Volume** | $189.8K |
| **Liquidity** | $67.6K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 7d |
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

- [View on DexScreener](https://dexscreener.com/solana/jhmcrrlmpte1qvypwe1yjtjzm2k44eorpducj6j8pwc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/andes-virus-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-14*

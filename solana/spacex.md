---
token: SpaceX
ticker: SPCX
network: solana
risk_score: 90
status: critical
date: 2026-05-23
---

# SpaceX (SPCX) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-sol)

---

## Audit Summary

The audit of the SpaceX (SPCX) SPL Token Mint reveals a critical issue: the mint account is reported as 'Initialized: False' despite having significant liquidity and trading volume. This state means the token's fundamental properties (like supply and decimals) are unset, and it is not functional for token operations. Both mint and freeze authorities have been revoked, which, combined with the uninitialized state, creates an irreversible non-functional token. Users are trading a token that is technically not properly configured on-chain, posing a severe risk of loss of funds.

> **Final Recommendation:** Given the critical uninitialized state of the SPL Token Mint account and the irreversible revocation of its authorities, this token is fundamentally flawed and poses a severe risk to holders. It is strongly recommended that users exercise extreme caution and avoid trading or holding this token until its on-chain state is corrected and verified as fully initialized and functional. The current configuration suggests a high potential for loss of funds due to misrepresentation or an unrecoverable error in token deployment. For future token deployments, it is crucial to ensure proper initialization and configuration of all token properties before any liquidity is provided or trading commences. A 'Premium Deploy' option would involve a thorough pre-deployment audit to prevent such critical misconfigurations, ensuring all SPL token properties are correctly set and verified on-chain before publ…

## Security Analysis

The audit of the SpaceX (SPCX) SPL Token Mint reveals a critical issue: the mint account is reported as 'Initialized: False' despite having significant liquidity and trading volume. This state means the token's fundamental properties (like supply and decimals) are unset, and it is not functional for token operations. Both mint and freeze authorities have been revoked, which, combined with the uninitialized state, creates an irreversible non-functional token. Users are trading a token that is technically not properly configured on-chain, posing a severe risk of loss of funds.

Given the critical uninitialized state of the SPL Token Mint account and the irreversible revocation of its authorities, this token is fundamentally flawed and poses a severe risk to holders. It is strongly recommended that users exercise extreme caution and avoid trading or holding this token until its on-chain state is corrected and verified as fully initialized and functional. The current configuration suggests a high potential for loss of funds due to misrepresentation or an unrecoverable error in token deployment. For future token deployments, it is crucial to ensure proper initialization and configuration of all token properties before any liquidity is provided or trading commences. A 'Premium Deploy' option would involve a thorough pre-deployment audit to prevent such critical misconfigurations, ensuring all SPL token properties are correctly set and verified on-chain before publ…

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical state of the SPL Token Mint account is critically flawed (7.2 Code Security). The account is marked as 'Initialized: False', meaning its core properties are unset and it cannot perform t |
| **Governance / Economics** | 6/10 | High | The economic implications are severe (7.4 Economic). Users are trading a token with significant liquidity and volume that is fundamentally non-functional due to its uninitialized state. This creates a |
| **Upgrades** | 6/10 | Low | The SPL Token Program itself is a core Solana program and is not subject to frequent upgrades that would impact individual mint accounts in this manner (7.7 Upgrades). The mint account's state is immu |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account `e6ifp2mjy8cyqehugutfvrxrirkxruonlmrvtfypump` is reported as `Initialized: False`. This means the token's core properties (like supply, decimals) have not been set, and the mint account is not functional for token operations. Despite this critical state, the token has significant liquidity ($261,151 USD) and trading volume ($636,198 USD), indicating that users are actively trading a non-functional asset.

**Recommendation:** A token mint account must be properly initialized before any tokens are issued or traded. Users should be aware that trading an uninitialized token carries extreme risk, as the token's properties could be set arbitrarily later (if authorities were not revoked) or it may never become functional. Immediate action is required to cease trading and inform holders.


### `H-01` — Irreversible Revocation of Authorities on Uninitialized Mint  *(Severity: High · Status: Unresolved)*

Both the Mint Authority and Freeze Authority for the `SPCX` token have been revoked (`None`), while the mint account itself is `Initialized: False`. This combination creates an irreversible state where the token cannot be properly initialized, its properties cannot be set, and no tokens can ever be minted or frozen. This effectively renders the token permanently non-functional and unmanageable.

**Recommendation:** Authorities should only be revoked *after* a token mint has been fully initialized and its properties (like decimals and supply) are correctly set and immutable. Revoking authorities on an uninitialized mint creates an irreversible state of non-functionality, making the token unusable.


### `M-01` — Lack of Transparency for Key Token Properties  *(Severity: Medium · Status: Unresolved)*

Due to the `Initialized: False` state of the mint account, crucial token properties such as `Supply (raw)` and `Decimals` are `unknown`. This lack of on-chain transparency prevents users from understanding the token's fundamental economic characteristics, such as its total supply or divisibility, which are essential for informed trading decisions.

**Recommendation:** For any token intended for public trading, all essential properties, including total supply and decimals, must be clearly defined and verifiable on-chain. This requires proper initialization of the mint account before any public engagement or liquidity provision.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`e6ifp2...pump`](https://solscan.io/account/e6ifp2mjy8cyqehugutfvrxrirkxruonlmrvtfypump) |
| **Network** | Solana |
| **Price** | $0.001361 |
| **24h Volume** | $383.0K |
| **Liquidity** | $129.8K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 1mo |
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

- [View on DexScreener](https://dexscreener.com/solana/dzxwcypptyr2ntfmen2xauscb77t1zlpkg63pbpbkmbc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-23*

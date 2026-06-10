---
token: Chinese Digital Oil Fund
ticker: CDOF
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# Chinese Digital Oil Fund (CDOF) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chinese-digital-oil-fund-sol)

---

## Audit Summary

This audit report for the Chinese Digital Oil Fund (CDOF) SPL Token Mint identifies a critical state inconsistency: the mint account is reported as uninitialized despite having significant active liquidity. This fundamental contradiction poses severe risks to the token's integrity and user funds. Additionally, key token metadata such as supply and decimals are unavailable, hindering a complete economic assessment. While mint and freeze authorities are appropriately revoked, the critical initialization issue and lack of transparency warrant extreme caution.

> **Final Recommendation:** Given the critical finding of an uninitialized SPL Token Mint account with active liquidity, extreme caution is advised for all interactions with the Chinese Digital Oil Fund (CDOF) token. This fundamental inconsistency poses a significant risk to user funds and the token's operational integrity. It is imperative to verify the true on-chain state of the mint account and the program owning it before any further engagement.

For future token deployments, we recommend a Premium Deploy option to ensure all token accounts are correctly initialized, all critical metadata is publicly available, and the token program is explicitly identified and, if custom, thoroughly audited. This proactive approach ensures transparency, reduces operational risks, and builds trust within the Solana ecosystem.

## Security Analysis

This audit report for the Chinese Digital Oil Fund (CDOF) SPL Token Mint identifies a critical state inconsistency: the mint account is reported as uninitialized despite having significant active liquidity. This fundamental contradiction poses severe risks to the token's integrity and user funds. Additionally, key token metadata such as supply and decimals are unavailable, hindering a complete economic assessment. While mint and freeze authorities are appropriately revoked, the critical initialization issue and lack of transparency warrant extreme caution.

Given the critical finding of an uninitialized SPL Token Mint account with active liquidity, extreme caution is advised for all interactions with the Chinese Digital Oil Fund (CDOF) token. This fundamental inconsistency poses a significant risk to user funds and the token's operational integrity. It is imperative to verify the true on-chain state of the mint account and the program owning it before any further engagement.

For future token deployments, we recommend a Premium Deploy option to ensure all token accounts are correctly initialized, all critical metadata is publicly available, and the token program is explicitly identified and, if custom, thoroughly audited. This proactive approach ensures transparency, reduces operational risks, and builds trust within the Solana ecosystem.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | 7.1 Architecture & 7.2 Code Security: The primary technical concern is the reported 'Initialized: False' state for the SPL Token Mint account, which critically contradicts the presence of active liqui |
| **Governance / Economics** | 6/10 | High | 7.4 Economic & 7.5 Governance: The economic risk is significantly elevated due to the unavailability of crucial token metadata, specifically 'Supply (raw)' and 'Decimals'. This lack of transparency pr |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: SPL Token Mint accounts are data structures managed by the SPL Token Program, not upgradable programs themselves. Therefore, direct upgradeability risks for this specific account are not |

## Security Findings

_🔴 1 Critical · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Uninitialized Mint Account with Active Liquidity  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account `cdofug7k6gygiotxw1vcyfc9p4rdaxnbbj2dch5ae4az` is reported as `Initialized: False`. However, it has significant active liquidity of `$282,475` and a 24h trading volume of `$314,781`. An uninitialized SPL Token Mint account should not be functional or hold any supply. This contradiction indicates a severe state inconsistency, a potential misinterpretation of the account's true nature, or a critical flaw in how the token is managed, potentially leading to unexpected behavior, loss of funds, or an inability to interact with the token as expected by standard SPL Token Program rules.

**Recommendation:** Immediately investigate the on-chain state of the mint account using Solana RPC to confirm its initialization status and the program that owns it. If it is truly uninitialized but has liquidity, all interactions with this token should cease until the discrepancy is resolved and the token's operational integrity is verified. Users should be warned of potential risks.


### `L-01` — Ambiguous Token Program Identification  *(Severity: Low · Status: Unresolved)*

The 'Token Program' responsible for managing this mint account is reported as `unknown`. Standard SPL Token Mints are managed by the well-known and audited SPL Token Program (e.g., `TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA`). An unknown token program introduces uncertainty regarding the underlying logic, security, and adherence to standard token functionalities. If it's a custom program, it lacks public audit assurance.

**Recommendation:** Verify the actual program ID that owns this mint account on-chain. If it is not the standard SPL Token Program, its source code should be obtained and thoroughly audited to ensure it implements token functionalities correctly and securely, without backdoors or vulnerabilities.


### `I-01` — Missing Key Token Metadata  *(Severity: Informational · Status: Unresolved)*

Critical metadata such as `Supply (raw)` and `Decimals` for the `Chinese Digital Oil Fund (CDOF)` token are reported as `unknown`. These details are fundamental for understanding the token's economic model, total market capitalization, and how it should be displayed and interacted with by wallets and exchanges. The absence of this information hinders a complete risk assessment and user understanding.

**Recommendation:** The token issuer or data provider should ensure that all essential token metadata, including total supply and decimals, is accurately and publicly available. This information is crucial for transparency and informed decision-making by users and integrators.


### `I-02` — Lack of Holder Distribution Data  *(Severity: Informational · Status: Unresolved)*

Information regarding the `holder concentration` or distribution of the `Chinese Digital Oil Fund (CDOF)` token is `unavailable`. This prevents an assessment of centralization risks, such as potential price manipulation by large holders (whales) or the ability of a few entities to control a significant portion of the token supply.

**Recommendation:** Implement or integrate with services that provide transparent holder distribution data. Publicly available holder distribution insights enhance transparency and allow users to assess the decentralization and potential market manipulation risks associated with the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`cdofug...e4az`](https://solscan.io/account/cdofug7k6gygiotxw1vcyfc9p4rdaxnbbj2dch5ae4az) |
| **Network** | Solana |
| **Price** | $0.009503 |
| **24h Volume** | $314.9K |
| **Liquidity** | $282.5K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 14d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2477 buys / 997 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2j8va5luscsdjq8gt4huz2cukttbrfpdswhvouqfrh5v)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chinese-digital-oil-fund-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*

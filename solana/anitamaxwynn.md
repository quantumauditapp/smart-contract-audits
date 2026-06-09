---
token: AnitaMaxWynn
ticker: WYNN
network: solana
risk_score: 90
status: critical
date: 2026-05-21
---

# AnitaMaxWynn (WYNN) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anitamaxwynn-sol)

---

## Audit Summary

This audit report assesses the AnitaMaxWynn (WYNN) SPL Token Mint based on available on-chain metadata. The analysis reveals critical data inconsistencies, such as the mint account being reported as uninitialized despite active trading, and an 'unknown' token program. While mint and freeze authorities are appropriately revoked, significant transparency gaps exist regarding token supply, decimals, and holder distribution. Users are advised to exercise extreme caution due to these fundamental data discrepancies and lack of critical information.

> **Final Recommendation:** The AnitaMaxWynn (WYNN) SPL Token Mint presents significant risks primarily due to fundamental data inconsistencies and a lack of transparency regarding critical token parameters. The reported 'uninitialized' state combined with active trading is a major red flag that warrants immediate investigation. Users should exercise extreme caution and verify all token details independently before engaging with this asset. It is strongly recommended that the project team clarify the status of the mint account, the associated token program, and provide full transparency on supply, decimals, and holder distribution. 

For future projects, consider a Premium Deploy option that includes a comprehensive pre-launch audit to identify and mitigate such critical issues, ensuring data integrity and transparency from inception.

## Security Analysis

This audit report assesses the AnitaMaxWynn (WYNN) SPL Token Mint based on available on-chain metadata. The analysis reveals critical data inconsistencies, such as the mint account being reported as uninitialized despite active trading, and an 'unknown' token program. While mint and freeze authorities are appropriately revoked, significant transparency gaps exist regarding token supply, decimals, and holder distribution. Users are advised to exercise extreme caution due to these fundamental data discrepancies and lack of critical information.

The AnitaMaxWynn (WYNN) SPL Token Mint presents significant risks primarily due to fundamental data inconsistencies and a lack of transparency regarding critical token parameters. The reported 'uninitialized' state combined with active trading is a major red flag that warrants immediate investigation. Users should exercise extreme caution and verify all token details independently before engaging with this asset. It is strongly recommended that the project team clarify the status of the mint account, the associated token program, and provide full transparency on supply, decimals, and holder distribution. 

For future projects, consider a Premium Deploy option that includes a comprehensive pre-launch audit to identify and mitigate such critical issues, ensuring data integrity and transparency from inception.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | 7.1 Architecture & 7.2 Code Security: The mint account is reported as 'Initialized: False' despite having active liquidity and trading volume, indicating a critical data inconsistency or fundamental m |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic & 7.5 Governance: The token exhibits active trading with a normal volume/liquidity ratio over 25 days. However, critical economic parameters such as total supply and decimals are 'unknown |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: As an SPL Token Mint, the underlying program logic is managed by the Solana Program Library and is not directly upgradeable by the token creator. This provides a stable and immutable fou |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Uninitialized Mint Account with Active Trading  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account is reported as 'Initialized: False'. However, the token (WYNN) has active liquidity ($47,789) and trading volume ($73,618) on decentralized exchanges. An uninitialized mint account should not be functional or tradable. This fundamental inconsistency indicates either a critical data reporting error or a severe misconfiguration of the token, which could lead to unpredictable behavior, loss of funds, or an inability to interact with the token as expected.

**Recommendation:** The project team must immediately clarify the true initialization status of the mint account. If the account is indeed uninitialized, all trading should cease, and the token should be re-evaluated. If the data source is incorrect, the project should provide verifiable on-chain proof of proper initialization.


### `H-01` — Unknown Token Program  *(Severity: High · Status: Unresolved)*

The 'Token Program' associated with the mint address is reported as 'unknown'. While the 'SOLC_VERSION' indicates 'SPL Token (Token Program v3)', the 'unknown' status in the on-chain facts is concerning. If the token is not governed by the standard, audited SPL Token Program (TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA), it implies a custom or non-standard token program. Custom token programs introduce significant security risks as they may contain unaudited vulnerabilities, backdoors, or unexpected behaviors.

**Recommendation:** The project team should explicitly state and verify the exact program ID governing this token mint. If it is a custom program, a full security audit of its source code is essential to ensure its integrity and security. If it is the standard SPL Token Program, the data source should be corrected to reflect this.


### `M-01` — Undisclosed Token Supply and Decimals  *(Severity: Medium · Status: Unresolved)*

Critical token parameters, including the total supply (raw) and decimals, are reported as 'unknown'. This lack of transparency prevents users and investors from understanding the token's fundamental economic model, such as its total issuance, potential for inflation/deflation, and how token values are calculated. This opacity hinders proper risk assessment and can lead to misinformed decisions.

**Recommendation:** The project team should ensure that the total supply and decimals are publicly verifiable and clearly communicated. This information is crucial for market participants to accurately assess the token's value and economic viability.


### `M-02` — Lack of Holder Distribution Data  *(Severity: Medium · Status: Unresolved)*

Information regarding the token's holder concentration and distribution is unavailable. Without this data, it is impossible to assess the level of centralization within the token's ownership. High concentration among a few holders could pose risks such as market manipulation, significant price volatility, or potential 'rug pull' scenarios if large holders decide to liquidate their positions simultaneously.

**Recommendation:** The project should provide access to verifiable token holder distribution data. This transparency allows the community to assess centralization risks and make informed decisions about participating in the token's ecosystem.


### `L-01` — Absence of External Security Signals  *(Severity: Low · Status: Unresolved)*

External security signals from reputable services like GoPlus Solana data and RugCheck are reported as unavailable. The absence of these independent assessments reduces the overall confidence in the token's security posture and legitimacy, as there is no third-party validation of potential risks or red flags.

**Recommendation:** The project team should aim to obtain and publish security assessments from recognized third-party services. This can significantly enhance trust and provide an additional layer of due diligence for potential users and investors.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Resolved)*

Both the Mint Authority and Freeze Authority for the token have been revoked. This is a positive security measure. Revoking the Mint Authority prevents any further issuance of tokens, ensuring a fixed supply (once known). Revoking the Freeze Authority prevents any entity from freezing token accounts, enhancing decentralization and user control over their assets.

**Recommendation:** Maintain the revoked status of these authorities to uphold the token's immutability and decentralization properties.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`cvxywj...pump`](https://solscan.io/account/cvxywjrq3zxqifmzauyuomdvj8pf8nitxx8hxrlgpump) |
| **Network** | Solana |
| **Price** | $0.001043 |
| **24h Volume** | $183.8K |
| **Liquidity** | $89.7K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 6d |
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

- [View on DexScreener](https://dexscreener.com/solana/5gp2nmgddgx48qjsrj54mhlljvxxkmk5gyvdyqh2dae2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anitamaxwynn-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-21*

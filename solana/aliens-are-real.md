---
token: Aliens are real
ticker: ALIENS
network: solana
risk_score: 90
status: critical
date: 2026-05-12
---

# Aliens are real (ALIENS) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aliens-are-real-sol)

---

## Audit Summary

This report details a security assessment of the 'Aliens are real' SPL Token Mint on Solana. Key findings include a critical inconsistency where the mint account is reported as uninitialized despite significant trading activity, an unknown token program ID, and a lack of essential token metadata. These issues collectively pose substantial risks to users, indicating potential data integrity problems or a non-functional asset.

> **Final Recommendation:** Users are strongly advised to exercise extreme caution when interacting with the 'Aliens are real' token. The critical inconsistency between the reported uninitialized mint account status and active trading data, coupled with an unknown token program, suggests a high likelihood of data integrity issues or a non-functional asset. Further investigation into the token's true state and associated program is essential before any engagement. 

For projects seeking to deploy a robust and secure SPL token, a Premium Deploy option is recommended. This includes a comprehensive pre-deployment audit, verification of all on-chain metadata, and integration with trusted security monitoring services to ensure transparency and functionality from inception.

## Security Analysis

This report details a security assessment of the 'Aliens are real' SPL Token Mint on Solana. Key findings include a critical inconsistency where the mint account is reported as uninitialized despite significant trading activity, an unknown token program ID, and a lack of essential token metadata. These issues collectively pose substantial risks to users, indicating potential data integrity problems or a non-functional asset.

Users are strongly advised to exercise extreme caution when interacting with the 'Aliens are real' token. The critical inconsistency between the reported uninitialized mint account status and active trading data, coupled with an unknown token program, suggests a high likelihood of data integrity issues or a non-functional asset. Further investigation into the token's true state and associated program is essential before any engagement. 

For projects seeking to deploy a robust and secure SPL token, a Premium Deploy option is recommended. This includes a comprehensive pre-deployment audit, verification of all on-chain metadata, and integration with trusted security monitoring services to ensure transparency and functionality from inception.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical assessment (7.2 Code Security, 7.3 Access Control) reveals critical issues. The mint account is reported as uninitialized, which fundamentally contradicts the presence of active trading  |
| **Governance / Economics** | 6/10 | High | The economic assessment (7.4 Economic) is severely hampered by a lack of fundamental data. Supply, decimals, and holder distribution are all unknown, making it impossible to evaluate tokenomics or pot |
| **Upgrades** | 6/10 | Low | As an SPL Token Mint, this account is not directly upgradeable in the traditional sense of a program. Its functionality is governed by the underlying token program, which is reported as unknown. There |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Uninitialized Mint Account with Active Trading Data  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account is reported as 'Initialized: False', which means it has not been properly configured to function as a token mint. However, the token also reports significant liquidity ($120,456 USD) and 24-hour trading volume ($27,539 USD). This is a critical contradiction: an uninitialized mint cannot issue tokens or support trading. This inconsistency indicates severe data integrity issues or that the token is fundamentally non-functional, posing an extreme risk of user funds being lost or transactions failing.

**Recommendation:** Immediately investigate the discrepancy between the mint's initialization status and reported trading activity. Verify the true initialization state of the mint account directly on-chain. If the mint is indeed uninitialized, all associated trading data should be considered erroneous or indicative of a scam. Users should be warned against interacting with this token until this critical inconsistency is resolved.


### `H-01` — Unknown Token Program ID  *(Severity: High · Status: Unresolved)*

The 'Token Program' associated with this mint is reported as 'unknown'. For standard SPL tokens, this should be the well-known Solana Program Library Token Program ID (TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA). An unknown program ID prevents verification of the token's underlying logic, raising concerns about its legitimacy, security, and adherence to standard token functionalities. It could indicate a custom, unaudited, or potentially malicious program.

**Recommendation:** Identify and verify the exact program ID governing this token mint. If it's a custom program, a full security audit of its source code is essential to ensure it adheres to security best practices and does not contain vulnerabilities. If the program ID cannot be determined, the token should be treated with extreme caution.


### `M-01` — Lack of Fundamental Token Data  *(Severity: Medium · Status: Unresolved)*

Essential token metadata such as 'Supply (raw)', 'Decimals', and 'Holder distribution' are all reported as 'unknown' or 'unavailable'. This lack of transparency makes it impossible to assess the token's economic structure, total market capitalization, or distribution among holders. Without this information, users cannot evaluate potential risks like concentrated ownership, rug pull potential, or inflationary/deflationary mechanics.

**Recommendation:** Ensure all fundamental token metadata is publicly available and verifiable on-chain. Projects should provide clear documentation regarding token supply, decimals, and distribution to foster transparency and allow users to make informed decisions. Until this data is available, users should be aware of the increased economic risk.


### `L-01` — Absence of External Security Signals  *(Severity: Low · Status: Unresolved)*

External security signals from reputable services like GoPlus Solana data and RugCheck are reported as 'unavailable'. The absence of these third-party assessments means there is no independent validation of the token's security posture or potential red flags, increasing the burden of due diligence on individual users.

**Recommendation:** Seek evaluation from established blockchain security analytics platforms (e.g., GoPlus, RugCheck) to provide additional layers of trust and transparency. While not a direct vulnerability, the lack of such signals contributes to overall project risk and user uncertainty.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Resolved)*

Both the 'Mint Authority' and 'Freeze Authority' for this SPL Token Mint are reported as 'revoked (None)'. This is a positive security practice, indicating that no new tokens can be minted by any authority and no existing tokens can be frozen in user accounts. This reduces the risk of inflationary attacks or arbitrary asset control by a central entity.

**Recommendation:** Maintain the revoked status of both mint and freeze authorities to ensure the immutability of token supply and user asset control. This practice enhances trust and decentralization.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`f5tfzt...pump`](https://solscan.io/account/f5tfzttne4sysmhzt5krfpwvhmysfjzorjcuxkpbpump) |
| **Network** | Solana |
| **Price** | $0.0008594 |
| **24h Volume** | $648.2K |
| **Liquidity** | $158.6K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 2mo |
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

- [View on DexScreener](https://dexscreener.com/solana/7nvp4qykvmpeuhobyrzcn1tqiz7k8pmk5uxqeebrzyh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aliens-are-real-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-12*

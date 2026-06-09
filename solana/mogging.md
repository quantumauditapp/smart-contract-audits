---
token: mogging
ticker: MOGGING
network: solana
risk_score: 90
status: critical
date: 2026-06-06
---

# mogging (MOGGING) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mogging-sol)

---

## Audit Summary

The audit of the 'mogging' SPL Token Mint at `5oq4zketrkummrftkwh7r1q6hzjmstjgceu6isgypump` reveals a critical security flaw: the mint account is reported as `Initialized: False`. This fundamental misconfiguration renders the token non-functional, yet it paradoxically shows active liquidity and trading volume. This severe discrepancy poses an immediate and high risk of total loss of funds for users interacting with this token. Additionally, the specific Token Program governing the mint is unknown, further increasing uncertainty.

> **Final Recommendation:** Users are strongly advised to exercise extreme caution and immediately cease all interactions with the 'mogging' token. The critical finding of an `Initialized: False` mint account, despite active trading, indicates a severe and fundamental flaw that could lead to total loss of funds for liquidity providers and traders. It is imperative to verify the legitimacy and functional status of any token before engaging in transactions. For projects launching new tokens, a Premium Deploy option, involving a comprehensive pre-launch audit and verification of all associated accounts and programs, is highly recommended to prevent such critical misconfigurations and ensure a secure and functional deployment from the outset.

## Security Analysis

The audit of the 'mogging' SPL Token Mint at `5oq4zketrkummrftkwh7r1q6hzjmstjgceu6isgypump` reveals a critical security flaw: the mint account is reported as `Initialized: False`. This fundamental misconfiguration renders the token non-functional, yet it paradoxically shows active liquidity and trading volume. This severe discrepancy poses an immediate and high risk of total loss of funds for users interacting with this token. Additionally, the specific Token Program governing the mint is unknown, further increasing uncertainty.

Users are strongly advised to exercise extreme caution and immediately cease all interactions with the 'mogging' token. The critical finding of an `Initialized: False` mint account, despite active trading, indicates a severe and fundamental flaw that could lead to total loss of funds for liquidity providers and traders. It is imperative to verify the legitimacy and functional status of any token before engaging in transactions. For projects launching new tokens, a Premium Deploy option, involving a comprehensive pre-launch audit and verification of all associated accounts and programs, is highly recommended to prevent such critical misconfigurations and ensure a secure and functional deployment from the outset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | 7.1 Architecture, 7.2 Code Security, 7.3 Access Control: The SPL Token Mint exhibits a critical architectural flaw as it is reported as `Initialized: False`, preventing any token operations. This fund |
| **Governance / Economics** | 6/10 | High | 7.4 Economic, 7.5 Governance: The economic risk is critically high due to the `Initialized: False` state of the token mint, which fundamentally undermines its functionality. Despite this, the token sh |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: SPL Token Mints are data accounts managed by the immutable SPL Token Program. As such, the mint account itself does not have an upgrade mechanism, eliminating upgrade-related risks. The  |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Uninitialized Mint Account with Active Liquidity  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account at `5oq4zketrkummrftkwh7r1q6hzjmstjgceu6isgypump` is reported as `Initialized: False`. Despite this critical state, the token has significant reported liquidity ($51,087 USD) and trading volume ($34,479 USD) over 89 days. An uninitialized mint account cannot function as a token, meaning no tokens can be minted, transferred, or held. This creates a severe discrepancy where users are trading a non-functional asset, posing an immediate risk of total loss of funds.

**Recommendation:** Users should immediately cease all interactions with this token and withdraw any provided liquidity. The program owner (if any) should investigate why an uninitialized mint account has active trading and address the underlying issue, or explicitly warn users. This state strongly suggests a misconfiguration or a potential scam.


### `H-01` — Unknown Token Program  *(Severity: High · Status: Unresolved)*

The 'Token Program' associated with this mint is reported as 'unknown'. For a standard SPL Token, this should be the well-known SPL Token Program ID (`TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA`). An unknown or non-standard token program introduces uncertainty regarding the token's behavior, security, and adherence to SPL standards. This issue is compounded by the `Initialized: False` state, making it unclear which program, if any, is intended to govern this mint.

**Recommendation:** The specific program ID governing this mint should be identified and verified against known, audited SPL Token Program versions. If it's a custom program, its source code would require a full audit. Given the `Initialized: False` state, this mint should not be trusted.


### `L-01` — Lack of External Security Signals  *(Severity: Low · Status: Unresolved)*

External security signals from GoPlus Solana and RugCheck are unavailable. While not a direct vulnerability, the absence of these independent assessments means there is less third-party verification of the token's safety and legitimacy, increasing reliance on manual due diligence.

**Recommendation:** Users should exercise increased caution due to the lack of independent security assessments. The project team should aim to integrate with and obtain ratings from reputable security analysis platforms to enhance transparency and trust.


### `I-01` — Revoked Authorities (Positive Security Feature)  *(Severity: Informational · Status: Unresolved)*

Both the Mint Authority and Freeze Authority for this SPL Token Mint are reported as 'revoked (None)'. This means no entity can mint new tokens or freeze existing token accounts, preventing inflationary attacks and censorship of user funds.

**Recommendation:** This configuration is generally considered a positive security feature for fixed-supply, permissionless tokens. However, this positive aspect is severely overshadowed by the critical `Initialized: False` state of the mint, which renders the token non-functional.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5oq4zk...pump`](https://solscan.io/account/5oq4zketrkummrftkwh7r1q6hzjmstjgceu6isgypump) |
| **Network** | Solana |
| **Price** | $0.0003518 |
| **24h Volume** | $165.5K |
| **Liquidity** | $57.3K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 2mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 860 buys / 750 sells |

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

## Frequently Asked Questions

### Is mogging a scam?

Based on the available data, mogging exhibits several high-risk characteristics. The unverified contract, unrenounced ownership, and unlocked liquidity are significant red flags. While the data doesn't definitively label it a scam, these elements create a high potential for developer-induced issues or asset withdrawal, warranting extreme caution. Investors should be aware of these fundamental security gaps.

### Is mogging safe to buy?

Mogging is currently classified as 'High Risk' with a score of 61/100, indicating it is not safe for most investors. Key risks include the contract not being verified, unrenounced ownership allowing potential developer manipulation, and unlocked liquidity exposing funds to potential rug pulls. These factors collectively highlight significant vulnerabilities, suggesting investors face substantial security risks when considering this token.

### Has mogging been audited?

The mogging contract is reported as 'not verified.' This means its code has not been published and confirmed on the blockchain. Without verification, assessing its functionality or security through an audit is severely hampered. Investors cannot independently inspect the contract, posing a significant transparency and trust risk.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5gjuboxlt8te68gvoaxttsx6pwfw1uzlsvhcp35esyxz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mogging-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-06*

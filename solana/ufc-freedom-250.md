---
token: UFC Freedom 250
ticker: UFC250
network: solana
risk_score: 90
status: critical
date: 2026-06-09
---

# UFC Freedom 250 (UFC250) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ufc-freedom-250-sol)

---

## Audit Summary

This audit reviews the on-chain state of the UFC Freedom 250 (UFC250) SPL Token Mint. A critical inconsistency was identified: the mint account is reported as 'Uninitialized' while simultaneously showing active trading volume and liquidity on decentralized exchanges. This fundamental discrepancy raises significant concerns about the token's legitimacy and potential for user loss. Additionally, the token is very new, exhibits a high volume-to-liquidity ratio, and lacks external security assessments, indicating elevated market and operational risks.

> **Final Recommendation:** Users are strongly advised to exercise extreme caution when interacting with the UFC Freedom 250 (UFC250) token. The critical finding regarding the 'Uninitialized' state of the mint account, despite reported trading activity, presents a fundamental and unresolved risk that could lead to complete loss of funds. The token's nascent age, high trading volatility, and lack of external security validation further amplify these risks. It is recommended to avoid engagement until the 'Uninitialized' status is definitively clarified and resolved.

For projects seeking to launch new SPL tokens, a Premium Deploy option is available. This service includes a comprehensive pre-launch audit of the token mint configuration, ensuring all parameters are correctly set, authorities are managed securely, and the token is properly initialized before public release, mitigating critical setup errors and enhanci…

## Security Analysis

This audit reviews the on-chain state of the UFC Freedom 250 (UFC250) SPL Token Mint. A critical inconsistency was identified: the mint account is reported as 'Uninitialized' while simultaneously showing active trading volume and liquidity on decentralized exchanges. This fundamental discrepancy raises significant concerns about the token's legitimacy and potential for user loss. Additionally, the token is very new, exhibits a high volume-to-liquidity ratio, and lacks external security assessments, indicating elevated market and operational risks.

Users are strongly advised to exercise extreme caution when interacting with the UFC Freedom 250 (UFC250) token. The critical finding regarding the 'Uninitialized' state of the mint account, despite reported trading activity, presents a fundamental and unresolved risk that could lead to complete loss of funds. The token's nascent age, high trading volatility, and lack of external security validation further amplify these risks. It is recommended to avoid engagement until the 'Uninitialized' status is definitively clarified and resolved.

For projects seeking to launch new SPL tokens, a Premium Deploy option is available. This service includes a comprehensive pre-launch audit of the token mint configuration, ensuring all parameters are correctly set, authorities are managed securely, and the token is properly initialized before public release, mitigating critical setup errors and enhanci…

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | (7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.8 Operations) The SPL Token Mint exhibits a critical technical flaw: it is reported as 'Uninitialized' (`Initialized: False`), which fundame |
| **Governance / Economics** | 6/10 | High | (7.4 Economic, 7.5 Governance, 7.6 External) The token is extremely new, with a pair age of only 1 day, contributing to high market volatility and uncertainty. A high Volume/Liquidity Ratio of 5.27 su |
| **Upgrades** | 6/10 | Low | (7.7 Upgrades) As an SPL Token Mint account, there is no custom program logic to upgrade. The underlying SPL Token Program is managed by Solana Labs and is not subject to project-specific upgrade risk |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — SPL Token Mint Reported as Uninitialized Despite Trading Activity  *(Severity: Critical · Status: Unresolved)*

The on-chain data for the SPL Token Mint `cwbirhpu2jqyjybidtb7fncfr9xwmmpxzgspirc3pump` indicates that its `Initialized` status is `False`. According to the SPL Token Program specification, an uninitialized mint account cannot have a supply, decimals, or participate in token transfers or trading. However, the provided data from dexscreener shows active liquidity ($17,355 USD) and significant 24-hour trading volume ($91,493 USD) for this token. This represents a critical inconsistency, as a truly uninitialized mint should not be tradable. This discrepancy suggests either a fundamental data retrieval error, a non-standard token implementation (not SPL), or a potential exploit where an invalid…

**Recommendation:** Investigate the root cause of the 'Uninitialized' status. If the mint is indeed uninitialized, all reported trading activity is illegitimate, and users should be immediately warned. If the data source for 'Initialized: False' is incorrect, verify the actual state of the mint account and update the information. Users should refrain from interacting with this token until this critical inconsistency is resolved and verified.


### `H-01` — Elevated Volume-to-Liquidity Ratio for a Newly Launched Token  *(Severity: High · Status: Unresolved)*

The token has a high Volume/Liquidity Ratio of 5.27, which is particularly concerning given its extremely short pair age of only 1 day. For new tokens, a high ratio can indicate wash trading, artificial volume generation, or a pump-and-dump scheme designed to attract unsuspecting investors. This pattern suggests potential market manipulation and high volatility, posing a significant risk to liquidity providers and traders.

**Recommendation:** Investors should exercise extreme caution and conduct thorough due diligence before engaging with tokens exhibiting such high Volume/Liquidity ratios, especially when they are newly launched. Monitor trading patterns closely for signs of manipulation.


### `M-01` — Absence of External Security Audit and Trust Signals  *(Severity: Medium · Status: Unresolved)*

No data from reputable external security analysis platforms such as GoPlus Solana or RugCheck is available for the UFC Freedom 250 token. The absence of these independent security signals makes it difficult to assess the token's legitimacy, potential for rug pulls, or other common scam indicators. This lack of external validation increases the inherent risk for users.

**Recommendation:** Projects should strive to obtain and display security audit results and integrate with reputable security analysis platforms to build trust and transparency within the community. Users should be wary of tokens lacking such external validation.


### `L-01` — Token is Extremely New  *(Severity: Low · Status: Unresolved)*

The token pair has only been active for 1 day. Newly launched tokens inherently carry higher risks due to unproven market stability, potential for early price volatility, and the lack of a track record for the project team. This short operational history provides limited data for assessing long-term viability or community support.

**Recommendation:** Investors should approach very new tokens with increased skepticism and allocate only risk-tolerant capital. It is advisable to observe the token's performance and project development over a longer period before making significant investments.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Resolved)*

The Mint Authority and Freeze Authority for the UFC Freedom 250 token have both been revoked (set to `None`). This is a positive security measure. Revoking the Mint Authority prevents the creation of new tokens, ensuring a fixed supply and protecting against inflationary attacks. Revoking the Freeze Authority prevents any entity from freezing token balances in user accounts, enhancing decentralization and user control over their assets.

**Recommendation:** This configuration is generally recommended for established, decentralized tokens to enhance trust and reduce central points of control.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`cwbirh...pump`](https://solscan.io/account/cwbirhpu2jqyjybidtb7fncfr9xwmmpxzgspirc3pump) |
| **Network** | Solana |
| **Price** | $0.00009756 |
| **24h Volume** | $92.8K |
| **Liquidity** | $21.7K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3180 buys / 1696 sells |

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

### Is UFC Freedom 250 a scam?

The data indicates UFC Freedom 250 exhibits several characteristics commonly associated with high-risk or potentially fraudulent projects. Its Critical Risk score of 75/100, unverified contract, unrenounced ownership, and unlocked liquidity are significant red flags. While we cannot definitively label it a 'scam' without intent, these technical findings strongly suggest extreme caution is warranted due to the inherent vulnerabilities and potential for malicious actions.

### Is UFC Freedom 250 safe to buy?

UFC Freedom 250 presents substantial safety concerns for potential buyers. The lack of contract verification means its code cannot be publicly audited for vulnerabilities or malicious functions. Unrenounced ownership allows the deployer to retain control, potentially altering the contract or affecting holder funds. Most critically, unlocked liquidity enables the team to remove funds, risking a complete loss for investors. These factors contribute to its critical risk score.

### Has UFC Freedom 250 been audited?

No, UFC Freedom 250 has not been audited. Its contract remains unverified, meaning the deployed code has not been publicly matched with source code. This lack of transparency is a prerequisite for any credible security audit, which examines smart contract code for vulnerabilities and potential exploits. Without verification, an audit is not possible, leaving the contract's integrity unknown.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/56garmqsyeky6oynuygocuizvcvddqsibube1q7eylfh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ufc-freedom-250-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-09*

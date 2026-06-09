---
token: three.ws
ticker: THREE
network: solana
risk_score: 90
status: critical
date: 2026-06-08
---

# three.ws (THREE) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/threews-sol)

---

## Audit Summary

The audit of the `three.ws` SPL Token Mint account reveals critical functional and technical deficiencies. The mint account is reported as uninitialized, rendering it non-functional for token operations, and its associated token program is unknown. While mint and freeze authorities are appropriately revoked, these fundamental issues pose significant risks to the token's integrity and usability. The presence of reported liquidity for an uninitialized token suggests a critical data discrepancy or potential misrepresentation.

> **Final Recommendation:** The audit of the `three.ws` SPL Token Mint reveals critical functional and technical issues, primarily the uninitialized state of the mint account and the unknown associated token program. These factors severely impact the token's operational viability and security posture. While the revocation of mint and freeze authorities is a positive security measure, the fundamental issues require immediate attention.

We strongly recommend verifying and rectifying the initialization status and identifying the controlling program. For projects seeking to launch robust and secure tokens, a comprehensive audit including source code review of any custom token programs is essential. Consider a Premium Deploy option for future token launches, which includes pre-deployment security checks, real-time monitoring, and expert guidance to ensure all critical parameters are correctly configured and verified b…

## Security Analysis

The audit of the `three.ws` SPL Token Mint account reveals critical functional and technical deficiencies. The mint account is reported as uninitialized, rendering it non-functional for token operations, and its associated token program is unknown. While mint and freeze authorities are appropriately revoked, these fundamental issues pose significant risks to the token's integrity and usability. The presence of reported liquidity for an uninitialized token suggests a critical data discrepancy or potential misrepresentation.

The audit of the `three.ws` SPL Token Mint reveals critical functional and technical issues, primarily the uninitialized state of the mint account and the unknown associated token program. These factors severely impact the token's operational viability and security posture. While the revocation of mint and freeze authorities is a positive security measure, the fundamental issues require immediate attention.

We strongly recommend verifying and rectifying the initialization status and identifying the controlling program. For projects seeking to launch robust and secure tokens, a comprehensive audit including source code review of any custom token programs is essential. Consider a Premium Deploy option for future token launches, which includes pre-deployment security checks, real-time monitoring, and expert guidance to ensure all critical parameters are correctly configured and verified b…

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The technical review (7.1 Architecture, 7.2 Code Security, 7.3 Access Control) reveals critical functional issues. The SPL Token Mint account is reported as `Initialized: False`, rendering it non-func |
| **Governance / Economics** | 6/10 | Medium | From an economic and governance perspective (7.4 Economic, 7.5 Governance), the token exhibits a high Volume/Liquidity Ratio of 6.27, indicating potential for high price volatility and slippage (M-01) |
| **Upgrades** | 6/10 | Low | As an SPL Token Mint account, this is a data account managed by the SPL Token Program, not an upgradeable program itself. Therefore, direct upgradeability risks (7.7 Upgrades) are not applicable to th |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account at `fembdox7r1psc4gecvjdsbnbza3bfztcydcatjvjpump` is reported as `Initialized: False`. An uninitialized mint account cannot be used to mint new tokens, transfer existing tokens, or perform any standard token operations. This renders the token non-functional for its intended purpose. If liquidity is reported for this token, it suggests a discrepancy in data or a potential misrepresentation, as a non-functional token cannot genuinely participate in trading.

**Recommendation:** Verify the initialization status of the mint account. If the intention is for this token to be tradable, the mint account must be properly initialized. If this account is indeed uninitialized, any associated liquidity or trading activity is highly suspicious and warrants immediate investigation.


### `H-01` — Unknown Token Program Association  *(Severity: High · Status: Unresolved)*

The "Token Program" associated with the mint account is listed as `unknown`. For a standard SPL Token, this should typically be `TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA`. An unknown program could indicate a custom token implementation, which would require a full source code audit to assess its security, or it could signify an error in data retrieval. Without knowing the controlling program, the security and functionality of the token cannot be reliably assessed.

**Recommendation:** Identify the precise program controlling this mint account. If it is a custom program, its source code must be made available for a comprehensive security review. If it is intended to be a standard SPL token, ensure it is correctly associated with the official SPL Token Program.


### `M-01` — High Volume-to-Liquidity Ratio  *(Severity: Medium · Status: Unresolved)*

The token exhibits a high Volume/Liquidity Ratio of `6.27` (where >5 is considered high). This indicates that trading volume significantly exceeds the available liquidity. While not a direct security vulnerability, a high ratio can lead to increased price volatility, significant slippage for larger trades, and potential for market manipulation due to shallow liquidity.

**Recommendation:** Users should exercise caution when trading this token, especially with large orders, due to potential high slippage and price impact. Project teams should consider strategies to increase liquidity to stabilize market dynamics.


### `I-01` — Missing Basic Mint Information  *(Severity: Informational · Status: Unresolved)*

Key details such as `Supply (raw)` and `Decimals` are reported as `unknown`. While this is consistent with an uninitialized mint account (C-01), for a functional token, these are fundamental properties. Their absence further confirms the non-operational state of this specific mint account.

**Recommendation:** Ensure all fundamental token properties are correctly set and retrievable once the mint account is properly initialized and operational.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`fembdo...pump`](https://solscan.io/account/fembdox7r1psc4gecvjdsbnbza3bfztcydcatjvjpump) |
| **Network** | Solana |
| **Price** | $0.004757 |
| **24h Volume** | $1.46M |
| **Liquidity** | $266.3K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 1mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32461 buys / 17505 sells |

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

### Is three.ws a scam?

Based on automated analysis, three.ws scores 65/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is three.ws safe to buy?

Our scanner flagged a risk score of 65/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has three.ws been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5byl7mzolabynwmpzkpkjf4mgkz7febzranos19pre2z)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/threews-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-08*

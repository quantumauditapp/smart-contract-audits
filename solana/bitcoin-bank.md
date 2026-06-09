---
token: Bitcoin Bank
ticker: BTCBANK
network: solana
risk_score: 90
status: critical
date: 2026-06-07
---

# Bitcoin Bank (BTCBANK) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitcoin-bank-sol)

---

## Audit Summary

The Bitcoin Bank (BTCBANK) SPL Token Mint exhibits a critical vulnerability: it is currently uninitialized despite having active trading and liquidity. This state allows any malicious actor to initialize the mint, define its properties (decimals, supply, authorities), and potentially mint tokens to themselves, leading to a complete loss of value for current holders. While mint and freeze authorities are reported as revoked, this status is irrelevant for an uninitialized account. Immediate action is required to address this fundamental flaw.

> **Final Recommendation:** The Bitcoin Bank (BTCBANK) SPL Token Mint is in a critically vulnerable state due to being uninitialized while having active trading. This poses an immediate and severe risk to all holders and liquidity providers. It is imperative that the legitimate project team immediately initializes the mint with correct parameters and then revokes all authorities to prevent malicious exploitation. Failure to do so will result in a complete loss of value for token holders. For future token deployments, consider using a 'Premium Deploy' service to ensure all token accounts are correctly initialized and configured from inception, preventing such fundamental vulnerabilities.

## Security Analysis

The Bitcoin Bank (BTCBANK) SPL Token Mint exhibits a critical vulnerability: it is currently uninitialized despite having active trading and liquidity. This state allows any malicious actor to initialize the mint, define its properties (decimals, supply, authorities), and potentially mint tokens to themselves, leading to a complete loss of value for current holders. While mint and freeze authorities are reported as revoked, this status is irrelevant for an uninitialized account. Immediate action is required to address this fundamental flaw.

The Bitcoin Bank (BTCBANK) SPL Token Mint is in a critically vulnerable state due to being uninitialized while having active trading. This poses an immediate and severe risk to all holders and liquidity providers. It is imperative that the legitimate project team immediately initializes the mint with correct parameters and then revokes all authorities to prevent malicious exploitation. Failure to do so will result in a complete loss of value for token holders. For future token deployments, consider using a 'Premium Deploy' service to ensure all token accounts are correctly initialized and configured from inception, preventing such fundamental vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | 7.1 Architecture & 7.2 Code Security: The SPL Token Mint for Bitcoin Bank (BTCBANK) is in an uninitialized state, which is a critical architectural flaw. This means core properties like decimals and s |
| **Governance / Economics** | 6/10 | High | 7.4 Economic: The token exhibits active trading with $29,272 in liquidity and $72,557 in 24h volume over 17 days. However, the uninitialized state of the mint introduces extreme economic risk, as the  |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: SPL Token Mint accounts are data structures managed by the SPL Token Program and do not possess direct upgradeability. Changes to the token's fundamental properties (like decimals or sup |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Uninitialized SPL Token Mint with Active Trading  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account for Bitcoin Bank (BTCBANK) is currently uninitialized (`Initialized: False`) despite having active liquidity ($29,272) and trading volume ($72,557). An uninitialized mint account means its core properties, such as decimals, total supply, and mint/freeze authorities, have not been set. Any actor can send an `InitializeMint` instruction to this account, defining these critical parameters. This allows a malicious actor to initialize the mint with arbitrary decimals (e.g., 0 decimals to make all tokens indivisible), set a new mint authority to themselves, and then mint an unlimited supply of tokens, effectively draining liquidity pools and rendering existing tokens wo…

**Recommendation:** The legitimate project team must immediately initialize the SPL Token Mint with the intended decimals and supply. After initialization, it is strongly recommended to revoke both the mint and freeze authorities to prevent any further token issuance or freezing, ensuring a fixed supply and decentralized control.


### `H-01` — Undefined Token Properties (Supply and Decimals)  *(Severity: High · Status: Unresolved)*

Due to the uninitialized state of the SPL Token Mint, the token's total supply and decimal precision are currently undefined (`Supply (raw): unknown`, `Decimals: unknown`). This creates significant uncertainty and risk for token holders and liquidity providers, as the fundamental characteristics of the token can be arbitrarily set by the first entity to initialize the mint. This directly impacts the token's divisibility and potential for dilution.

**Recommendation:** As part of the mint initialization process, ensure that the token's decimals are set to an appropriate value (e.g., 6 or 9 for standard tokens) and that the initial supply is clearly defined and understood by the community. Transparency regarding these properties is crucial for investor confidence.


### `M-01` — Misleading Authority Revocation Status for Uninitialized Mint  *(Severity: Medium · Status: Unresolved)*

The audit reports indicate that both the Mint Authority and Freeze Authority are `revoked (None)`. While revocation is generally a positive security measure for established tokens, this status is misleading and provides a false sense of security for an uninitialized mint. Since the mint is uninitialized, these authorities have not yet been set, and therefore cannot be truly 'revoked.' Any actor initializing the mint can assign these authorities to an address of their choosing, negating the perceived security benefit.

**Recommendation:** Understand that authority revocation is only meaningful *after* a mint has been properly initialized and the authorities have been explicitly set and then revoked. Prioritize the immediate initialization of the mint. Once initialized, if a fixed supply and immutable state are desired, ensure authorities are explicitly set to `None` (revoked) as a separate step.


### `I-01` — Incomplete External Security Signal Data  *(Severity: Informational · Status: Unresolved)*

External security signals from GoPlus Solana data and RugCheck are unavailable. This limits the comprehensive assessment of the token's broader ecosystem risk, such as potential rug pull indicators or contract security scores provided by these third-party services.

**Recommendation:** While not a direct vulnerability of the token itself, it is recommended to monitor these external security platforms if data becomes available in the future. For projects, ensuring visibility and data availability on such platforms can enhance transparency and trust.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9s96g1...pump`](https://solscan.io/account/9s96g11xgshczudfjqkqzqxzvubqgjxsysj1wrgxpump) |
| **Network** | Solana |
| **Price** | $0.0004337 |
| **24h Volume** | $220.2K |
| **Liquidity** | $56.8K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 15d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2817 buys / 1914 sells |

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

### Is Bitcoin Bank a scam?

Based on the available data, Bitcoin Bank (BTCBANK) exhibits several high-risk characteristics commonly associated with potential scams. The contract is unverified, ownership is not renounced, and liquidity is unlocked. These elements allow developers complete control over the token's future, including the ability to remove liquidity and potentially render tokens worthless, making it highly susceptible to a "rug pull."

### Is Bitcoin Bank safe to buy?

Given its high-risk score of 70/100, Bitcoin Bank (BTCBANK) is not considered safe for investment. Key risk factors include an unverified contract, unrenounced ownership, and unlocked liquidity. These conditions expose investors to significant vulnerabilities such as potential contract manipulation, token supply inflation, and the complete withdrawal of liquidity, leading to substantial financial loss.

### Has Bitcoin Bank been audited?

There is no indication that Bitcoin Bank (BTCBANK) has undergone a formal security audit. Crucially, its contract remains unverified, meaning the underlying code is not publicly available for review by auditors or the community. Without contract verification, a comprehensive security audit is impossible, leaving potential vulnerabilities undetected and unaddressed.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4a2acvjbjysaueewedivqhcmnfty2ef49eayyxswdmt2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bitcoin-bank-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-07*

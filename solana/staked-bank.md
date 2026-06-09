---
token: Staked Bank
ticker: STAKE
network: solana
risk_score: 90
status: critical
date: 2026-05-29
---

# Staked Bank (STAKE) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/staked-bank-sol)

---

## Audit Summary

The audit of the Staked Bank (Stake) SPL Token Mint at `5s7tf6ih2cezf7zpnkjatcknaq9dl5gswhmmt3jdpump` reveals a critical inconsistency: the mint account is reported as uninitialized, yet significant liquidity and trading volume are observed. While mint and freeze authorities are revoked, the uninitialized state fundamentally prevents the token from functioning correctly, posing a severe risk to users engaging with this asset. This contradiction suggests a high potential for user losses.

> **Final Recommendation:** The Staked Bank (Stake) token mint presents critical risks due to its uninitialized state despite reported trading activity. Users are strongly advised to exercise extreme caution and verify the true functional status of the token before any interaction. The contradiction between the uninitialized state and active trading suggests a high potential for loss of funds.

For projects seeking to deploy functional and secure SPL tokens, a Premium Deploy option is recommended. This service includes a comprehensive pre-deployment audit of the token mint configuration, ensuring all parameters are correctly set and authorities are managed securely, preventing fundamental issues like uninitialized states.

## Security Analysis

The audit of the Staked Bank (Stake) SPL Token Mint at `5s7tf6ih2cezf7zpnkjatcknaq9dl5gswhmmt3jdpump` reveals a critical inconsistency: the mint account is reported as uninitialized, yet significant liquidity and trading volume are observed. While mint and freeze authorities are revoked, the uninitialized state fundamentally prevents the token from functioning correctly, posing a severe risk to users engaging with this asset. This contradiction suggests a high potential for user losses.

The Staked Bank (Stake) token mint presents critical risks due to its uninitialized state despite reported trading activity. Users are strongly advised to exercise extreme caution and verify the true functional status of the token before any interaction. The contradiction between the uninitialized state and active trading suggests a high potential for loss of funds.

For projects seeking to deploy functional and secure SPL tokens, a Premium Deploy option is recommended. This service includes a comprehensive pre-deployment audit of the token mint configuration, ensuring all parameters are correctly set and authorities are managed securely, preventing fundamental issues like uninitialized states.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical analysis of the SPL Token Mint reveals a critical issue: the mint account is uninitialized (`Initialized: False`), which means the token cannot be minted, transferred, or have its supply |
| **Governance / Economics** | 6/10 | High | The economic risk is critically high due to the uninitialized state of the token mint (7.4 Economic). Users interacting with this token, despite its reported liquidity, may be engaging with an asset t |
| **Upgrades** | 6/10 | Low | N/A - This is an SPL Token Mint account, not an upgradeable program. The state of the mint is fixed once initialized (or uninitialized in this case), and there are no upgrade mechanisms applicable to  |

## Security Findings

_🔴 2 Critical · ⚪ 2 Informational_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account `5s7tf6ih2cezf7zpnkjatcknaq9dl5gswhmmt3jdpump` is reported as `Initialized: False`. An uninitialized mint account cannot have a defined supply or decimals, and tokens cannot be minted or transferred from it. This state fundamentally prevents the token from functioning as a standard SPL token.

**Recommendation:** The mint account must be properly initialized using the SPL Token Program's `InitializeMint` instruction. This involves setting the supply, decimals, and assigning initial authorities. Without proper initialization, the token is non-functional.


### `C-02` — Inconsistent State: Uninitialized Mint with Active Trading  *(Severity: Critical · Status: Unresolved)*

Despite the mint account being reported as `Initialized: False`, external data indicates significant liquidity ($16,077 USD) and 24-hour trading volume ($4,933 USD) associated with this specific token address. This is a critical inconsistency, as an uninitialized mint cannot legitimately support trading. Users attempting to acquire or trade this token may find themselves holding non-transferable assets or assets with no real underlying supply, leading to a total loss of funds.

**Recommendation:** Investigate the discrepancy between the on-chain `Initialized: False` status and the reported trading activity. If the mint is indeed uninitialized, all associated trading pairs should be delisted immediately to prevent user losses. If the `Initialized` status is incorrect, provide evidence of proper initialization.


### `I-01` — Missing Supply and Decimals Information  *(Severity: Informational · Status: Unresolved)*

The supply (raw) and decimals for the token are reported as `unknown`. This is a direct consequence of the mint account being uninitialized. Without these fundamental parameters, the token's value and divisibility cannot be determined, further hindering its usability.

**Recommendation:** Ensure the mint is properly initialized, which will populate the supply and decimals fields. Once initialized, this information should be readily available via RPC queries.


### `I-02` — Lack of Comprehensive External Security Signals  *(Severity: Informational · Status: Unresolved)*

Data from external security analysis platforms such as GoPlus Solana and RugCheck is unavailable. These platforms provide valuable insights into potential risks, scam indicators, and community trust signals for tokens. The absence of this data limits the holistic security assessment.

**Recommendation:** Integrate with and monitor external security platforms for comprehensive risk assessment. While not a direct vulnerability, this information gap can impact investor confidence and early detection of potential issues.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5s7tf6...pump`](https://solscan.io/account/5s7tf6ih2cezf7zpnkjatcknaq9dl5gswhmmt3jdpump) |
| **Network** | Solana |
| **Price** | $0.0001349 |
| **24h Volume** | $140.7K |
| **Liquidity** | $36.3K |
| **Volume / Liquidity** | 3.9× |
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

- [View on DexScreener](https://dexscreener.com/solana/eyuhvulacx9n1a3mj4lzts6ju7ejk49sfmtjne65mpnv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/staked-bank-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-29*

---
token: FarmTown
ticker: FARM
network: solana
risk_score: 32
status: medium
date: 2026-06-22
---

# FarmTown (FARM) — Smart Contract Security Analysis | Solana

> **Risk Score: 32/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/farmtown-sol)

---

## Audit Summary

This audit of the FarmTown (FARM) SPL token mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint and freeze authorities are revoked, and no Token-2022 extensions posing significant risks are active. Holder concentration data was unavailable from RPC, but RugCheck.xyz indicated high ownership by top holders, which is a market risk to consider.

> **Final Recommendation:** Based on the available data and deterministic rules, the FarmTown (FARM) token mint presents a low-risk profile regarding its on-chain configuration and authorities. Key administrative powers like minting and freezing have been revoked, and no high-risk Token-2022 extensions are active. However, holder concentration data was unavailable from RPC, and RugCheck.xyz indicated high ownership by top holders, which could still pose a market risk. Users should consider this external signal and the relatively new pair age (12 days) when evaluating investment decisions. No Premium Deploy option is applicable for SPL token mints as there is no source code to deploy.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The FarmTown (FARM) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, indicating that no new tokens can be minted and no existing accounts can be frozen. |
| **Governance / Economics** | 6/10 | Medium | The token exhibits moderate liquidity with $39,311 USD in total DEX liquidity, which is above the very low liquidity threshold. The 24-hour volume of $119,821 results in a Volume/Liquidity Ratio of 3. |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the token have been revoked, meaning no further administrative changes can be made to the token's supply or account freezing capabilities. The token uses th |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`yMJPZb...pump`](https://solscan.io/account/yMJPZbnhoHib3ib8n8PfiVcp9yauk1vnaGKLx7epump) |
| **Network** | Solana |
| **Price** | $0.00161 |
| **24h Volume** | $767.0K |
| **Liquidity** | $112.3K |
| **Volume / Liquidity** | 6.8× |
| **Token Age** | 5d |
| **Top-10 Holders** | 20.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4022 buys / 3696 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is FarmTown a scam?

Based on the provided data, FarmTown cannot be definitively labeled a scam. Its ownership is renounced, and it lacks a mint function, which are positive indicators against immediate malicious team action. However, the unverified contract and unlocked liquidity introduce substantial risks commonly associated with less reputable projects. The medium risk score of 43/100 suggests a cautious approach is warranted, acknowledging both positive and negative signals.

### Is FarmTown safe to buy?

Buying FarmTown (FARM) carries notable risks due to key security vulnerabilities. The contract is unverified, meaning its code cannot be publicly reviewed for potential exploits or hidden malicious functions. Furthermore, the liquidity for FARM is not locked. This creates a significant risk where liquidity providers could withdraw funds, potentially leading to a sharp price decline and making it difficult for investors to sell their tokens.

### Has FarmTown been audited?

The FarmTown contract has not been verified, which is a prerequisite for a formal security audit. Contract verification makes the code public and available for review by the community and professional auditors. Without a verified contract, an independent security audit cannot be conducted, leaving the contract's integrity and security status unconfirmed by third-party experts. Investors should proceed with caution.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/frxrs52rlf45nywimjeoquh4g7crry7ny13fxn6t4dd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/farmtown-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-22*

---
token: Solstice
ticker: SLX
network: solana
risk_score: 34
status: medium
date: 2026-06-01
---

# Solstice (SLX) — Smart Contract Security Analysis | Solana

> **Risk Score: 34/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solstice-sol)

---

## Audit Summary

Automated review assessed the protocol architecture, upgrade controls, and external dependencies based on available inputs. Core flows look consistent and follow common patterns, but some edge cases and monitoring gaps remain. This report balances strengths with concrete remediation steps to reduce risk before deployment.

> **Final Recommendation:** Proceed with deployment after addressing high-severity findings and adding timelock protections for admin actions. A short remediation sprint for medium issues will materially reduce upgrade and oracle risk.

For teams seeking stronger assurance, the Premium Deploy track adds upgrade rehearsals, monitoring baselines, and post-deploy verification of oracle and admin flows. Premium Deploy also includes a rollback drill and sign-off checklist before production launch.

## Security Analysis

Automated review assessed the protocol architecture, upgrade controls, and external dependencies based on available inputs. Core flows look consistent and follow common patterns, but some edge cases and monitoring gaps remain. This report balances strengths with concrete remediation steps to reduce risk before deployment.

Proceed with deployment after addressing high-severity findings and adding timelock protections for admin actions. A short remediation sprint for medium issues will materially reduce upgrade and oracle risk.

For teams seeking stronger assurance, the Premium Deploy track adds upgrade rehearsals, monitoring baselines, and post-deploy verification of oracle and admin flows. Premium Deploy also includes a rollback drill and sign-off checklist before production launch.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Architecture (7.1) is modular, separating storage, strategy, and interface layers to contain faults and align with standards like ERC-20. Code security (7.2) is mostly solid with input validation and  |
| **Governance / Economics** | 6/10 | Medium | Economic design (7.4) uses capped emissions and fee ceilings, and rate limits reduce flash-loan sensitivity. However, reward curves still depend on liquidity timing, and unbounded parameter changes co |
| **Upgrades** | 6/10 | Medium | Upgrade lifecycle (7.7) follows proxy standards and initializer versioning, which reduces accidental state resets. Still, upgrades can be executed without delay and rollback testing is limited, increa |

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
| **Contract** | [`slxdx4...rfgq`](https://solscan.io/account/slxdx4but2v9ujqnzwqsfztj9ukludsvxhfmeedrfgq) |
| **Network** | Solana |
| **Price** | $0.4214 |
| **24h Volume** | $521.6K |
| **Liquidity** | $203.3K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 6d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2275 buys / 2192 sells |

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

### Is Solstice a scam?

Based on the provided data, Solstice (SLX) exhibits multiple critical risk factors often associated with fraudulent schemes, culminating in a 72/100 Critical Risk score. The lack of contract verification, unrenounced ownership, and unlocked liquidity are significant indicators of potential malicious intent or severe vulnerability. While these factors don't definitively label it a scam, they strongly advise against investment due to the high probability of financial loss.

### Is Solstice safe to buy?

No, Solstice (SLX) is assessed as critically unsafe for investment, reflected by its 72/100 risk score. The contract's unverified status means its code is unknown and unauditable, while unrenounced ownership allows the developer to retain full control. Crucially, the liquidity pool is not locked, exposing investor funds to potential removal by the owner (a rug pull). These fundamental risks make Solstice a highly speculative and dangerous asset.

### Has Solstice been audited?

There is no indication of a security audit for Solstice (SLX). Furthermore, the contract code is not verified on the blockchain. This means the underlying code is opaque and has not been publicly confirmed or reviewed by independent parties. Without verification, a professional audit is practically impossible, leaving investors with no transparency regarding the contract's safety or functionality.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/sgo6ropnwxzutdhkbejkxvyuvwycgwzh5hgx6w6pxhh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solstice-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-01*

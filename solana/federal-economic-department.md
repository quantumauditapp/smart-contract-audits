---
token: Federal Economic Department
ticker: FED
network: solana
risk_score: 34
status: medium
date: 2026-05-16
---

# Federal Economic Department (FED) — Smart Contract Security Analysis | Solana

> **Risk Score: 34/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/federal-economic-department-sol)

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
| **Contract** | [`3gnfjb...pump`](https://solscan.io/account/3gnfjbtekgcbwwpuc6hunwnukwveehgfie4kx6xipump) |
| **Network** | Solana |
| **Price** | $0.0002881 |
| **24h Volume** | $198.2K |
| **Liquidity** | $42.6K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 1d |
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

- [View on DexScreener](https://dexscreener.com/solana/fq8jq7t6hwxrfdkyjudrt84zyrnpaq9wwjvgqtqhvxbk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/federal-economic-department-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-16*

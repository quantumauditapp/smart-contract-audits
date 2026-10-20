---
token: NeoSoul
ticker: NEOS
network: arbitrum
risk_score: 73
status: high
date: 2026-10-10
---

# NeoSoul (NEOS) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/neosoul-arb)

---

## Audit Summary

This report is generated for the contract at 0xa201eff84651d8b3e57587223ba5ce06035a7284 on Arbitrum. No contract source code was provided for analysis, therefore a comprehensive security audit could not be performed. The findings below reflect the lack of available information rather than specific code vulnerabilities.

> **Final Recommendation:** For any future security assessments, it is crucial to provide the complete and verified source code for the contract. This enables a thorough analysis of technical vulnerabilities, economic risks, governance structures, and upgrade mechanisms. Without source code, no meaningful security guarantees can be provided, and users should exercise extreme caution when interacting with such contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Without access to the contract's source code, a technical security assessment (7.1 Architecture, 7.2 Code Security, 7.3 Access Control) cannot be performed. Key areas like reentrancy, integer… |
| **Governance / Economics** | 1/10 | High | An economic and governance risk assessment (7.4 Economic, 7.5 Governance) requires understanding the contract's logic, tokenomics, and administrative controls. Without the source code, it is… |
| **Upgrades** | 6/10 | Medium | The upgradeability status (7.7 Upgrades) of the contract cannot be determined without its source code. It is unknown if the contract utilizes a proxy pattern (e.g., UUPS, Transparent) or is… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 10 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x738f…04b0 — holds 99.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No Contract Source Code Provided  *(Severity: Informational · Status: Unresolved)*

The audit request did not include the source code for the contract at 0xa201eff84651d8b3e57587223ba5ce06035a7284. This prevents any form of static analysis, dynamic testing, or manual review of the contract's logic and security posture. All aspects of the audit, including technical, economic, governance, and upgradeability, are unassessable.

**Recommendation:** Always provide the full, verified source code for all contracts intended for audit. Ensure the code is publicly verifiable on block explorers like Arbiscan to enhance transparency and trust.


### `I-02` — Verification Status Unknown  *(Severity: Informational · Status: Unresolved)*

The contract at 0xa201eff84651d8b3e57587223ba5ce06035a7284 is not indicated as verified on the block explorer (is_verified: false). Unverified contracts pose a significant risk as their deployed bytecode cannot be easily matched against human-readable source code, making it difficult for users and auditors to understand their functionality and ensure safety.

**Recommendation:** Verify the contract's source code on the respective block explorer (e.g., Arbiscan) to provide transparency and allow for public scrutiny. This is a fundamental step for user trust and security.


### `I-03` — Compiler Version Undetermined  *(Severity: Informational · Status: Unresolved)*

Without the contract's source code, the Solidity compiler version used for deployment cannot be determined. Knowing the compiler version is crucial for identifying potential vulnerabilities specific to certain compiler versions (e.g., optimizer bugs, known issues in older versions).

**Recommendation:** When providing source code, ensure the `pragma solidity` directive is correctly specified. Ideally, use a recent, stable, and well-audited compiler version, and avoid using `^` in pragma statements for production deployments.


### `I-04` — Proxy Implementation Status Unknown  *(Severity: Informational · Status: Unresolved)*

The provided information indicates `is_proxy: false` and `implementation: null`, but without source code, it's impossible to confirm if this contract is part of a proxy pattern or an immutable contract. If it were a proxy, the security of the implementation contract would be paramount, and upgradeability considerations would apply.

**Recommendation:** If the contract is intended to be part of a proxy system, provide the source code for both the proxy and its implementation(s). Clearly document the proxy pattern used (e.g., UUPS, Transparent) and the upgrade mechanism.


### `I-05` — Lack of Operational Context and Documentation  *(Severity: Informational · Status: Unresolved)*

Without contract source code or accompanying documentation, the intended purpose, operational procedures (7.8 Operations), and external dependencies (7.6 External) of the contract are entirely unknown. This lack of context hinders any assessment of its overall security and integration risks.

**Recommendation:** Provide comprehensive documentation outlining the contract's architecture, intended functionality, external interactions (e.g., oracles, other protocols), administrative roles, and operational procedures. This is vital for a complete security review.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.7% of supply. What remains: 91.2% in wallets, 2.4% in other contracts. The deployer/owner wallet itself holds 2.4%. 417 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

417 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $85K (DexScreener, all pools). 24h trading volume $140K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $85K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa201...7284`](https://arbiscan.io/address/0xa201eff84651d8b3e57587223ba5ce06035a7284) |
| **Network** | Arbitrum |
| **Price** | $0.1231 |
| **24h Volume** | $139.9K |
| **Liquidity** | $85.0K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 23h |
| **Top-10 Holders** | 93.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 871 buys / 314 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xc8d293ce6bd48903ae90aa87659de3d34303b0e3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/neosoul-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*

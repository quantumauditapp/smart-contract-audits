---
token: Emmie
ticker: EMMIE
network: base
risk_score: 63
status: medium
date: 2026-11-03
---

# Emmie (EMMIE) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/emmie-base)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, it is impossible to distinguish between a legitimate project and a malicious honeypot or rug-pull. Users should only engage with contracts that have verified source code on the block explorer and have undergone professional security audits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified due to lack of source code. 7.3 Access Control: Cannot be verified. 7.6 External: Unknown interactions with liquidity pools. |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: Potential for hidden minting or transfer taxes exists. 7.5 Governance: Cannot determine if ownership is renounced or if admin functions exist. 7.8 Operations: High risk of rug-pull or… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Cannot verify if the contract is immutable or utilizes a proxy pattern. Without source code, any upgradeability features remain hidden from the user. |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 4 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any technical security assessment.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security review.


### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 28.9% of supply. What remains: 28.9% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 23.1%. A holder that also controls the contract can sell into its own liquidity. 460 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

460 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $86K (DexScreener, all pools). 24h trading volume $515K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $86K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xef02...b6cb`](https://basescan.org/address/0xef022eb9f5a3c6fabee44c116a38d5efa419b6cb) |
| **Network** | Base |
| **Price** | $0.0002103 |
| **24h Volume** | $514.9K |
| **Liquidity** | $86.0K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 16h |
| **Top-10 Holders** | 28.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 688 buys / 540 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xd0f732d66f37cdf1987e140cab0b026da560926870ca11cfcb8eaa3e56fea52e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/emmie-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

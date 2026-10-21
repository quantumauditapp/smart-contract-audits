---
token: GEN
ticker: GEN
network: bsc
risk_score: 66
status: high
date: 2026-10-21
---

# GEN (GEN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gen-bsc)

---

## Audit Summary

The contract at the provided address is not verified on the BSC block explorer. Consequently, the source code is inaccessible for security analysis. The contract is controlled by an EOA (Externally Owned Account), and ownership has not been renounced, presenting a significant centralization risk.

> **Final Recommendation:** Do not interact with this contract. The absence of verified source code makes it impossible to distinguish between a legitimate project and a malicious honeypot or rug-pull mechanism. Investors should prioritize projects with fully verified, audited, and transparent codebases.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security cannot be assessed due to lack of source code. 7.3 Access Control is opaque, as the contract logic is hidden from public view. 7.6 External interactions remain… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance parameters are entirely controlled by an EOA. Without verified code, there is no transparency regarding tax mechanisms, minting capabilities, or liquidity lock status.… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades and 7.8 Operations are unverifiable. While the contract is not identified as a standard proxy, the lack of source code prevents confirmation of immutability. Users should assume the… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security assessment of the logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security review.


### `H-02` — Centralized Ownership  *(Severity: High · Status: Unresolved)*

The contract is controlled by an EOA and ownership has not been renounced, allowing the owner to potentially execute arbitrary administrative functions.

**Recommendation:** Renounce ownership or transfer control to a multi-signature wallet or a time-locked governance contract.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 0.1% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 99.8% in other contracts. 8 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

8 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $361K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdfb2...d6bb`](https://bscscan.com/address/0xdfb29e72835f5382301f4f7ed7eac6c13c49d6bb) |
| **Network** | BNB Chain |
| **Price** | $0.1605 |
| **24h Volume** | $360.9K |
| **Liquidity** | $1.56M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7713 buys / 33 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xce091a55e98186b69a802da5c83c42fed9734c01)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gen-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

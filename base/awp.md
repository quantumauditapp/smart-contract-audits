---
token: AWP
ticker: AWP
network: base
risk_score: 79
status: high
date: 2026-11-03
---

# AWP (AWP) — Smart Contract Security Analysis | Base

> **Risk Score: 79/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/awp-base)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for security review. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or liquidity lock status.

> **Final Recommendation:** Do not interact with this contract. The inability to verify the source code makes it impossible to distinguish between a legitimate project and a malicious one. Prioritize assets with verified, audited, and transparent source code to ensure the safety of your funds.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security cannot be assessed due to the absence of source code. 7.3 Access Control mechanisms are opaque, meaning potential backdoors or minting functions remain hidden.… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance parameters are entirely opaque. Without source code, it is impossible to determine if there are hidden transfer taxes, blacklists, or centralized control over… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades status is unknown. If the contract is a proxy, it could be upgraded to malicious logic at any time. Without verification, there is no way to confirm if the contract is immutable or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security analysis or verification of logic.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `H-01` — Opaque Governance and Access Control  *(Severity: High · Status: Unresolved)*

Without source code, it is impossible to identify administrative privileges, minting capabilities, or potential backdoors.

**Recommendation:** Ensure all administrative functions are documented and subject to timelocks or multi-signature requirements.


### `M-01` — Potential for Malicious Logic  *(Severity: Medium · Status: Unresolved)*

Unverified contracts frequently contain hidden mechanisms such as honeypot logic, transfer taxes, or liquidity withdrawal functions.

**Recommendation:** Avoid interacting with unverified contracts to prevent loss of funds due to hidden malicious logic.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x6183…c593 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.5% of supply. Of that, 8.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 68.4% in wallets, 14.9% in other contracts. 1,739 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,739 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $223K (DexScreener, all pools). 24h trading volume $93K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $223K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc9af...c540`](https://basescan.org/address/0xc9af3d36f0278c19b1cae50d67d263950e1fc540) |
| **Network** | Base |
| **Price** | $0.00688 |
| **24h Volume** | $92.8K |
| **Liquidity** | $223.0K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 5h |
| **Top-10 Holders** | 91.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1240 buys / 371 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x5e5b8828bf4248858d1bccd7a3776f0e3306cd20)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/awp-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

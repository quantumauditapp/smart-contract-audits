---
token: Meanwhile
ticker: MENWH
network: arbitrum
risk_score: 75
status: high
date: 2026-10-20
---

# Meanwhile (MENWH) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meanwhile-arb)

---

## Audit Summary

The contract at the provided address is not verified on the Arbitrum block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with or provide liquidity to this contract until the source code is verified on the block explorer. Without verified code, there is no way to ensure the contract does not contain malicious functions such as honeypot mechanisms, unauthorized minting, or permanent fund locking.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Unverifiable due to lack of source code. 7.3 Access Control: Cannot be audited. 7.6 External: Interactions with external protocols cannot be assessed. |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Tokenomics and tax structures are hidden. 7.5 Governance: Potential centralized control mechanisms cannot be identified. The lack of transparency poses a significant risk to capital… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: It is impossible to determine if the contract is upgradeable or contains proxy patterns. 7.8 Operations: Operational security is compromised by the inability to verify contract logic. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for security vulnerabilities or malicious logic.

**Recommendation:** Publish the source code on the block explorer and undergo a professional security audit.


### `H-01` — Lack of Transparency  *(Severity: High · Status: Unresolved)*

Investors cannot verify the existence of ownership controls, tax logic, or liquidity lock mechanisms, leading to high information asymmetry.

**Recommendation:** Provide full documentation and verified source code to allow for community due diligence.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x1660…e780 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.5% of supply. Of that, 14.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 70.2% in wallets, 1.5% in other contracts. The deployer/owner wallet itself holds 7.5%. 1,880 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,880 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $276K (DexScreener, all pools). 24h trading volume $112K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $276K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0da6...5bd4`](https://arbiscan.io/address/0x0da6767c1a70359085c45f367d6bcd32110a5bd4) |
| **Network** | Arbitrum |
| **Price** | $0.01056 |
| **24h Volume** | $112.2K |
| **Liquidity** | $276.4K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 6h |
| **Top-10 Holders** | 86.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 460 buys / 39 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x0e60cc17b4e995e19307925e7d725f1939494dc3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meanwhile-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

---
token: bibi.ai
ticker: BIBI
network: bsc
risk_score: 71
status: high
date: 2026-10-23
---

# bibi.ai (BIBI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bibiai-bsc-38f5)

---

## Audit Summary

The contract at 0x679f0211668363cdcea269f9e0375dd0e7f97777 is not verified on the BSC block explorer. Consequently, the source code is unavailable for security analysis. The contract ownership is held by an EOA (0x34f0...), which presents significant centralization risks as the owner may have the ability to modify token parameters, pause trading, or blacklist addresses.

> **Final Recommendation:** Investors should exercise extreme caution as the contract is unverified. Do not interact with or provide liquidity to this contract until the source code is published and audited by a reputable third party. The centralization of control via an EOA is a major red flag for potential rug-pull scenarios.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security cannot be assessed due to lack of source code. 7.3 Access Control is likely centralized given the EOA ownership. 7.6 External dependencies and 7.8 Operations… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance parameters are hidden from public view. The EOA owner possesses unilateral control over the contract, which is a high-risk configuration for token holders. There is no… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. However, the lack of code visibility prevents confirmation of immutability. The contract remains a 'black box' to the community. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not verified on the block explorer, making it impossible to audit for malicious logic, backdoors, or vulnerabilities.

**Recommendation:** Verify the contract source code on the block explorer immediately to provide transparency to users.


### `H-02` — Centralized Ownership (EOA)  *(Severity: High · Status: Unresolved)*

The contract is owned by an EOA, allowing the owner to potentially execute privileged functions without community oversight or time-locks.

**Recommendation:** Transfer ownership to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks.


### `M-01` — Lack of Transparency  *(Severity: Medium · Status: Unresolved)*

The absence of verified code prevents the community from understanding the tokenomics, tax structures, or potential minting capabilities.

**Recommendation:** Publish the source code and provide documentation detailing all administrative functions and economic parameters.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.4% of supply. Of that, 11.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 69.2% in wallets, 0.0% in other contracts. 1,385 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,385 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 31 Oct 2027 (372 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $247.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x679f...7777`](https://bscscan.com/address/0x679f0211668363cdcea269f9e0375dd0e7f97777) |
| **Network** | BNB Chain |
| **Price** | $0.007287 |
| **24h Volume** | $247.38M |
| **Liquidity** | $1.57M |
| **Volume / Liquidity** | 157.5× |
| **Token Age** | 5h |
| **Top-10 Holders** | 80.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2925 buys / 2761 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xce1ee510553897553e6d72cfe76e10eb04179157)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bibiai-bsc-38f5)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*

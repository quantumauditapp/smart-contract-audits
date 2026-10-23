---
token: Niannian_GiggleAcademy
ticker: 年年
network: bsc
risk_score: 70
status: high
date: 2026-10-23
---

# Niannian_GiggleAcademy (年年) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nianniangiggleacademy-bsc-6630)

---

## Audit Summary

The contract at the provided address is not verified on the block explorer, preventing any static or dynamic analysis of the source code. The contract is controlled by an EOA (Externally Owned Account), and ownership has not been renounced, posing a significant centralization risk. Investors should exercise extreme caution as the lack of transparency precludes verification of tax mechanisms, minting capabilities, or liquidity lock status.

> **Final Recommendation:** Do not interact with this contract until the source code is verified on the block explorer. Verify the contract logic for hidden minting functions, ownership transfer mechanisms, and tax logic before considering any financial exposure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security cannot be assessed due to the lack of verified source code. 7.3 Access Control is likely centralized under an EOA, which is a common vector for rug-pulls. 7.6… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance parameters are hidden from public view. The EOA owner has full control over potential minting or tax functions. There is no evidence of a DAO or decentralized… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades cannot be verified. If the contract is a proxy, the implementation logic is obscured. Without source verification, the ability to modify contract behavior post-deployment remains a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for backdoors, honeypot mechanisms, or logic errors.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `H-01` — Centralized Ownership  *(Severity: High · Status: Unresolved)*

The contract is controlled by an EOA, and ownership has not been renounced, allowing the owner to potentially modify critical parameters or drain liquidity.

**Recommendation:** Renounce ownership or transfer control to a multi-signature wallet or a time-locked governance contract.


### `M-01` — Lack of Transparency  *(Severity: Medium · Status: Unresolved)*

The absence of verified code prevents users from understanding the tokenomics, including potential transaction taxes or transfer restrictions.

**Recommendation:** Provide a clear, documented whitepaper and verified code to establish trust with the community.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.4% of supply. Of that, 10.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 69.5% in wallets, 0.0% in other contracts. 1,387 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,387 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 31 Oct 2027 (372 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.5M (DexScreener, all pools). 24h trading volume $285.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.5M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x790d...7777`](https://bscscan.com/address/0x790d54a05292bbb2516ce96223127afacc827777) |
| **Network** | BNB Chain |
| **Price** | $0.005836 |
| **24h Volume** | $285.00M |
| **Liquidity** | $1.48M |
| **Volume / Liquidity** | 192.2× |
| **Token Age** | 11h |
| **Top-10 Holders** | 80.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3636 buys / 3623 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3bf7981bfbbae865fcb7ab79a408fce296874e4f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nianniangiggleacademy-bsc-6630)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*

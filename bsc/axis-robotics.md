---
token: Axis Robotics
ticker: AXIS
network: bsc
risk_score: 77
status: high
date: 2026-10-21
---

# Axis Robotics (AXIS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/axis-robotics-bsc)

---

## Audit Summary

The contract at the provided address is not verified on the block explorer. Consequently, the source code is inaccessible for security analysis. The contract is controlled by an EOA (Externally Owned Account), and ownership has not been renounced, posing significant centralization risks to token holders.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, it is impossible to determine if the contract contains backdoors, malicious tax logic, or minting vulnerabilities. Investors should prioritize projects with verified, audited, and transparent source code.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown; 7.2 Code Security: Unverifiable; 7.3 Access Control: Centralized EOA; 7.6 External: Unknown. The lack of source code verification prevents any assessment of logic… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: High risk due to lack of transparency in tokenomics; 7.5 Governance: Fully centralized under an EOA. The owner has unilateral control over the contract, which could lead to rug-pull… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Unknown; 7.8 Operations: High risk. While the contract does not appear to be a standard proxy, the lack of verification means hidden upgradeability or logic-swapping mechanisms cannot… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for security vulnerabilities or malicious logic.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `H-01` — Centralized Ownership  *(Severity: High · Status: Unresolved)*

The contract is controlled by an EOA, which allows the owner to potentially modify critical parameters or restrict user access without notice.

**Recommendation:** Renounce ownership or transfer control to a multi-signature wallet or a decentralized governance contract.


### `M-01` — Lack of Transparency  *(Severity: Medium · Status: Unresolved)*

The absence of verified code prevents users from understanding the tokenomics, tax structures, or transfer restrictions implemented in the contract.

**Recommendation:** Provide a clear, documented whitepaper and verify the contract code to build trust with the community.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.4% of supply. Of that, 7.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 73.1% in wallets, 0.0% in other contracts. 1,389 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,389 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 31 Oct 2027 (375 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.2M (DexScreener, all pools). 24h trading volume $279.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.2M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb3a3...7777`](https://bscscan.com/address/0xb3a30fbaecc17da5711d6dfcdc04280dbb967777) |
| **Network** | BNB Chain |
| **Price** | $0.01417 |
| **24h Volume** | $279.54M |
| **Liquidity** | $2.17M |
| **Volume / Liquidity** | 128.8× |
| **Token Age** | 10h |
| **Top-10 Holders** | 80.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3789 buys / 3709 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1f7ce856254e7fc817e28b1745b3f77c38a1cae9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/axis-robotics-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

---
token: Axis Robotics
ticker: AXIS
network: bsc
risk_score: 75
status: high
date: 2026-10-21
---

# Axis Robotics (AXIS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/axis-robotics-bsc-58cc)

---

## Audit Summary

The contract at the provided address is not verified on the BSC block explorer. Consequently, the source code is unavailable for security analysis. The project exhibits high risk due to lack of transparency, centralized ownership by an EOA, and the inability to verify internal logic or tax mechanisms.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, it is impossible to determine if the contract contains malicious functions such as honeypot mechanisms, blacklists, or unauthorized minting capabilities. Investors should prioritize projects with verified source code and audited smart contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Unverifiable due to lack of source code. 7.3 Access Control: Centralized control via EOA. 7.6 External: Unknown dependency risks. |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: High risk of rug-pull or hidden tax mechanisms. 7.5 Governance: Fully centralized under an EOA. 7.8 Operations: Lack of transparency regarding project management. |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Contract is not identified as a proxy, but logic cannot be confirmed. No upgradeability features can be verified. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security review of the logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security analysis.


### `H-01` — Centralized Ownership  *(Severity: High · Status: Unresolved)*

The contract is owned by an EOA (0x34f0...), which grants the owner full control over administrative functions without time-locks or multi-sig protection.

**Recommendation:** Transfer ownership to a multi-signature wallet or a DAO-governed contract to mitigate single-point-of-failure risks.


### `M-01` — Lack of Transparency  *(Severity: Medium · Status: Unresolved)*

The absence of verified code and project documentation creates an information asymmetry that poses significant risks to token holders.

**Recommendation:** Provide comprehensive documentation and verify all deployed contracts to establish trust with the community.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.4% of supply. Of that, 6.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 74.1% in wallets, 0.0% in other contracts. 1,395 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,395 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 31 Oct 2027 (374 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.3M (DexScreener, all pools). 24h trading volume $274.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.3M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd390...7777`](https://bscscan.com/address/0xd3901b360b03469e4f12481745196f5f88107777) |
| **Network** | BNB Chain |
| **Price** | $0.01596 |
| **24h Volume** | $274.08M |
| **Liquidity** | $2.27M |
| **Volume / Liquidity** | 120.6× |
| **Token Age** | 7h |
| **Top-10 Holders** | 80.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3731 buys / 3623 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xcbd4b453e9a705fa1f9526b26fab8a8bc7b9915e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/axis-robotics-bsc-58cc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

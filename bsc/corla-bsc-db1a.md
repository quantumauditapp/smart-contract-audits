---
token: CORLA
ticker: CORLA
network: bsc
risk_score: 74
status: high
date: 2026-11-05
---

# CORLA (CORLA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/corla-bsc-db1a)

---

## Audit Summary

The contract at the provided address is not verified on the BSC block explorer. Consequently, the source code is inaccessible, preventing a technical security audit. The contract is currently controlled by an EOA, and ownership has not been renounced, posing significant centralization risks to token holders.

> **Final Recommendation:** Investors should exercise extreme caution as the contract is unverified and controlled by an EOA. It is strongly recommended to avoid interacting with this contract until the source code is verified on the block explorer and audited by a reputable third party. 

Prioritize assets where the contract source is transparent, ownership is renounced or managed by a multi-sig/DAO, and security audits are publicly available. Do not assume the contract functions as a standard token without independent verification.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown due to lack of source code. 7.2 Code Security: Cannot be verified; potential for backdoors or malicious logic exists. 7.3 Access Control: The contract is controlled by an… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Tokenomics are opaque without contract verification. 7.5 Governance: Centralized control via EOA allows for potential minting, pausing, or blacklisting. 7.8 Operations: Lack of… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract is not identified as a proxy, but without source code, the ability to modify logic cannot be ruled out. No upgradeability patterns are visible on-chain. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to verify the logic, security, or safety of the token.

**Recommendation:** Verify the contract source code on the block explorer immediately.


### `H-01` — Centralized EOA Ownership  *(Severity: High · Status: Unresolved)*

The contract is owned by an EOA (0x83dc...), which grants the owner full control over administrative functions without any time-locks or multi-signature requirements.

**Recommendation:** Transfer ownership to a multi-signature wallet or renounce ownership if no administrative functions are required.


### `M-01` — Lack of Transparency  *(Severity: Medium · Status: Unresolved)*

The absence of verified code prevents users from understanding the token's economic model, tax mechanisms, or potential anti-whale features.

**Recommendation:** Publish documentation and verified code to provide transparency to the community.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.4% of supply. Of that, 8.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 72.0% in wallets, 0.0% in other contracts. 1,387 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,387 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 30 Nov 2027 (389 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $254.5M (DexScreener, all pools).

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
| **Contract** | [`0xd686...7777`](https://bscscan.com/address/0xd686a88a5c102bbcebd0d747734a809ea3207777) |
| **Network** | BNB Chain |
| **Price** | $0.008167 |
| **24h Volume** | $254.48M |
| **Liquidity** | $1.61M |
| **Volume / Liquidity** | 157.6× |
| **Token Age** | 7h |
| **Top-10 Holders** | 80.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2829 buys / 2765 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd7dc49ddf386713a53edd0ae7595704f4f6df2b8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/corla-bsc-db1a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*

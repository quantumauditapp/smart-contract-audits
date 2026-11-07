---
token: GREEN MORNING
ticker: GM
network: bsc
risk_score: 75
status: high
date: 2026-11-07
---

# GREEN MORNING (GM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/green-morning-bsc-a7f8)

---

## Audit Summary

The contract at the provided address is not verified on the block explorer, making it impossible to perform a static analysis of the source code. The contract is controlled by an EOA (Externally Owned Account) and ownership has not been renounced, presenting significant centralization risks. Investors should exercise extreme caution as the lack of transparency prevents verification of tax mechanisms, minting capabilities, or liquidity lock status.

> **Final Recommendation:** Do not interact with this contract. The lack of source code verification is a major red flag that prevents any meaningful security assessment. Without the ability to audit the code, there is no protection against malicious functions such as honeypots, blacklisting, or unauthorized minting.

If you are considering an investment, wait for the developer to verify the source code on the block explorer. Verify that the ownership has been renounced or transferred to a secure multi-sig wallet, and ensure that liquidity is locked in a reputable, audited protocol.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The source code is unavailable for inspection, preventing assessment of 7.1 Architecture and 7.2 Code Security. Without verification, it is impossible to confirm the presence of standard ERC-20… |
| **Governance / Economics** | 1/10 | High | The contract is controlled by an EOA, which poses a high risk regarding 7.4 Economic and 7.5 Governance parameters. Without source code, 7.6 External dependencies and potential hidden tax mechanisms… |
| **Upgrades** | 6/10 | Medium | The contract is not identified as a proxy, but 7.7 Upgrades and 7.8 Operations cannot be verified without source code. There is no guarantee that the contract is immutable. Users should assume the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security audit or verification of contract logic.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `H-01` — Centralized Ownership via EOA  *(Severity: High · Status: Unresolved)*

The contract is owned by an EOA and ownership has not been renounced, granting the owner full control over administrative functions.

**Recommendation:** Renounce ownership or transfer control to a time-locked multi-sig contract to improve decentralization and security.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.4% of supply. Of that, 1.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 79.0% in wallets, 0.0% in other contracts. 1,382 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,382 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 30 Nov 2027 (387 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $240.5M (DexScreener, all pools).

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
| **Contract** | [`0xdb5f...7777`](https://bscscan.com/address/0xdb5fa98738c5261f15a76a942c7f2bee392e7777) |
| **Network** | BNB Chain |
| **Price** | $0.0781 |
| **24h Volume** | $240.48M |
| **Liquidity** | $1.60M |
| **Volume / Liquidity** | 150.7× |
| **Token Age** | 5h |
| **Top-10 Holders** | 80.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2737 buys / 2628 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6237dbe86c9d5939d800ce9640a96bd6ba2c2191)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/green-morning-bsc-a7f8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*

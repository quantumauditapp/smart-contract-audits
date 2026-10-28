---
token: TestMachine
ticker: TEMCN
network: arbitrum
risk_score: 73
status: high
date: 2026-10-28
---

# TestMachine (TEMCN) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/testmachine-arb)

---

## Audit Summary

The contract at the provided address is not verified on the Arbitrum block explorer. Consequently, the source code is unavailable for inspection. Investors cannot verify the contract's logic, ownership structure, or potential backdoors. Interaction with unverified contracts carries extreme risk of total loss of funds.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, there is no way to ensure the safety of your assets or the integrity of the contract's functions. If you are a token holder, consider the high probability of malicious intent or hidden vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified. 7.3 Access Control: Cannot be verified. 7.6 External: Cannot be verified. The absence of source code prevents any assessment of… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Unknown. 7.5 Governance: Unknown. 7.8 Operations: Unknown. Without visibility into the contract, it is impossible to determine if there are minting functions, tax mechanisms, or… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Unknown. It is impossible to determine if the contract is immutable or if it utilizes a proxy pattern that allows for logic updates by an owner. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security audit or verification of contract behavior.

**Recommendation:** Publish the source code on the block explorer to allow for community and security review.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xd353…e06c — holds 99.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.2% of supply. What remains: 82.2% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 7.5%. 2,128 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,128 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $78K (DexScreener, all pools). 24h trading volume $189K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $78K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x56ef...b56b`](https://arbiscan.io/address/0x56ef273754fa5ead63e0ba26c40431d35d09b56b) |
| **Network** | Arbitrum |
| **Price** | $0.02908 |
| **24h Volume** | $189.3K |
| **Liquidity** | $78.2K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 12h |
| **Top-10 Holders** | 82.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 605 buys / 76 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x5da102945538ad756477446380a0d9f99bc785c5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/testmachine-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*

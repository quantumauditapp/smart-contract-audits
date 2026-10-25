---
token: Navra
ticker: NAVA
network: arbitrum
risk_score: 77
status: high
date: 2026-10-25
---

# Navra (NAVA) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/navra-arb)

---

## Audit Summary

The contract at the provided address is not verified on the Arbitrum block explorer. As the source code is unavailable, it is impossible to perform a technical security audit or verify the contract's logic, ownership structure, or potential backdoors. Users should exercise extreme caution as unverified contracts often lack transparency and may contain malicious functions.

> **Final Recommendation:** Do not interact with this contract until the source code is verified on the block explorer and a professional security audit is conducted. Verify the contract's ownership and supply distribution through public data before considering any participation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be evaluated due to the lack of source code. 7.1 Architecture, 7.2 Code Security, and 7.3 Access Control are entirely opaque. Without verification, there is no… |
| **Governance / Economics** | 1/10 | High | Economic parameters and governance mechanisms are hidden from public view. 7.4 Economic and 7.5 Governance items remain unverified. There is no way to confirm if the token supply is capped or if… |
| **Upgrades** | 6/10 | Medium | Upgradeability status is unknown as the contract bytecode is not mapped to source. 7.7 Upgrades and 7.8 Operations cannot be audited. The contract may be a proxy or contain self-destruct mechanisms… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not verified on the block explorer, preventing any security analysis of the underlying logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for transparency and independent security review.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xdc74…2f04 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.6% of supply. Of that, 2.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 91.2% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 1.7%. 409 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

409 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $252K (DexScreener, all pools). 24h trading volume $120K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $252K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3456...6d73`](https://arbiscan.io/address/0x3456eb26030cfed865356da23e7bb8ba2fb26d73) |
| **Network** | Arbitrum |
| **Price** | $0.05258 |
| **24h Volume** | $119.6K |
| **Liquidity** | $251.8K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 5h |
| **Top-10 Holders** | 93.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 585 buys / 269 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xdc638e2983c0c83a3ba5b54d049b8071e2725006)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/navra-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*

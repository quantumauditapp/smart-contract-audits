---
token: 销毁丸
ticker: 销毁丸
network: bsc
risk_score: 59
status: medium
date: 2026-11-06
---

# 销毁丸 (销毁丸) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-c17ebc-bsc)

---

## Audit Summary

The contract at the provided address is not verified on the BSC block explorer. Consequently, the source code is inaccessible for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with this contract. The absence of verified source code is a major red flag that prevents any meaningful security assessment. Without transparency, there is no way to ensure the safety of funds or the integrity of the token's economic model.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be evaluated due to lack of source code. 7.3 Access Control: Cannot be verified, posing a risk of unauthorized administrative actions. 7.6… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic: Tokenomics and tax logic are opaque. 7.5 Governance: Potential for rug-pulls or malicious minting cannot be ruled out. 7.8 Operations: Operational security is entirely dependent on the… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades: The upgradeability status is unknown. Without source code, it is impossible to determine if the contract is a proxy or if it contains hidden upgrade logic. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer. This prevents any security analysis or verification of contract logic.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `H-02` — Opaque Administrative Privileges  *(Severity: High · Status: Unresolved)*

Due to the lack of source code, it is impossible to determine if the contract contains owner-only functions that could lead to fund theft, blacklisting, or unauthorized minting.

**Recommendation:** Renounce ownership or provide a transparent, time-locked governance structure if the contract is intended for public use.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.4% of supply. Of that, 90.1% burned, 2.0% locked, 2.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.8% in wallets, 0.2% in other contracts. 1,304 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,304 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $45K (DexScreener, all pools). 24h trading volume $128K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 3% on buy, 2.99% on sell. Market: $45K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x96b7...0c71`](https://bscscan.com/address/0x96b7054deab2a01643f5eb21b06253bb3cd10c71) |
| **Network** | BNB Chain |
| **Price** | $0.0009181 |
| **24h Volume** | $128.1K |
| **Liquidity** | $44.7K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 1d |
| **Top-10 Holders** | 95.4% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 5672 buys / 3615 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x46d7821fa450f3722a3e64b4cd9c68fd1ff16685)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-c17ebc-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*

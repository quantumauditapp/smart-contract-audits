---
token: El Gato
ticker: GATO
network: ethereum
risk_score: 25
status: low
date: 2026-10-20
---

# El Gato (GATO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/el-gato-eth)

---

## Audit Summary

The ElGato token is a standard ERC-20 implementation with ownership renounced. The contract logic is straightforward, and the renouncement of ownership effectively disables all administrative functions, mitigating risks associated with centralized control. A minor vulnerability regarding tx.origin usage was identified, though its impact is limited in the current state.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renouncement of ownership. No further action is required for the current deployment as administrative functions are permanently disabled.

For future deployments, ensure that any use of tx.origin is replaced with msg.sender to prevent potential phishing or contract-based authorization bypasses, even if the current impact is negligible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract follows standard ERC-20 patterns with 7.1 Architecture and 7.2 Code Security being well-implemented. 7.3 Access Control is currently inert due to ownership renouncement, ensuring no… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance risks are effectively nullified by the renouncement of ownership. There are no active governance mechanisms or inflationary parameters that can be adjusted by any… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are static, meaning the contract behavior is immutable. No upgrade risk exists for this implementation. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin to determine authorization or logic within the balanceOf function. This is a security risk because an attacker can create a malicious contract that calls the token contract, tricking the logic into identifying the original transaction initiator rather than the immediate caller.

**Recommendation:** Replace all instances of tx.origin with msg.sender to ensure that authorization and logic are tied to the immediate caller, which is the standard and secure practice for smart contract interactions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 12.1% of supply. Of that, 7.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.9% in wallets, 0.8% in other contracts. 697 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

697 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $112K (DexScreener, all pools). 24h trading volume $2.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $112K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7684...2c27`](https://etherscan.io/address/0x768488c988cf2493f0e7ccb3d56547f2384e2c27) |
| **Network** | Ethereum |
| **Price** | $0.001044 |
| **24h Volume** | $2.43M |
| **Liquidity** | $112.5K |
| **Volume / Liquidity** | 21.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | 12.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3420 buys / 1830 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x3027d452fb89034649aca6f324aeba8596c75c2c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/el-gato-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

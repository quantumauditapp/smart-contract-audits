---
token: Veridia
ticker: VERIDIA
network: ethereum
risk_score: 7
status: low
date: 2026-10-04
---

# Veridia (VERIDIA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/veridia-eth)

---

## Audit Summary

The audit of the LaunchToken contract revealed a standard ERC-20 implementation with no custom privileged functions or complex transfer logic. No critical or high-severity vulnerabilities were identified during the analysis.

> **Final Recommendation:** Given the contract's simplicity as a standard ERC-20 token with no custom privileged functions or complex logic, the primary recommendation is to ensure thorough testing of all standard ERC-20 functionalities. Additionally, verify that the deployment parameters, such as initial supply and decimals, are correctly configured. For any future integrations, ensure external protocols correctly handle standard ERC-20 behaviors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The LaunchToken contract implements a standard ERC-20 token. It includes all expected ERC-20 functions such as `transfer`, `transferFrom`, and `approve`. The static analysis (7.2 Code Security)… |
| **Governance / Economics** | 9/10 | Low | The LaunchToken contract does not incorporate any governance mechanisms (7.5 Governance) or complex economic models (7.4 Economic). There are no privileged roles or functions that can alter token… |
| **Upgrades** | 9/10 | Low | The LaunchToken contract is not implemented as a proxy (7.7 Upgrades) and therefore is not upgradeable. This eliminates risks associated with upgradeability, such as proxy misconfigurations or logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 25.1% |
| **Top-3 Unlocked** | 62.7% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.7% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 57% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.7% of supply. Of that, 4.3% burned — not holders that can sell, so excluded from the concentration score. What remains: 6.3% in wallets, 22.1% in other contracts. 718 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

718 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $155K (DexScreener, all pools). 24h trading volume $995K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $155K of DEX liquidity across 17 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x255c...90cf`](https://etherscan.io/address/0x255cf35cc469ffa9b5c74a721e899380834e90cf) |
| **Network** | Ethereum |
| **Price** | $0.0005401 |
| **24h Volume** | $800.5K |
| **Liquidity** | $88.6K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 6d |
| **Top-10 Holders** | 32.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1564 buys / 1028 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xaf04a9c146aff55ffbef1883354a4c547155c2d43d335d902287024d06742ef6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/veridia-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*

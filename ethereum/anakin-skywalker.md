---
token: Anakin Skywalker
ticker: ANAKIN
network: ethereum
risk_score: 66
status: high
date: 2026-11-01
---

# Anakin Skywalker (ANAKIN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anakin-skywalker-eth)

---

## Audit Summary

The ANAKIN contract is a standard ERC-20 token implementation. It lacks any privileged administrative functions, blacklists, or tax mechanisms, making it a simple, immutable asset. No vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The contract is secure and follows best practices for a standard ERC-20 token. No further action is required as the code is immutable and free of administrative backdoors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows the standard OpenZeppelin ERC-20 implementation, ensuring high compatibility with existing DeFi protocols. 7.1 Architecture is clean and modular, while 7.2 Code Security… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are not applicable as the token is a simple utility asset. There are no minting, burning, or fee-on-transfer mechanisms that could impact market stability. The… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported, as the contract is not a proxy. This provides maximum security against upgrade-related exploits or malicious logic changes. 7.8 Operations are straightforward, with no… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xe37b…2cc3) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 23.3% of supply. Of that, 4.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.3% in wallets, 0.0% in other contracts. 349 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

349 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $117K (DexScreener, all pools). 24h trading volume $591K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $117K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcaf9...316d`](https://etherscan.io/address/0xcaf9faa57678e67636bdf87e2e6245c13e95316d) |
| **Network** | Ethereum |
| **Price** | $0.001573 |
| **24h Volume** | $590.7K |
| **Liquidity** | $117.3K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 5h |
| **Top-10 Holders** | 23.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 517 buys / 366 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xb3ff2722ee44c94e0de11b847f35e2bd4735eac3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anakin-skywalker-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*

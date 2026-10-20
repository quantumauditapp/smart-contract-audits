---
token: DNA
ticker: DNA
network: ethereum
risk_score: 0
status: low
date: 2026-10-13
---

# DNA (DNA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dna-eth)

---

## Audit Summary

The DNAToken contract is a standard ERC-20 token implementation. The audit found no critical or high-severity vulnerabilities. The contract lacks privileged functions, reducing attack vectors related to centralized control. Its simplicity contributes to a low overall risk profile.

> **Final Recommendation:** Token holders should be aware that DNAToken is a standard, non-upgradeable ERC-20 token. Its simplicity and lack of privileged functions contribute to a robust security posture. Users should always exercise caution when interacting with any token, verifying the contract address and understanding the implications of approving spending limits for third-party applications.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The DNAToken contract implements the standard ERC-20 interface, including `transfer`, `transferFrom`, `approve`, `balanceOf`, and `totalSupply`. The code analysis (7.2 Code Security) revealed no… |
| **Governance / Economics** | 10/10 | Low | The contract functions purely as a basic ERC-20 token without any integrated governance mechanisms (7.5 Governance) or complex economic models (7.4 Economic). There are no parameters that can be… |
| **Upgrades** | 10/10 | Low | The DNAToken contract is not implemented as a proxy (7.7 Upgrades) and is therefore not upgradeable. This eliminates all risks associated with upgradeability, such as potential vulnerabilities… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 38.4% of supply. What remains: 7.6% in wallets, 30.8% in other contracts. 1,057 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as DNA (DNA), rank #4440. 1,057 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 85% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $98K (DexScreener, all pools). 24h trading volume $473K (CoinGecko, all markets, daily snapshot). 24h trading volume $794K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $98K of DEX liquidity across 21 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3977...8402`](https://etherscan.io/address/0x39772d019ed525f667a7cbbf8e64b07120378402) |
| **Network** | Ethereum |
| **Price** | $0.0002802 |
| **24h Volume** | $575.3K |
| **Liquidity** | $83.6K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 1d |
| **Top-10 Holders** | 38.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1181 buys / 816 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf6187f124e9aca0628d50a59d1c81538a4f961edee92227af5145f1e9f0ca370)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dna-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*

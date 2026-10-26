---
token: Binance Agent
ticker: 7AGENT
network: bsc
risk_score: 24
status: low
date: 2026-10-26
---

# Binance Agent (7AGENT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-agent-bsc-d3cc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token. The contract ownership has been renounced on-chain, rendering all privileged administrative functions (such as migration controls) permanently dormant. The codebase is standard and utilizes OpenZeppelin's upgradeable library patterns, though the deployment architecture itself is immutable.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renounced ownership. No further action is required for the current deployment. Users should verify the contract address against the official project documentation to ensure they are interacting with the correct instance.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the EIP-1167 standard, ensuring a lightweight and gas-efficient deployment. 7.1 Architecture is sound for a fixed-logic token, while 7.2 Code Security is maintained through… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic parameters are fixed by the renounced ownership, preventing any further manipulation of tax or migration states. 7.5 Governance is non-existent as the contract is immutable and… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are impossible for this EIP-1167 clone, providing high security against proxy-based attacks. The implementation is fixed at the time of deployment. 7.8 Operations are stable as the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 95.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x3e6b…c99a — holds 95.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 24.5% of supply. What remains: 6.5% in wallets, 18.0% in other contracts. 742 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

742 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31K (DexScreener, all pools). 24h trading volume $523K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb726...7777`](https://bscscan.com/address/0xb726477d1743b02c5fdae5ab094745665eeb7777) |
| **Network** | BNB Chain |
| **Price** | $0.0001019 |
| **24h Volume** | $403.8K |
| **Liquidity** | $30.8K |
| **Volume / Liquidity** | 13.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 24.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3386 buys / 2427 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x690e21d626cd7896d08740d69767f8c6e6a5aae5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-agent-bsc-d3cc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*

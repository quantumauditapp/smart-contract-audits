---
token: Token
ticker: 词元
network: bsc
risk_score: 42
status: medium
date: 2026-11-02
---

# Token (词元) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-bsc-4ff1)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with migration-based state transitions. Ownership has been renounced on-chain, rendering all privileged administrative functions dormant and immutable. The protocol is secure against unauthorized administrative interference.

> **Final Recommendation:** No security issues were identified. As ownership is renounced, the protocol is in a final, immutable state. Users should verify the current state of the poolState via public read functions to understand the active tax and anti-farmer parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a gas-efficient EIP-1167 minimal clone pattern. 7.1 Architecture is robust, 7.2 Code Security is high due to standard library usage, and 7.3 Access Control is effectively… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance risks are mitigated by the renunciation of ownership. No single entity can influence the poolState or tax parameters post-deployment. The economic model is now… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not possible as the contract is a minimal clone pointing to a fixed implementation. 7.8 Operations are stable and require no further maintenance. The contract is effectively… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x14e5…be4a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $326K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.3% of supply. What remains: 13.6% in wallets, 31.7% in other contracts. 330 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

330 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $9K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbc2c...7777`](https://bscscan.com/address/0xbc2cb02f7dcca9ccdee6adf8ecada8886fd67777) |
| **Network** | BNB Chain |
| **Price** | $0.0000109 |
| **24h Volume** | $307.3K |
| **Liquidity** | $8.9K |
| **Volume / Liquidity** | 34.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 45.3% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 2966 buys / 2840 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc8e561fb8c3279540888c5dad7aa53b0ed443d5c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-bsc-4ff1)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*

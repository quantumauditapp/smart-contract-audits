---
token: EverValueCoin
ticker: EVA
network: arbitrum
risk_score: 19
status: low
date: 2026-10-09
---

# EverValueCoin (EVA) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/evervaluecoin-arb)

---

## Audit Summary

The EverValueCoin contract is a standard ERC-20 token implementation. Static analysis confirms the absence of privileged functions or centralized control over token transfers. No critical vulnerabilities or significant issues were identified during the audit.

> **Final Recommendation:** Users should verify the contract's address and ensure they understand its immutable nature as a standard ERC-20 token without special features or administrative control. For the deployer, ensure that any initial token distribution or liquidity provision is handled securely, as the contract itself offers no further administrative capabilities. Adherence to standard security practices for interacting with EVM tokens is always recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The EverValueCoin contract implements the standard ERC-20 token interface, including `totalSupply()`, `balanceOf()`, `transfer()`, `transferFrom()`, `approve()`, and `allowance()`. The architecture… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of decentralization as there are no privileged functions or administrative roles capable of influencing token transfers or economic parameters (7.5 Governance).… |
| **Upgrades** | 8/10 | Low | The EverValueCoin contract is not implemented as a proxy and does not include any upgradeability mechanisms (7.7 Upgrades). This design choice eliminates all risks associated with upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x0ba4…b01b — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.6% of supply. What remains: 14.1% in wallets, 15.5% in other contracts. 8,567 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as EverValue Coin (EVA). 8,567 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $177K (DexScreener, all pools). 24h trading volume $44K (CoinGecko, all markets, daily snapshot). 24h trading volume $32K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $177K of DEX liquidity across 4 pools. Launch: 819 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x45d9...1c8c`](https://arbiscan.io/address/0x45d9831d8751b2325f3dbf48db748723726e1c8c) |
| **Network** | Arbitrum |
| **Price** | $44.6100 |
| **24h Volume** | $31.5K |
| **Liquidity** | $174.3K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 29.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 68 buys / 127 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x076994463d511adbe0c113b93dcb084a839b0d80)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/evervaluecoin-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*

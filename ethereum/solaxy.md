---
token: Solaxy
ticker: SOLX
network: ethereum
risk_score: 31
status: low
date: 2026-10-10
---

# Solaxy (SOLX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solaxy-eth)

---

## Audit Summary

This audit covers an ERC-20 token contract. The contract's ownership has been renounced, eliminating central control risks. One medium-severity issue was identified related to the use of `tx.origin` in the token transfer logic, which could potentially be exploited in phishing scenarios.

> **Final Recommendation:** It is crucial to address the identified `tx.origin` vulnerability by replacing its usage with `msg.sender` in the `_transfer` function's rule-making logic. This change will ensure that authorization and critical decisions are based on the immediate caller, mitigating potential phishing and re-entrancy attack vectors. Although ownership is renounced, ensuring the core transfer logic is robust against such patterns is vital for user security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements the ERC-20 standard, providing standard token functionalities such as `transfer` and `transferFrom`. A medium-severity issue (7.2 Code Security) was identified where the… |
| **Governance / Economics** | 8/10 | Low | The contract's ownership has been renounced on-chain (7.5 Governance), meaning no single entity can control or alter the contract's core parameters or transfer rules, such as `uniswapPool`. This… |
| **Upgrades** | 9/10 | Low | The contract is not designed with any upgradeability mechanisms (7.7 Upgrades). This means its logic is immutable once deployed, providing certainty but also preventing future bug fixes or feature… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — UNCX Locker |
| **Top-1 Unlocked Holder** | 0.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity lock has expired  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% still sits in UNCX Locker, but that lock expired on 23 Jun 2026 — its owner can withdraw it at any moment. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Risk from `tx.origin` usage in transfer logic  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function, which is central to moving tokens, uses `tx.origin` to determine a rule. This means that if a user interacts with a malicious contract, that contract could potentially trick the token contract into performing actions on behalf of the original user (`tx.origin`), even if the malicious contract is the direct caller (`msg.sender`). This is a known vulnerability pattern that can lead to phishing attacks.

**Recommendation:** It is recommended to replace `tx.origin` with `msg.sender` in the `_transfer` function's rule-making logic. `msg.sender` reliably identifies the immediate caller, preventing intermediate contracts from manipulating authorization or rules intended for the direct user.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.7% of supply. Of that, 7.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.1% in wallets, 51.6% in other contracts. 52,754 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Solaxy (SOLX), market cap $2M, rank #2490. 52,754 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $223K (DexScreener, all pools). 24h trading volume $102K (CoinGecko, all markets, daily snapshot). 24h trading volume $53K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0014 on 2025-07-01; the price is now 98.486% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $223K of DEX liquidity across 4 pools. Launch: 473 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe0b7...cf48`](https://etherscan.io/address/0xe0b7ad7f8f26e2b00c8b47b5df370f15f90fcf48) |
| **Network** | Ethereum |
| **Price** | $0.00001905 |
| **24h Volume** | $53.3K |
| **Liquidity** | $222.7K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 80.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 80 buys / 38 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x7e75b6876a9fee811ec67b55385ba5a1491d11f3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solaxy-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*

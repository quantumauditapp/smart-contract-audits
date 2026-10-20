---
token: Whuffie
ticker: WHUF
network: base
risk_score: 49
status: medium
date: 2026-10-09
---

# Whuffie (WHUF) — Smart Contract Security Analysis | Base

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/whuffie-base)

---

## Audit Summary

The EthosWhuffie contract is an ERC-20 token implemented as a UUPS proxy. Ownership of the contract has been renounced, meaning no single entity can exercise privileged functions such as minting, pausing transfers, or unlocking transfers. This significantly reduces centralisation risk. One informational finding was identified regarding dormant privileged controls.

> **Final Recommendation:** Given that ownership has been renounced, the EthosWhuffie token contract is highly decentralized and immutable in its current state. Token holders should be aware that no further upgrades or administrative actions (like minting or pausing) can be performed. It is recommended to ensure that the current state of the `transfersUnlocked` variable aligns with the intended operational status of the token, as this state is now permanent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The EthosWhuffie contract is a standard ERC-20 token utilizing the UUPS proxy pattern (7.1 Architecture). It includes standard ERC-20 functions like `transfer` and `balanceOf`. The contract… |
| **Governance / Economics** | 6/10 | Medium | The economic model of EthosWhuffie is characterized by its ERC-20 standard implementation (7.4 Economic). Crucially, the contract's ownership has been renounced (7.5 Governance). This means that no… |
| **Upgrades** | 3/10 | High | The EthosWhuffie contract uses the UUPS (Universal Upgradeable Proxy Standard) pattern (7.7 Upgrades), allowing for future logic upgrades. However, since ownership has been renounced, the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.1% |
| **Top-3 Unlocked** | ⚠️ 96.9% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 7 address(es) other than the owner/deployer. One of them — a wallet, 0x2713…835c — holds 92.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 81% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-05` — A privileged address controls a switch that decides whether transfers go through  *(Severity: Informational · Status: Unresolved)*

An on/off setting checked in the transfer path can be changed by a privileged function; depending on its value, transfers or sales are allowed or refused. Ownership is renounced, so no one can call these functions now. Functions: mint, mintBatch, unlockTransfers. Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.9% of supply. What remains: 2.9% in wallets, 91.0% in other contracts. 1,544 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Whuffie (WHUF), market cap $8M, rank #1408. Traded on Coinbase. 1,544 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $355K (DexScreener, all pools). 24h trading volume $2.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $3.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable, capped at 0.6% of supply per year. Control: nobody (ownership renounced). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $355K of DEX liquidity across 22 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeeee...eeee`](https://basescan.org/address/0xeeee77bc7e82c0d4166d52f58239d4c5bf41eeee) |
| **Network** | Base |
| **Price** | $3.7200 |
| **24h Volume** | $2.77M |
| **Liquidity** | $286.1K |
| **Volume / Liquidity** | 9.7× |
| **Token Age** | 2d |
| **Top-10 Holders** | 93.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3622 buys / 1980 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x7735599c022c840da8bb5c2caa739a8d839aa299)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/whuffie-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*

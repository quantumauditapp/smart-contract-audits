---
token: Treehouse Token
ticker: TREE
network: ethereum
risk_score: 36
status: medium
date: 2026-10-24
---

# Treehouse Token (TREE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/treehouse-token-eth)

---

## Audit Summary

The TreehouseToken is a standard ERC-20 implementation utilizing UUPS proxy patterns and OpenZeppelin's upgradeable library. The contract includes governance capabilities via ERC-20Votes and is managed by a Timelock controller. No critical or high-severity vulnerabilities were identified in the provided source code.

> **Final Recommendation:** The protocol is well-structured and follows security best practices. We recommend maintaining the current Timelock configuration for all administrative actions and ensuring that the private keys for the Timelock controller are stored in a multi-signature wallet or hardware security module.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows industry-standard patterns (7.1 Architecture) using OpenZeppelin's battle-tested libraries. Code security (7.2) is high due to the use of audited upgradeable contracts and… |
| **Governance / Economics** | 1/10 | High | Economic (7.4) and Governance (7.5) parameters are robust, as the contract is managed by a 5-day Timelock. This ensures that any administrative changes, such as setting the CCIP admin, are subject to… |
| **Upgrades** | 2/10 | High | The contract utilizes the UUPS proxy pattern (7.7), which is the current industry standard for upgradeability. Operations (7.8) are protected by the Timelock, ensuring that upgrades cannot be… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xb494…3b91 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 52% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 87.6% of supply. What remains: 16.8% in wallets, 70.8% in other contracts. 10,434 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Treehouse (TREE), market cap $7M, rank #1428. Traded on Coinbase. 10,434 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $509K (DexScreener, all pools). 24h trading volume $12.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $937K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.36 on 2025-07-29; the price is now 96.7206% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Liquid Staking Governance Tokens. Tokenomics — Supply: fixed — the contract has no mint function. Control: a timelock with a 120h delay. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $509K of DEX liquidity across 4 pools. Launch: 456 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7714...d1f3`](https://etherscan.io/address/0x77146784315ba81904d654466968e3a7c196d1f3) |
| **Network** | Ethereum |
| **Price** | $0.04298 |
| **24h Volume** | $169.2K |
| **Liquidity** | $266.9K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 87.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 261 buys / 211 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xdaba3d8ccf79ef289a7e2dbce51871b39ea445a2-0x77146784315ba81904d654466968e3a7c196d1f3-0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/treehouse-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

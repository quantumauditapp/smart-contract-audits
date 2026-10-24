---
token: Rocket Pool Protocol
ticker: RPL
network: ethereum
risk_score: 38
status: medium
date: 2026-10-24
---

# Rocket Pool Protocol (RPL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rocket-pool-protocol-eth)

---

## Audit Summary

The RocketTokenRPL contract is a standard ERC-20 implementation facilitating the migration of legacy RPL tokens. The architecture is robust, utilizing established OpenZeppelin standards for token management. No critical or high-severity vulnerabilities were identified during the static analysis of the provided source code.

> **Final Recommendation:** The contract is secure and functions as intended for the RPL token migration. No immediate changes are required for the current implementation.

Maintain monitoring of the rplFixedSupplyContract address to ensure that the migration source remains valid and that no unauthorized changes are made to the protocol's registry.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 patterns with secure arithmetic operations via OpenZeppelin. 7.1 Architecture is modular, relying on a fixed supply contract for migration logic. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic parameters are defined by the migration ratio, which is 1:1. 7.5 Governance is handled via the broader protocol ecosystem rather than this specific token contract. The economic model is… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not applicable as this contract is not a proxy. 7.8 Operations are stable, with the contract serving as a static migration point. The lack of upgradeability ensures immutability of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 74.4% |
| **Top-3 Unlocked** | ⚠️ 90.9% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 6 address(es) other than the owner/deployer. One of them — a contract, 0xb867…8cb9 — holds 74.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 56% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.2% of supply. What remains: 19.2% in wallets, 54.0% in other contracts. 12,606 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Rocket Pool (RPL), market cap $35M, rank #582. Traded on Binance, Coinbase. 12,606 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $530K (DexScreener, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $103K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $61.90 on 2023-04-16; the price is now 97.5532% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $530K of DEX liquidity across 10 pools. Launch: 1807 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd335...a51f`](https://etherscan.io/address/0xd33526068d116ce69f19a9ee46f0bd304f21a51f) |
| **Network** | Ethereum |
| **Price** | $1.4800 |
| **24h Volume** | $102.8K |
| **Liquidity** | $297.2K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 5y |
| **Top-10 Holders** | 73.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 558 buys / 556 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xe42318ea3b998e8355a3da364eb9d48ec725eb45)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rocket-pool-protocol-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

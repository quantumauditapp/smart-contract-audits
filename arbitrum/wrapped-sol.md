---
token: Wrapped SOL
ticker: SOL
network: arbitrum
risk_score: 70
status: high
date: 2026-10-26
---

# Wrapped SOL (SOL) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-sol-arb)

---

## Audit Summary

The BridgeToken implementation is a standard ERC-20 token with administrative minting capabilities. The contract utilizes a Beacon proxy pattern for upgradability. No critical vulnerabilities were identified in the provided source code analysis. The protocol relies on a centralized owner contract to manage supply and metadata updates.

> **Final Recommendation:** The protocol is well-structured. It is recommended to transition the owner address to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single point of failure in the minting and upgrade processes. Ensure that the Beacon contract is also secured behind a multi-sig to prevent unauthorized implementation swaps.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality with robust arithmetic safety provided by Solidity 0.8.x. 7.1 Architecture follows a standard Beacon proxy pattern, ensuring consistent… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic risk is tied to the centralized minting authority, which can increase supply at will. 7.5 Governance is currently managed by an external contract, which acts as a single point of… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are handled via a Beacon proxy, allowing for implementation updates. 7.8 Operations are simplified by this pattern, though it introduces a dependency on the Beacon contract's integrity.… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 15.5% |
| **Top-3 Unlocked** | 42.3% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 82.1% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 8% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a contract — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.4% of supply. What remains: 27.7% in wallets, 53.6% in other contracts. 13,334 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wormhole Bridged WSOL (WSOL). 13,334 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.5M (DexScreener, all pools). 24h trading volume $240K (CoinGecko, all markets, daily snapshot). 24h trading volume $43K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Bridged-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $1.5M of DEX liquidity across 8 pools. Launch: 1149 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2bcc...0c07`](https://arbiscan.io/address/0x2bcc6d6cdbbdc0a4071e48bb3b969b06b3330c07) |
| **Network** | Arbitrum |
| **Price** | $100.6100 |
| **24h Volume** | $35.5K |
| **Liquidity** | $120.8K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 3y |
| **Top-10 Holders** | 81.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 45 buys / 60 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xdaf544bcab17e2dcd293c3af28e67c7e8b5a49ee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-sol-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*

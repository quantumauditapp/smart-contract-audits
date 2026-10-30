---
token: Nesa
ticker: NES
network: bsc
risk_score: 81
status: high
date: 2026-10-30
---

# Nesa (NES) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nesa-bsc)

---

## Audit Summary

The HypERC20 contract implements an interchain token bridge using a proxy architecture. The system relies on a multisig-controlled ProxyAdmin for upgrades and administrative configuration. While the core logic follows standard cross-chain patterns, the ability to mint tokens via the bridge mechanism introduces inherent economic risks regarding supply inflation.

> **Final Recommendation:** Maintain the current multisig threshold and ensure that all administrative actions are subject to a time-lock if possible. Regularly monitor the bridge's total supply across chains to detect any unauthorized minting events.

Ensure that the 'handle' function's integration with the mailbox remains strictly audited, as it is the primary vector for cross-chain token minting. Consider implementing a circuit breaker or pause mechanism to halt cross-chain transfers in the event of an detected anomaly.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes a robust Transparent Proxy pattern (7.1) with clear separation of concerns between the router and token logic. Code security (7.2) is high, leveraging established… |
| **Governance / Economics** | 1/10 | High | Economic risk (7.4) is primarily driven by the bridge's ability to mint tokens on the destination chain, which could lead to supply dilution if the bridge is compromised. Governance (7.5) is… |
| **Upgrades** | 1/10 | High | The contract supports transparent upgrades (7.7) managed by a dedicated ProxyAdmin. Operations (7.8) are well-defined, allowing for the enrollment of new remote routers and adjustment of gas… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 6-of-10 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — State Variable Shadowing  *(Severity: High · Status: Unresolved)*

The contract contains instances where local variables or inherited state variables shadow existing ones, potentially leading to incorrect state updates or logic errors during execution.

**Recommendation:** Rename shadowed variables to ensure clarity and prevent accidental overwriting of critical state data.


### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The functions 'transferRemote' and 'handle' allow for the creation of new tokens. This is a standard feature of cross-chain bridges, but it means that the bridge mechanism itself has the power to increase the total supply of the token, which could dilute existing holders if the bridge security is breached.

**Recommendation:** Implement strict monitoring on the total supply and ensure the mailbox contract is secured by a robust, multi-layered security module.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x19d8…b802 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.0% of supply. What remains: 59.3% in wallets, 39.6% in other contracts. 31,497 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Nesa (NES), market cap $36M, rank #572. 31,497 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.0M (GeckoTerminal, all pools). 24h trading volume $11.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $6.5M (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $1.0M of DEX liquidity across 7 pools. Launch: 51 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x097a...5b81`](https://bscscan.com/address/0x097acf27503753e77bca940277806156c5925b81) |
| **Network** | BNB Chain |
| **Price** | $0.11841268 |
| **24h Volume** | $6.47M |
| **Liquidity** | $1.01M |
| **Volume / Liquidity** | 6.4× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 99.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2559 buys / 3695 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x097acf27503753e77bca940277806156c5925b81)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nesa-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

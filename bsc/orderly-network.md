---
token: Orderly Network
ticker: ORDER
network: bsc
risk_score: 71
status: high
date: 2026-10-25
---

# Orderly Network (ORDER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orderly-network-bsc)

---

## Audit Summary

The OrderOFT contract implements a cross-chain token bridge using the LayerZero OFT standard. The architecture relies on a UUPS proxy pattern and is managed by a 2-of-3 multisig. The code follows standard library implementations with minimal custom logic, resulting in a robust security posture. One minor rounding issue was identified in the dust removal logic.

> **Final Recommendation:** The protocol demonstrates a high level of security maturity. We recommend maintaining the current multisig configuration and ensuring that any future upgrades undergo rigorous testing in a staging environment before deployment to mainnet.

For the identified rounding issue, ensure that the dust removal logic is consistent across all chains to prevent minor discrepancies in token balances during cross-chain transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes established LayerZero OFT patterns for cross-chain messaging. 7.1 Architecture is modular, separating core logic from proxy storage. 7.2 Code Security is high, leveraging… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are mitigated by the use of a 2-of-3 multisig wallet. The bridge parameters, such as peers and enforced options, are controlled by this multisig. 7.6 External… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are handled via the UUPS pattern, which is the current industry standard for gas-efficient and secure proxy upgrades. 7.8 Operations are supported by pause/unpause functionality… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 21.6% |
| **Top-3 Unlocked** | 53.5% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — a 2-of-3 multisig — pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 97.8% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Rounding loss in dust removal  *(Severity: Low · Status: Unresolved)*

The _removeDust function performs division before multiplication, which can lead to minor precision loss when calculating token amounts.

**Recommendation:** Reorder operations to perform multiplication before division to maintain maximum precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.5% of supply. Of that, 39.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 16.7% in wallets, 37.2% in other contracts. 3,289 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Orderly (ORDER), market cap $16M, rank #927. 3,289 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $378K (DexScreener, all pools). 24h trading volume $314.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $3.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: a copy of the coin from its home chain (ethereum), minted here by LayerZero (lzReceive). Tokenomics — Supply: fixed — the contract has no mint function. Control: a 2-of-3 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $378K of DEX liquidity across 3 pools. Launch: 570 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4e20...97b8`](https://bscscan.com/address/0x4e200fe2f3efb977d5fd9c430a41531fb04d97b8) |
| **Network** | BNB Chain |
| **Price** | $0.04705 |
| **24h Volume** | $3.25M |
| **Liquidity** | $377.4K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8019 buys / 9459 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa7df052672a24885d784a72b5f72d50296161531)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orderly-network-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*

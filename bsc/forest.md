---
token: Forest
ticker: FOREST
network: bsc
risk_score: 54
status: medium
date: 2026-10-21
---

# Forest (FOREST) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/forest-bsc)

---

## Audit Summary

The BridgeToken contract is a standard ERC-20 implementation utilizing a Beacon proxy pattern. The contract provides core token functionality with centralized administrative control over minting and metadata updates. No critical vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The protocol should ensure that the owner address (currently an external contract) is secured by a multi-signature wallet or a decentralized governance contract to mitigate the risk of single-point-of-failure. Regular monitoring of the mint function is recommended to ensure supply changes remain within expected parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The architecture follows a standard Beacon proxy pattern, ensuring consistent implementation across multiple instances. 7.1 Architecture and 7.2 Code Security are robust, utilizing standard… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are centered on the centralized owner address, which is currently an external contract. The owner has the authority to mint new tokens, which directly impacts… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via a Beacon proxy, which is a secure and standard approach for multi-contract deployments. This allows for efficient implementation updates while maintaining state… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 90.1% |
| **Top-3 Unlocked** | ⚠️ 97.4% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 8 address(es) other than the owner/deployer. One of them — a wallet, 0xf949…0298 — holds 90.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a contract — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.3% of supply. Of that, 0.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.2% in wallets, 83.3% in other contracts. 5,764 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Forest Protocol (FOREST), market cap $2M, rank #2563. 5,764 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $401K (DexScreener, all pools). 24h trading volume $147K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.4M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.246 on 2026-05-10; the price is now 92.3949% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $401K of DEX liquidity across 7 pools. Launch: 417 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x11cf...a7d0`](https://bscscan.com/address/0x11cf6bf6d87cb0eb9c294fd6cbfec91ee3a1a7d0) |
| **Network** | BNB Chain |
| **Price** | $0.03883 |
| **24h Volume** | $1.14M |
| **Liquidity** | $363.9K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6808 buys / 7061 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf0601427e3bfc416bc7838fb9e15c6f0f56f4aa0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/forest-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

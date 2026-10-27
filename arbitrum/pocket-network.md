---
token: Pocket Network
ticker: POKT
network: arbitrum
risk_score: 82
status: high
date: 2026-10-27
---

# Pocket Network (POKT) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pocket-network-arb)

---

## Audit Summary

The xPOKT contract is a cross-chain token implementation utilizing a Transparent Proxy pattern. The architecture is robust, featuring standard minting limits and a pause mechanism managed by a designated guardian. No critical or high-severity vulnerabilities were identified during the static analysis of the provided codebase.

> **Final Recommendation:** The protocol demonstrates a high level of security maturity. It is recommended to maintain the current multisig configuration for all administrative functions and ensure that the pause guardian role is held by a distinct, highly secure entity to prevent single points of failure.

Continue monitoring the bridge rate limits as liquidity requirements evolve. Ensure that any future upgrades undergo thorough testing in a staging environment before deployment to the mainnet.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract architecture follows established OpenZeppelin standards for upgradeable tokens. 7.1 Architecture is well-structured, utilizing modular mixins for pause and minting logic. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic controls are managed through rate limits and buffer caps, preventing excessive minting. 7.5 Governance is centralized under a multisig, which is appropriate for the current operational… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are handled via the Transparent Proxy pattern, requiring a multisig-controlled ProxyAdmin. This ensures that any logic changes are transparent and authorized. 7.8 Operations are… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 1-of-1 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — a 1-of-1 multisig — mint new supply; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x03a4…39ad — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $46K (DexScreener, all pools). 24h trading volume $6.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $67K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $3.11 on 2022-01-15; the price is now 99.6941% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 13.0% in wallets, 87.0% in other contracts. 44 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Pocket Network (POKT), market cap $23M, rank #765. 44 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 1-of-1 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $46K of DEX liquidity across 1 pools. Launch: 207 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x764a...a935`](https://arbiscan.io/address/0x764a726d9ced0433a8d7643335919deb03a9a935) |
| **Network** | Arbitrum |
| **Price** | $0.009112 |
| **24h Volume** | $67.1K |
| **Liquidity** | $46.1K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 387 buys / 277 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xb2d4f4c5853e448854246a94f8bb392e5d8a76d8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pocket-network-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*

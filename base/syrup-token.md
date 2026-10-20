---
token: Syrup Token
ticker: SYRUP
network: base
risk_score: 28
status: low
date: 2026-10-01
---

# Syrup Token (SYRUP) — Smart Contract Security Analysis | Base

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/syrup-token-base)

---

## Audit Summary

The SYRUP_OFT contract is an upgradeable LayerZero OFT (Omnichain Fungible Token) deployed on the Base network. It functions as an ERC-20 token with cross-chain capabilities. The contract is managed by a 2/4 multisig for both ownership and proxy administration. No specific vulnerabilities were identified during this analysis.

> **Final Recommendation:** Maintain strict security practices for the multisig controlling both contract ownership and proxy administration, including secure key management and robust operational procedures (7.8 Operations). Ensure all proposed upgrades undergo thorough security reviews and testing before deployment to prevent the introduction of new vulnerabilities. Continuously monitor the contract's behavior and external dependencies for any anomalies (7.6 External).

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The SYRUP_OFT contract implements the ERC-20 standard and LayerZero's Omnichain Fungible Token (OFT) functionality, enabling cross-chain transfers. Core ERC-20 functions like `transfer` and… |
| **Governance / Economics** | 5/10 | Medium | The contract's ownership is retained by a 2/4 multisig, which controls several critical administrative functions (7.3 Access Control). The owner can call `setMsgInspector`, `setEnforcedOptions`… |
| **Upgrades** | 3/10 | High | The SYRUP_OFT contract is deployed as a TransparentUpgradeableProxy, allowing its logic to be upgraded in the future (7.1 Architecture, 7.7 Upgrades). The proxy administration is controlled by a 2/4… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-4 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.9% |
| **Top-3 Unlocked** | 76.9% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a wallet, 0xcdbc…25d9 — holds 50.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 56% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 39.0% of supply. Of that, 2.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 32.1% in wallets, 4.5% in other contracts. 6,845 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Maple Finance (SYRUP), market cap $264M, rank #163. 6,845 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $93K (DexScreener, all pools). 24h trading volume $13.9M (CoinGecko, all markets, daily snapshot). 24h trading volume $93K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 2-of-4 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $93K of DEX liquidity across 5 pools. Launch: 684 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x688a...9a2f`](https://basescan.org/address/0x688aee022aa544f150678b8e5720b6b96a9e9a2f) |
| **Network** | Base |
| **Price** | $0.225 |
| **24h Volume** | $91.0K |
| **Liquidity** | $52.2K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 39.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 479 buys / 635 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x7432aab631b801a10bef7d70c1507a32755595fa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/syrup-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*

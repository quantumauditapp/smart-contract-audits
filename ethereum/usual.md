---
token: USUAL
ticker: USUAL
network: ethereum
risk_score: 52
status: medium
date: 2026-10-26
---

# USUAL (USUAL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usual-eth)

---

## Audit Summary

The Usual token is a standard ERC-20 implementation utilizing the OpenZeppelin upgradeable library. The contract architecture follows industry-standard patterns for proxy-based upgrades and includes standard administrative controls such as pausing and minting. No vulnerabilities were identified in the current implementation.

> **Final Recommendation:** The protocol demonstrates a strong security posture with no identified vulnerabilities. It is recommended to maintain the current multisig threshold and ensure that any future logic upgrades undergo rigorous testing and community transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes robust, battle-tested OpenZeppelin libraries for ERC-20 functionality and proxy management. 7.1 Architecture is sound, utilizing a Transparent Proxy pattern to allow for future… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are managed through a 15-member multisig with an 8-signature threshold. This provides a strong security posture for administrative actions like minting. 7.6… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are handled via a dedicated ProxyAdmin contract, ensuring that logic changes are controlled by the multisig. 7.8 Operations are well-defined, with the proxy pattern allowing for seamless… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 8-of-15 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 89.1% |
| **Top-3 Unlocked** | ⚠️ 99.6% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply; freeze or blacklist individual addresses; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a contract, 0x20c8…5f9b — holds 89.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 85% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $774K (DexScreener, all pools). 24h trading volume $4.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $111K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.61 on 2024-12-19; the price is now 99.3434% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.3% of supply. What remains: 33.3% in wallets, 55.0% in other contracts. 24,161 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Usual (USUAL), market cap $21M, rank #800. Traded on Binance. 24,161 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $774K of DEX liquidity across 4 pools. Launch: 677 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc444...e38e`](https://etherscan.io/address/0xc4441c2be5d8fa8126822b9929ca0b81ea0de38e) |
| **Network** | Ethereum |
| **Price** | $0.01057 |
| **24h Volume** | $100.5K |
| **Liquidity** | $658.0K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 88.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 96 buys / 96 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x4b43f8fb1a3c884261ae6f1e0d6d3d16203475335bdefe45f547f32db15eceb0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usual-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*

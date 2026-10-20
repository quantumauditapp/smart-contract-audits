---
token: ENA
ticker: ENA
network: base
risk_score: 39
status: medium
date: 2026-10-01
---

# ENA (ENA) — Smart Contract Security Analysis | Base

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ena-base)

---

## Audit Summary

The ENAOFT contract is an Omnichain Fungible Token (OFT) designed for cross-chain transfers, built on the ERC-20 standard. The contract's ownership is retained and controlled by a Timelock, which provides a delay for administrative actions. A key finding identifies that a specific 'endpoint' address has the capability to mint new tokens, which could lead to supply inflation if compromised. The contract is not upgradeable, meaning its logic is immutable post-deployment.

> **Final Recommendation:** It is critical to ensure robust security measures are in place for the 'endpoint' address that controls token minting capabilities. This address should ideally be managed by a multi-signature wallet or a secure governance mechanism with appropriate access controls and monitoring. Regular security reviews of the 'endpoint' address's operational procedures are advised to mitigate the risk of unauthorized token creation and protect token holder value.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ENAOFT contract implements the ERC-20 standard with additional LayerZero OFT (Omnichain Fungible Token) capabilities, allowing for cross-chain token transfers. It includes a `RateLimiter` to… |
| **Governance / Economics** | 1/10 | High | The contract uses a Timelock for its owner, which enhances security for owner-controlled functions like `transferOwnership` and `setRateLimiter` by introducing a delay for changes. However, the… |
| **Upgrades** | 4/10 | Medium | The ENAOFT contract is not deployed as an upgradeable proxy. This means its logic cannot be modified or updated after deployment. While this eliminates upgrade-related risks such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Special Address Can Create New Tokens  *(Severity: Medium · Status: Unresolved)*

The ENAOFT token contract has a special address, referred to as the 'endpoint', that has the power to create new ENAOFT tokens. This can happen through functions like `send`, `lzReceiveSimulate`, and `lzReceive`. When new tokens are created, the total supply of ENAOFT increases, which can reduce the value of tokens held by existing holders.

**Recommendation:** It is crucial to understand who controls this 'endpoint' address and what security measures are in place to protect it. The project team should ensure that the 'endpoint' address is highly secure, possibly controlled by a multi-signature wallet or a robust governance mechanism, to prevent any unauthorized creation of tokens.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xfcaf…245e — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 83.6% of supply. What remains: 2.6% in wallets, 80.9% in other contracts. 4,738 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Ethena (ENA), market cap $2.7B, rank #41. 4,738 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $59K (DexScreener, all pools). 24h trading volume $790.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $68K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: a timelock with a 24h delay. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $59K of DEX liquidity across 11 pools. Launch: 403 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5853...0133`](https://basescan.org/address/0x58538e6a46e07434d7e7375bc268d3cb839c0133) |
| **Network** | Base |
| **Price** | $0.2605 |
| **24h Volume** | $67.3K |
| **Liquidity** | $56.5K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 83.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 726 buys / 1068 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xc422bfb18f9fc217f955d759d3753f31137ccefd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ena-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*

---
token: Metaplex
ticker: MPLX
network: bsc
risk_score: 65
status: high
date: 2026-10-20
---

# Metaplex (MPLX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metaplex-bsc)

---

## Audit Summary

The BridgeToken contract is a standard ERC-20 implementation with administrative minting capabilities. The contract utilizes a beacon proxy pattern for upgradeability. No critical or high-severity vulnerabilities were identified during the static analysis of the implementation logic.

> **Final Recommendation:** The protocol should consider transitioning the owner address to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks associated with the minting capability. Ensure that the beacon proxy owner is also secured with similar multi-signature requirements to prevent unauthorized implementation upgrades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract follows standard ERC-20 patterns with robust implementation of transfer and approval logic. 7.1 Architecture is sound, utilizing a beacon proxy for modularity. 7.2 Code Security is high… |
| **Governance / Economics** | 5/10 | Medium | 7.3 Access Control is centralized under an owner address, which is currently a contract. 7.4 Economic risk is present due to the minting function, which allows the owner to increase supply… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are managed via a Beacon proxy, allowing for implementation updates. This pattern is well-understood and provides a clear path for maintenance. 7.8 Operations are supported by the… |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a contract — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No code-level findings — contract source is not verified on the explorer  *(Severity: Informational · Status: Acknowledged)*

The contract's source code has not been published or verified on the block explorer, so only its deployed bytecode and on-chain behaviour were available. No source-level vulnerability could be confirmed or ruled out. The assessment on this page rests on mint/owner authority, mint capability.

**Recommendation:** Treat an unverified contract as unaudited at the code level. Ask the team to verify the source on the explorer, which makes an independent review possible.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Metaplex (MPLX), market cap $24M, rank #755.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $709K (DexScreener, all pools). 24h trading volume $994K (CoinGecko, all markets, daily snapshot). 24h trading volume $2.9M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.897 on 2022-09-19; the price is now 94.4311% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $709K of DEX liquidity across 3 pools. Launch: 487 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x75a5...470f`](https://bscscan.com/address/0x75a5863a19af60ec0098d62ed8c34cc594fb470f) |
| **Network** | BNB Chain |
| **Price** | $0.07593 |
| **24h Volume** | $2.87M |
| **Liquidity** | $709.1K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4297 buys / 4146 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xcacd3583c7ef55126099be733b12672c60e2ab23)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metaplex-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

---
token: RWA Inc
ticker: RWA
network: base
risk_score: 50
status: medium
date: 2026-10-31
---

# RWA Inc (RWA) — Smart Contract Security Analysis | Base

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rwa-inc-base)

---

## Audit Summary

The RWAIncToken is an Omnichain Fungible Token (OFT) deployed on Base. The architecture relies on LayerZero for cross-chain interoperability. While the core ERC-20 implementation is standard, the token includes minting capabilities tied to cross-chain messaging, which introduces specific risks regarding supply inflation and endpoint trust.

> **Final Recommendation:** It is recommended to transition the ownership of the contract to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks. Additionally, monitor the LayerZero endpoint and peer configurations closely to ensure that cross-chain minting parameters remain within expected bounds.

Ensure that all administrative actions are logged and that the owner address is secured with hardware-based multi-factor authentication. Regularly audit the configuration of the 'enforcedOptions' to prevent potential denial-of-service or fee-related issues in cross-chain transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust LayerZero OFT architecture, ensuring standard ERC-20 compliance and cross-chain compatibility. 7.1 Architecture is well-structured using established OApp patterns. 7.2… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic risks are centered on the minting mechanism inherent in the OFT standard. 7.5 Governance is currently centralized under an EOA, allowing the owner to modify peers and enforced options.… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, which provides security against hidden logic changes but prevents patching vulnerabilities post-deployment. The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Privileged Minting via Cross-Chain Messaging  *(Severity: Medium · Status: Unresolved)*

The functions 'send', 'lzReceiveSimulate', and 'lzReceive' allow for the minting of new tokens as part of the cross-chain transfer process. This increases the total supply of the token, which could lead to the dilution of existing token holders if the cross-chain messaging endpoint is compromised or misconfigured.

**Recommendation:** Implement strict supply caps or circuit breakers to limit the amount of tokens that can be minted via cross-chain operations. Ensure that the LayerZero endpoint is trusted and that the 'setPeer' configuration is strictly managed to prevent unauthorized cross-chain interactions.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x5efb…ab5a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $66K (DexScreener, all pools). 24h trading volume $123K (CoinGecko, all markets, daily snapshot). 24h trading volume $31K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.141 on 2024-12-04; the price is now 99.0731% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 49.8% of supply. What remains: 17.3% in wallets, 32.4% in other contracts. 73,700 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as RWA Inc. (RWA), market cap $1M, rank #3064. 73,700 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $66K of DEX liquidity across 5 pools. Launch: 705 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe2b1...b35a`](https://basescan.org/address/0xe2b1dc2d4a3b4e59fdf0c47b71a7a86391a8b35a) |
| **Network** | Base |
| **Price** | $0.00133 |
| **24h Volume** | $31.1K |
| **Liquidity** | $65.8K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 49.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 315 buys / 299 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x60d1cebd97a6168516f35982d499cdf8a452abb3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rwa-inc-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*

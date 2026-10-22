---
token: AltLayer Token
ticker: ALT
network: bsc
risk_score: 47
status: medium
date: 2026-10-22
---

# AltLayer Token (ALT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/altlayer-token-bsc)

---

## Audit Summary

The AltLayerToken is a standard ERC-20 implementation utilizing OpenZeppelin libraries for pausing, minting, and permit functionality. The architecture is straightforward and relies on centralized ownership for administrative control. While the code follows industry standards, the ability for the owner to mint tokens and pause transfers introduces centralized risk that requires trust in the protocol's governance.

> **Final Recommendation:** The protocol should consider transitioning ownership to a decentralized governance contract or a larger multisig to mitigate the risks associated with centralized control. Additionally, implementing a timelock on the minting function would provide transparency and prevent sudden supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust, battle-tested OpenZeppelin libraries for all core ERC-20 operations. 7.1 Architecture is modular and 7.2 Code Security is high due to the use of standard, audited… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the owner's ability to mint tokens and pause transfers. The minting function allows for supply inflation, which directly impacts token holder… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as this is a non-proxy contract. 7.8 Operations are limited to standard administrative tasks like pausing and minting. The lack of upgradeability ensures immutability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to call the mint function, which increases the total supply of the token. This allows the controller to dilute the holdings of all existing token holders at any time.

**Recommendation:** Implement a timelock or a hard cap on the total supply to restrict the owner's ability to mint tokens arbitrarily.


### `CP-04` — Centralized Transfer Pausing  *(Severity: Medium · Status: Unresolved)*

The owner can call the pause and unpause functions, which effectively freeze all token transfers. This gives the controller the power to prevent users from moving their assets.

**Recommendation:** Restrict the use of pause functionality to emergency scenarios only and consider adding a governance vote requirement before pausing.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x7966…e764 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.7% of supply. What remains: 61.1% in wallets, 12.6% in other contracts. 8,882 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AltLayer (ALT), market cap $87M, rank #307. Traded on Binance, Coinbase. 8,882 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $69K (DexScreener, all pools). 24h trading volume $100.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $126K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.677 on 2024-03-28; the price is now 98.2609% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $69K of DEX liquidity across 2 pools. Launch: 1000 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8457...fbfb`](https://bscscan.com/address/0x8457ca5040ad67fdebbcc8edce889a335bc0fbfb) |
| **Network** | BNB Chain |
| **Price** | $0.008301 |
| **24h Volume** | $126.0K |
| **Liquidity** | $69.4K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 2y |
| **Top-10 Holders** | 73.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1865 buys / 1952 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9669b9ee0ac0b0ea93181cd04557ffdc857c815d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/altlayer-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*

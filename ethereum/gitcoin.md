---
token: Gitcoin
ticker: GTC
network: ethereum
risk_score: 38
status: medium
date: 2026-10-02
---

# Gitcoin (GTC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gitcoin-eth)

---

## Audit Summary

The GTC contract is an ERC-20 compatible token. A key finding highlights that a privileged 'minter' address possesses the capability to mint new tokens, which can lead to the dilution of existing token holders. This centralized control over the token supply represents a significant economic risk.

> **Final Recommendation:** Token holders should be fully aware of the centralized control points within the GTC contract, particularly the 'minter' role's ability to inflate the token supply. For enhanced security and decentralization, the project team should consider implementing multi-signature wallet control or a time-locked governance mechanism for critical administrative functions like `setMinter` and `mint`. Additionally, robust monitoring for `mint` events should be in place to ensure transparency and accountability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The GTC contract implements standard ERC-20 functionalities for token transfers and approvals. A central technical control is the 'minter' address, which can call `mint(address,uint256)` to increase… |
| **Governance / Economics** | 1/10 | High | The economic model of the GTC token allows for supply inflation through the `mint` function, which is controlled by a single 'minter' address (7.4 Economic). This introduces a centralization risk… |
| **Upgrades** | 3/10 | High | The GTC contract is not designed with an upgrade proxy pattern, meaning its logic cannot be changed after deployment (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Control Over Token Supply (Minting Capability)  *(Severity: Medium · Status: Unresolved)*

The `mint(address,uint256)` function allows a specific address, designated as the `minter`, to create new GTC tokens. This increases the total supply of GTC, which can dilute the value of existing tokens held by other users. The `minter` can also change the `minter` address itself via `setMinter(address)`, concentrating significant power in a single entity.

**Recommendation:** Token holders should be aware that the `minter` address has the power to increase the token supply. To mitigate this risk, the project team should consider implementing a multi-signature wallet or a time-locked governance mechanism to control the `minter` address and the `mint` function, reducing reliance on a single entity.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xd6c5…2e8c — holds 98.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 76% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $228K (DexScreener, all pools). 24h trading volume $59.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $287K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $22.37 on 2021-11-26; the price is now 99.3137% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 68.0% of supply. What remains: 50.2% in wallets, 17.8% in other contracts. The owner address holds 12.5% — it is a governance timelock (48h delay), so any sale of that share needs a public, delayed transaction. 89,221 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Gitcoin (GTC), market cap $13M, rank #1113. Traded on Binance, Coinbase. 89,221 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: minter — a timelock with a 48h delay. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $228K of DEX liquidity across 13 pools. Launch: 1955 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xde30...163f`](https://etherscan.io/address/0xde30da39c46104798bb5aa3fe8b9e0e1f348163f) |
| **Network** | Ethereum |
| **Price** | $0.1306 |
| **24h Volume** | $241.8K |
| **Liquidity** | $172.9K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 5y |
| **Top-10 Holders** | 68.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 814 buys / 689 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xd017617f6f0fd22796e137a8240cc38f52a147b2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gitcoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*

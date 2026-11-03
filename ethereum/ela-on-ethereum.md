---
token: ELA on Ethereum
ticker: ELA
network: ethereum
risk_score: 75
status: high
date: 2026-11-03
---

# ELA on Ethereum (ELA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ela-on-ethereum-eth)

---

## Audit Summary

The PermittableToken contract is a centralized ERC-20 implementation with extensive administrative privileges. While it follows standard token patterns, the owner possesses significant power to mint tokens and manipulate user balances, creating a high level of trust dependency. The contract lacks modern security features like reentrancy guards, though the current logic is relatively straightforward.

> **Final Recommendation:** Token holders should be aware that the contract owner has full control over the total supply and individual user balances. It is recommended that the owner address be transitioned to a multi-signature wallet or a time-locked governance contract to mitigate the risk of single-point-of-failure compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with additional bridge and permit functionality. 7.1 Architecture: Centralized control via owner. 7.2 Code Security: Uses SafeMath for arithmetic… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The owner can mint tokens at will, directly impacting token value. 7.5 Governance: No decentralized governance mechanism exists; all power is concentrated in the owner address. 7.8… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades: The contract is not a proxy and cannot be upgraded. This provides immutability but prevents patching vulnerabilities post-deployment. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · ⚪ 3 Informational_

### `CP-02` — Owner can manipulate user balances  *(Severity: High · Status: Unresolved)*

Functions like transferAndCall, push, pull, and move allow the owner to directly modify balances or move funds from any user address, posing a critical risk to asset security.

**Recommendation:** Remove administrative functions that allow direct manipulation of user balances to ensure user sovereignty over their assets.


### `CP-01` — Owner can mint new tokens  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows the owner to create new tokens, which increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Restrict minting to a capped amount or remove the function entirely if the total supply should be fixed.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0xf06b…c0eb — holds 99.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $96K (DexScreener, all pools). 24h trading volume $4.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $582K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $89.14 on 2018-02-23; the price is now 99.3901% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.7% of supply. What remains: 65.0% in wallets, 14.7% in other contracts. 2,763 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Elastos (ELA), market cap $13M, rank #1090. Traded on Coinbase. 2,763 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $96K of DEX liquidity across 4 pools. Launch: 1953 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe6fd...1867`](https://etherscan.io/address/0xe6fd75ff38adca4b97fbcd938c86b98772431867) |
| **Network** | Ethereum |
| **Price** | $0.6846 |
| **24h Volume** | $580.5K |
| **Liquidity** | $95.3K |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 5y |
| **Top-10 Holders** | 79.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 594 buys / 504 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x412940fdac1214fc3df430769f54e69210a18e49)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ela-on-ethereum-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

---
token: GreenMetaverseToken
ticker: GMT
network: polygon
risk_score: 56
status: medium
date: 2026-10-29
---

# GreenMetaverseToken (GMT) — Smart Contract Security Analysis | Polygon

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/greenmetaversetoken-poly)

---

## Audit Summary

The GreenMetaverseToken is a standard ERC-20 implementation with burnable capabilities. The contract is managed by a 3-of-4 multisig wallet, providing a robust layer of operational security. The primary risk identified is the centralized minting authority, which allows the owner to increase the total supply at will.

> **Final Recommendation:** To mitigate the risk of supply dilution, it is recommended to implement a timelock controller for the minting function. This would ensure that any increase in total supply is subject to a mandatory delay, providing transparency and an opportunity for the community to react to changes in tokenomics.

Furthermore, the multisig signers should maintain strict operational security protocols for their private keys. Given the centralization of the minting power, the project should consider transitioning to a decentralized governance model if the token supply is intended to be expanded significantly in the future.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and Ownable functionality, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is correctly… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the minting authority held by the multisig. While the 3-of-4 multisig structure provides 7.8 Operations security, the ability to mint tokens… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, eliminating 7.7 Upgrades risks associated with proxy patterns. The logic is immutable, ensuring that the current token behavior cannot be altered by the owner. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 70.5% |
| **Top-3 Unlocked** | ⚠️ 94.1% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner of the contract has the ability to call the mint function, which creates new tokens and increases the total supply. This action dilutes the value of existing tokens held by users.

**Recommendation:** Implement a timelock on the mint function or renounce the minting authority if the total supply is intended to be fixed. If minting is required, ensure all minting events are publicly announced and documented.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 7 address(es) other than the owner/deployer. One of them — a wallet, 0x41e4…ac84 — holds 70.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $3.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $36K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $4.11 on 2022-04-27; the price is now 99.8309% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.2% of supply. What remains: 86.9% in wallets, 6.4% in other contracts. 46,432 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GMT (GMT), market cap $22M, rank #794. Traded on Binance. 46,432 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Gaming Governance Token. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-4 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 7 pools. Launch: 1147 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x714d...d4c2`](https://polygonscan.com/address/0x714db550b574b3e927af3d93e26127d15721d4c2) |
| **Network** | Polygon |
| **Price** | $0.007004 |
| **24h Volume** | $34.0K |
| **Liquidity** | $1.11M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 93.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 121 buys / 109 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0xb064e9b00d713496d54617c3ef6e659072b8339f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/greenmetaversetoken-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

---
token: TCOM
ticker: TCOM
network: bsc
risk_score: 61
status: medium
date: 2026-10-23
---

# TCOM (TCOM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tcom-bsc)

---

## Audit Summary

MyToken is a standard ERC-20 implementation with integrated governance (ERC20Votes) and custom transfer restrictions. The contract utilizes a centralized owner to manage a whitelist and a time-locked transfer activation mechanism. The code follows standard OpenZeppelin patterns, ensuring robust base functionality, though the centralized control over transferability introduces a dependency on the owner's integrity.

> **Final Recommendation:** The protocol should consider transitioning ownership to a decentralized DAO or a time-locked contract to mitigate the risks associated with centralized control over transferability. Additionally, ensure that the multisig signers are geographically and organizationally distributed to prevent single points of failure.

Regular monitoring of the 'transferAllowedTimestamp' and whitelist changes is recommended for token holders to ensure transparency. No immediate code changes are required as the current implementation is secure and standard.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages well-audited OpenZeppelin libraries for core ERC-20 and governance features. 7.1 Architecture is modular, 7.2 Code Security is high due to standard library usage, and 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized under the owner. While the owner is a multisig (3/5), the ability to restrict transfers via setTransferAllowedTimestamp and manage a whitelist… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, relying on standard ownership management. The lack of upgradeability ensures immutability of the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xe53a…2860 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Centralized Control Over Transferability  *(Severity: Low · Status: Unresolved)*

The owner can use the setTransferAllowedTimestamp function to delay or enable token transfers, and the addToWhitelist/removeFromWhitelist functions to control which addresses can move tokens. This grants the owner significant power to halt or restrict market liquidity at will.

**Recommendation:** Document the intended use of these restrictions clearly for users. Consider implementing a time-lock on these administrative functions to provide community notice before transfer rules are modified.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.8% of supply. Of that, 3.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 94.7% in wallets, 0.8% in other contracts. 22,464 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as TCOM Global (TCOM), rank #3244. 22,464 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $328K (DexScreener, all pools). 24h trading volume $558K (CoinGecko, all markets, daily snapshot). 24h trading volume $224K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.107 on 2025-12-25; the price is now 92.5843% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $328K of DEX liquidity across 1 pools. Launch: 435 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc23d...5d84`](https://bscscan.com/address/0xc23db46993f643f1fa0494cd30f9f43505885d84) |
| **Network** | BNB Chain |
| **Price** | $0.008086 |
| **24h Volume** | $224.3K |
| **Liquidity** | $328.1K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2349 buys / 2295 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7f0b9a92fe7abbc64d38cbd02a3c39191657b8bb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tcom-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*

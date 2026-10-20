---
token: PolkastarterToken
ticker: POLS
network: ethereum
risk_score: 44
status: medium
date: 2026-10-11
---

# PolkastarterToken (POLS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/polkastartertoken-eth)

---

## Audit Summary

The PolkastarterToken is an ERC-20 compliant token with standard functionalities including transfer, approval, and balance tracking. It incorporates pausable functionality, allowing the owner to halt all token transfers. The contract is owned by a multisig wallet, which controls the ability to pause and unpause transfers. One medium-severity finding related to centralized control over transfers was identified.

> **Final Recommendation:** Ensure the multisig wallet controlling the contract's ownership is secured with robust operational procedures and sufficient signer diversity to prevent single points of failure. Communicate clearly with token holders about the conditions under which transfers might be paused. Regularly review the multisig's security posture and consider implementing a timelock for critical administrative actions to provide a delay for review and reaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The PolkastarterToken is an ERC-20 compliant token, inheriting from `StandardToken` and `BasicToken`, ensuring fundamental token functionalities (7.1 Architecture). It includes `PausableToken`… |
| **Governance / Economics** | 3/10 | High | The contract utilizes the `Ownable` pattern, granting a single owner address control over critical functions such as `pause()`, `unpause()`, and `transferOwnership()` (7.3 Access Control). The owner… |
| **Upgrades** | 7/10 | Low | This contract is not designed with upgradeability in mind, as it does not implement any proxy pattern (7.7 Upgrades). Therefore, its logic cannot be modified or extended after deployment. Any future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 3.8% |
| **Lock Expiry** | Expired 821d ago |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-04` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The `PolkastarterToken` contract includes a pausing mechanism, which allows the contract owner to stop all token transfers. Specifically, the `pause()` function can be called by the owner to halt all `transfer()` and `transferFrom()` operations, and the `unpause()` function can resume them. This means a single entity (the owner) has the power to unilaterally freeze all token movement.

**Recommendation:** Token holders should be aware that the owner, a multisig wallet, can halt all token transfers at any time. While this feature can be useful in emergencies (e.g., to mitigate a major exploit), it also introduces a significant centralization risk. Ensure you trust the multisig signers and understand their operational policies regarding the use of this function. Consider advocating for a community-driven governance mechanism or a timelock to manage such critical functions in the future.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 27.3% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 92% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $150K (DexScreener, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $139K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $7.51 on 2021-02-16; the price is now 99.1594% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 68.1% of supply. What remains: 50.0% in wallets, 18.1% in other contracts. 31,612 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Polkastarter (POLS), market cap $6M, rank #1549. Traded on Binance, Coinbase. 31,612 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 1-of-2 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $150K of DEX liquidity across 6 pools. Launch: 2202 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x83e6...d5aa`](https://etherscan.io/address/0x83e6f1e41cdd28eaceb20cb649155049fac3d5aa) |
| **Network** | Ethereum |
| **Price** | $0.06314 |
| **24h Volume** | $137.4K |
| **Liquidity** | $138.0K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 6y |
| **Top-10 Holders** | 68.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 312 buys / 343 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xffa98a091331df4600f87c9164cd27e8a5cd2405)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/polkastartertoken-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
